import logging

import os

import sys
import json
from copy import deepcopy
from typing import Any
from urllib.parse import urlencode

from celery.schedules import crontab

from flask_caching.backends.filesystemcache import FileSystemCache
from flask import redirect, session
from flask_appbuilder import expose
from flask_appbuilder.security.manager import AUTH_DB, AUTH_OAUTH
from flask_appbuilder.security.views import AuthOAuthView
from flask_login import logout_user
from superset.config import (
    TALISMAN_CONFIG as DEFAULT_TALISMAN_CONFIG,
    TALISMAN_DEV_CONFIG as DEFAULT_TALISMAN_DEV_CONFIG,
)
from superset.security import SupersetSecurityManager
 
logger = logging.getLogger()
 
# -----------------------------

# Database settings (unchanged)

# -----------------------------

DATABASE_DIALECT = os.getenv("DATABASE_DIALECT")

DATABASE_USER = os.getenv("DATABASE_USER")

DATABASE_PASSWORD = os.getenv("DATABASE_PASSWORD")

DATABASE_HOST = os.getenv("DATABASE_HOST")

DATABASE_PORT = os.getenv("DATABASE_PORT")

DATABASE_DB = os.getenv("DATABASE_DB")
 
EXAMPLES_USER = os.getenv("EXAMPLES_USER")

EXAMPLES_PASSWORD = os.getenv("EXAMPLES_PASSWORD")

EXAMPLES_HOST = os.getenv("EXAMPLES_HOST")

EXAMPLES_PORT = os.getenv("EXAMPLES_PORT")

EXAMPLES_DB = os.getenv("EXAMPLES_DB")
 
SQLALCHEMY_DATABASE_URI = (

    f"{DATABASE_DIALECT}://"

    f"{DATABASE_USER}:{DATABASE_PASSWORD}@"

    f"{DATABASE_HOST}:{DATABASE_PORT}/{DATABASE_DB}"

)
 
SQLALCHEMY_EXAMPLES_URI = os.getenv(

    "SUPERSET__SQLALCHEMY_EXAMPLES_URI",

    (

        f"{DATABASE_DIALECT}://"

        f"{EXAMPLES_USER}:{EXAMPLES_PASSWORD}@"

        f"{EXAMPLES_HOST}:{EXAMPLES_PORT}/{EXAMPLES_DB}"

    ),

)
 
# -----------------------------

# Caching / results (unchanged)

# -----------------------------

REDIS_HOST = os.getenv("REDIS_HOST", "redis")

REDIS_PORT = os.getenv("REDIS_PORT", "6379")

REDIS_CELERY_DB = os.getenv("REDIS_CELERY_DB", "0")

REDIS_RESULTS_DB = os.getenv("REDIS_RESULTS_DB", "1")
 
RESULTS_BACKEND = FileSystemCache("/app/superset_home/sqllab")
 
CACHE_CONFIG = {

    "CACHE_TYPE": "RedisCache",

    "CACHE_DEFAULT_TIMEOUT": 300,

    "CACHE_KEY_PREFIX": "superset_",

    "CACHE_REDIS_HOST": REDIS_HOST,

    "CACHE_REDIS_PORT": REDIS_PORT,

    "CACHE_REDIS_DB": REDIS_RESULTS_DB,

}

DATA_CACHE_CONFIG = CACHE_CONFIG

THUMBNAIL_CACHE_CONFIG = CACHE_CONFIG
 
# -----------------------------

# Celery (unchanged)

# -----------------------------

class CeleryConfig:

    broker_url = f"redis://{REDIS_HOST}:{REDIS_PORT}/{REDIS_CELERY_DB}"

    imports = (

        "superset.sql_lab",

        "superset.tasks.scheduler",

        "superset.tasks.thumbnails",

        "superset.tasks.cache",

    )

    result_backend = f"redis://{REDIS_HOST}:{REDIS_PORT}/{REDIS_RESULTS_DB}"

    worker_prefetch_multiplier = 1

    task_acks_late = False

    beat_schedule = {

        "reports.scheduler": {

            "task": "reports.scheduler",

            "schedule": crontab(minute="*", hour="*"),

        },

        "reports.prune_log": {

            "task": "reports.prune_log",

            "schedule": crontab(minute=10, hour=0),

        },

    }
 
 
CELERY_CONFIG = CeleryConfig
 
# -----------------------------

# Feature flags (additions)

# -----------------------------

FEATURE_FLAGS = {

    "ALERT_REPORTS": True,

    # Helpful for your dashboard migrations:

    "VERSIONED_EXPORT": True,

    "VERSIONED_IMPORT_EXPORT": True,

    # Enable embedded dashboards

    "EMBEDDED_SUPERSET": True,

    # Enable automatic dashboard/chart thumbnails

    "THUMBNAILS": True,

    "THUMBNAILS_SQLA_LISTENERS": True,

}
 
ALERT_REPORTS_NOTIFICATION_DRY_RUN = True

# -----------------------------

# Thumbnail Configuration

# -----------------------------

# Use Playwright for thumbnail generation (RECOMMENDED)
# Requires INCLUDE_CHROMIUM=true in docker-compose build args

FEATURE_FLAGS["PLAYWRIGHT_REPORTS_AND_THUMBNAILS"] = True

# Base URL that Playwright uses to access Superset (MUST be internal docker network)
# This URL is used by the Celery worker to take screenshots
WEBDRIVER_BASEURL = "http://superset_app:8088/"
WEBDRIVER_BASEURL_USER_FRIENDLY = "http://superset_app:8088/"

# Thumbnail generation executors - who can trigger thumbnail generation
from superset.tasks.types import ExecutorType
THUMBNAIL_EXECUTORS = [ExecutorType.CURRENT_USER]

# Thumbnail cache timeout (in seconds) - 7 days
THUMBNAIL_CACHE_CONFIG = {
    "CACHE_TYPE": "RedisCache",
    "CACHE_DEFAULT_TIMEOUT": 60 * 60 * 24 * 7,
    "CACHE_KEY_PREFIX": "thumbnail_",
    "CACHE_REDIS_HOST": REDIS_HOST,
    "CACHE_REDIS_PORT": REDIS_PORT,
    "CACHE_REDIS_DB": REDIS_RESULTS_DB,
}

# Screenshot timing configuration
SCREENSHOT_LOCATE_WAIT = 30   # Wait time for element to appear (seconds)
SCREENSHOT_LOAD_WAIT = 120    # Wait time for page to load (seconds)
 
# -----------------------------
# HTTPS / reverse-proxy awareness
# -----------------------------
# These settings are driven by environment variables so local, UAT, and prod can
# use the same code with different runtime values.

ENABLE_PROXY_FIX = os.getenv("ENABLE_PROXY_FIX", "true").lower() == "true"
PROXY_FIX_CONFIG = {"x_for": 1, "x_proto": 1, "x_host": 1, "x_port": 1, "x_prefix": 1}

PREFERRED_URL_SCHEME = os.getenv("PREFERRED_URL_SCHEME", "https")
SESSION_COOKIE_HTTPONLY = True
SESSION_COOKIE_SAMESITE = os.getenv("SESSION_COOKIE_SAMESITE", "Lax")

session_cookie_secure_env = os.getenv("SESSION_COOKIE_SECURE")
if session_cookie_secure_env is None:
    SESSION_COOKIE_SECURE = PREFERRED_URL_SCHEME == "https"
else:
    SESSION_COOKIE_SECURE = session_cookie_secure_env.lower() == "true"

# Public URL used by alerts/reports and OAuth redirect URI generation.
DNS_NAME = os.getenv("SUPERSET_DNS_NAME", "").strip()
APP_ROOT = os.environ.get("SUPERSET_APP_ROOT", "/")

if not APP_ROOT.startswith("/"):
    APP_ROOT = f"/{APP_ROOT}"
if not APP_ROOT.endswith("/"):
    APP_ROOT = f"{APP_ROOT}/"

configured_webserver_baseurl = os.getenv("WEBSERVER_BASEURL", "").strip()
if configured_webserver_baseurl:
    WEBSERVER_BASEURL = configured_webserver_baseurl.rstrip("/")
elif DNS_NAME:
    WEBSERVER_BASEURL = f"{PREFERRED_URL_SCHEME}://{DNS_NAME}{APP_ROOT}".rstrip("/")
else:
    WEBSERVER_BASEURL = f"http://superset_app{APP_ROOT}".rstrip("/")

WEBDRIVER_BASEURL_USER_FRIENDLY = f"{WEBSERVER_BASEURL}/"

CXLOOP_URL = os.getenv("CXLOOP_URL", "").strip().rstrip("/")


def _split_origin_env(name: str, default: str = "") -> list[str]:
    return [
        origin.strip().rstrip("/")
        for origin in os.getenv(name, default).split(",")
        if origin.strip()
    ]


# Allow CTAS/CSV etc. (unchanged)

SQLLAB_CTAS_NO_LIMIT = True

# -----------------------------
# Optional SSO (SAML-via-IdP) settings
# -----------------------------
#
# This block is opt-in and does not change existing login behavior unless
# ENABLE_SAML_SSO is true.
#
# Superset/FAB routes SSO providers via /login/<provider>. The frontend SSO
# button is wired to /login/saml, so the provider name must be "saml".


def _get_json_env(name: str, default: Any) -> Any:
    raw = os.getenv(name)
    if not raw:
        return default
    try:
        return json.loads(raw)
    except json.JSONDecodeError:
        logger.warning("Invalid JSON in %s, using default value", name)
        return default


def _split_csv_env(name: str) -> set[str]:
    return {
        value.strip().lower()
        for value in os.getenv(name, "").split(",")
        if value.strip()
    }


def _get_group_role_map() -> dict[str, str]:
    raw = os.getenv("SUPERSET_GROUP_ROLE_MAP_JSON", "{}")
    parsed = _get_json_env("SUPERSET_GROUP_ROLE_MAP_JSON", {})
    if not isinstance(parsed, dict):
        logger.warning(
            "SUPERSET_GROUP_ROLE_MAP_JSON is not a JSON object: %s",
            raw,
        )
        return {}
    mapping: dict[str, str] = {}
    for group_id, role_name in parsed.items():
        if isinstance(group_id, str) and isinstance(role_name, str):
            mapping[group_id.lower()] = role_name
    return mapping


def _get_azure_post_logout_redirect_url() -> str:
    configured = os.getenv("AZURE_POST_LOGOUT_REDIRECT_URL", "").strip()
    if configured:
        return configured
    return f"{WEBSERVER_BASEURL}/login/"


def _get_azure_logout_url(tenant_id: str) -> str:
    return os.getenv(
        "AZURE_LOGOUT_URL",
        (
            f"https://login.microsoftonline.com/{tenant_id}"
            "/oauth2/logout"
        ),
    ).strip()


class AzureAuthOAuthView(AuthOAuthView):
    @expose("/logout/")
    def logout(self) -> Any:
        logout_user()
        session.clear()

        provider_logout_enabled = (
            os.getenv("AZURE_PROVIDER_LOGOUT_ENABLED", "true").lower() == "true"
        )
        tenant_id = os.getenv("AZURE_TENANT_ID", "").strip()
        if provider_logout_enabled and tenant_id:
            post_logout_redirect_uri = _get_azure_post_logout_redirect_url()
            logout_url = _get_azure_logout_url(tenant_id)
            query = urlencode(
                {"post_logout_redirect_uri": post_logout_redirect_uri},
                doseq=True,
            )
            separator = "&" if "?" in logout_url else "?"
            return redirect(f"{logout_url}{separator}{query}")

        return redirect(self.appbuilder.get_url_for_login)

    # Endpoint for Azure front-channel logout notification
    @expose("/oauth-logout/azure/")
    def oauth_logout_azure(self) -> Any:
        logout_user()
        session.clear()
        return redirect(self.appbuilder.get_url_for_login)


class CustomSsoSecurityManager(SupersetSecurityManager):
    @staticmethod
    def _to_group_list(raw_groups: Any) -> list[str]:
        if isinstance(raw_groups, list):
            return [str(item).strip() for item in raw_groups if str(item).strip()]
        if isinstance(raw_groups, str) and raw_groups.strip():
            return [raw_groups.strip()]
        return []

    @staticmethod
    def _normalize_userinfo(userinfo: dict[str, Any], provider: str) -> dict[str, Any]:
        email = (
            userinfo.get("email")
            or userinfo.get("mail")
            or userinfo.get("upn")
            or userinfo.get("preferred_username")
            or userinfo.get("userPrincipalName")
            or ""
        )
        principal = (
            userinfo.get("username")
            or userinfo.get("user_name")
            or userinfo.get("preferred_username")
            or userinfo.get("userPrincipalName")
            or email
        )
        principal = str(principal).strip()
        username = principal.split("@")[0] if "@" in principal else principal

        full_name = str(
            userinfo.get("name")
            or userinfo.get("displayName")
            or "",
        ).strip()
        first_name = str(
            userinfo.get("first_name")
            or userinfo.get("givenName")
            or (full_name.split(" ")[0] if full_name else ""),
        ).strip()
        last_name = str(
            userinfo.get("last_name")
            or userinfo.get("surname")
            or (" ".join(full_name.split(" ")[1:]) if " " in full_name else ""),
        ).strip()

        groups = CustomSsoSecurityManager._to_group_list(
            userinfo.get("groups") or userinfo.get("roles") or [],
        )

        return {
            "provider": provider,
            "name": full_name,
            "email": str(email).strip(),
            "username": username,
            "first_name": first_name,
            "last_name": last_name,
            "groups": groups,
        }

    def oauth_user_info(
        self,
        provider: str,
        response: dict[str, Any] | None = None,
    ) -> dict[str, Any]:
        try:
            if provider == "azure":
                remote = self.appbuilder.sm.oauth_remotes.get("azure")
                if remote is None:
                    logger.error("Azure OAuth remote app is not configured.")
                    return {}

                me_response = remote.get("https://graph.microsoft.com/v1.0/me")
                if not getattr(me_response, "ok", False):
                    logger.error("Failed to fetch Entra profile from Graph API.")
                    return {}

                me = me_response.json() or {}
                logger.debug("Entra ID user info response: %s", me)
                return self._normalize_userinfo(me, provider)

            base_info = super().oauth_user_info(provider, response) or {}
            if not isinstance(base_info, dict):
                logger.warning(
                    "Unexpected oauth_user_info payload type for provider=%s",
                    provider,
                )
                return {}
            return self._normalize_userinfo(base_info, provider)
        except Exception as ex:  # noqa: BLE001
            logger.exception(
                "Failed to resolve OAuth user info for provider=%s: %s",
                provider,
                ex,
            )
            return {}

    def auth_user_oauth(self, userinfo: dict[str, Any]) -> Any:
        if not isinstance(userinfo, dict):
            logger.error("Invalid oauth userinfo payload type.")
            return None

        try:
            user = super().auth_user_oauth(userinfo)
        except Exception as ex:  # noqa: BLE001
            logger.exception("Error during oauth user authentication: %s", ex)
            return None

        if user is None:
            return None

        email = str(userinfo.get("email", "")).strip().lower()
        default_role_name = os.getenv(
            "AUTH_USER_REGISTRATION_ROLE",
            "Gamma",
        )
        role_name = os.getenv("SSO_DEFAULT_ROLE", default_role_name)

        admin_users = _split_csv_env("SUPERSET_ADMIN_EMAILS")
        alpha_users = _split_csv_env("SUPERSET_ALPHA_EMAILS")
        if email in admin_users:
            role_name = "Admin"
        elif email in alpha_users:
            role_name = "Alpha"
        else:
            groups = userinfo.get("groups", [])
            group_ids = {
                str(group_id).strip().lower()
                for group_id in groups
                if str(group_id).strip()
            }
            for group_id, mapped_role in _get_group_role_map().items():
                if group_id in group_ids:
                    role_name = mapped_role
                    break

        role = self.find_role(role_name) or self.find_role(default_role_name)
        if role is not None:
            try:
                user.roles = [role]
                self.update_user(user)
            except Exception as ex:  # noqa: BLE001
                logger.exception("Failed to update OAuth user role: %s", ex)
        return user


ENABLE_AZURE_SSO = os.getenv("ENABLE_AZURE_SSO", "false").lower() == "true"
ENABLE_GENERIC_OAUTH = os.getenv("ENABLE_GENERIC_OAUTH", "false").lower() == "true"
ENABLE_SAML_SSO = os.getenv("ENABLE_SAML_SSO", "false").lower() == "true"

if ENABLE_AZURE_SSO and (ENABLE_SAML_SSO or ENABLE_GENERIC_OAUTH):
    logger.warning(
        "Multiple SSO flags are enabled. "
        "Azure SSO configuration will be used.",
    )
elif ENABLE_GENERIC_OAUTH and ENABLE_SAML_SSO:
    logger.warning(
        "Both ENABLE_GENERIC_OAUTH and ENABLE_SAML_SSO are true. "
        "Generic OAuth configuration will be used.",
    )

if ENABLE_AZURE_SSO:
    AZURE_TENANT_ID = os.getenv("AZURE_TENANT_ID", "").strip()
    AZURE_CLIENT_ID = os.getenv("AZURE_CLIENT_ID", "").strip()
    AZURE_CLIENT_SECRET = os.getenv("AZURE_CLIENT_SECRET", "").strip()
    AZURE_METADATA_URL = os.getenv(
        "AZURE_METADATA_URL",
        (
            f"https://login.microsoftonline.com/{AZURE_TENANT_ID}"
            "/v2.0/.well-known/openid-configuration"
        ),
    ).strip()
    AZURE_USE_METADATA_DISCOVERY = (
        os.getenv("AZURE_USE_METADATA_DISCOVERY", "false").lower() == "true"
    )
    AZURE_JWKS_URI = os.getenv(
        "AZURE_JWKS_URI",
        (
            f"https://login.microsoftonline.com/{AZURE_TENANT_ID}"
            "/discovery/v2.0/keys"
        ),
    ).strip()

    missing_azure_vars = [
        name
        for name, value in (
            ("AZURE_TENANT_ID", AZURE_TENANT_ID),
            ("AZURE_CLIENT_ID", AZURE_CLIENT_ID),
            ("AZURE_CLIENT_SECRET", AZURE_CLIENT_SECRET),
        )
        if not value
    ]

    if missing_azure_vars:
        logger.error(
            "Azure SSO is enabled but required env vars are missing: %s. "
            "Falling back to AUTH_DB.",
            ", ".join(missing_azure_vars),
        )
        AUTH_TYPE = AUTH_DB
    else:
        AUTH_TYPE = AUTH_OAUTH
        AUTH_USER_REGISTRATION = True
        AUTH_USER_REGISTRATION_ROLE = os.getenv(
            "AUTH_USER_REGISTRATION_ROLE",
            "Gamma",
        )
        AUTH_ROLES_SYNC_AT_LOGIN = True
        AUTH_ROLES_MAPPING = _get_json_env(
            "AUTH_ROLES_MAPPING_JSON",
            {},
        )

        azure_authorize_url = (
            f"https://login.microsoftonline.com/{AZURE_TENANT_ID}"
            "/oauth2/v2.0/authorize"
        )
        azure_access_token_url = (
            f"https://login.microsoftonline.com/{AZURE_TENANT_ID}"
            "/oauth2/v2.0/token"
        )
        azure_issuer = (
            f"https://login.microsoftonline.com/{AZURE_TENANT_ID}/v2.0"
        )

        azure_remote_app: dict[str, Any] = {
            "client_id": AZURE_CLIENT_ID,
            "client_secret": AZURE_CLIENT_SECRET,
            "api_base_url": "https://graph.microsoft.com/v1.0/",
            # Keep explicit endpoints so /login/azure can redirect even when
            # OIDC discovery endpoint is not reachable in restricted networks.
            "authorize_url": azure_authorize_url,
            "access_token_url": azure_access_token_url,
            "jwks_uri": AZURE_JWKS_URI,
            "client_kwargs": {
                "scope": "openid email profile User.Read"
            },
        }
        if AZURE_USE_METADATA_DISCOVERY:
            azure_remote_app["server_metadata_url"] = AZURE_METADATA_URL
        else:
            # Provide deterministic OIDC metadata in non-discovery mode so
            # Authlib always has jwks_uri during token verification.
            azure_remote_app["server_metadata"] = {
                "issuer": azure_issuer,
                "authorization_endpoint": azure_authorize_url,
                "token_endpoint": azure_access_token_url,
                "jwks_uri": AZURE_JWKS_URI,
            }

        OAUTH_PROVIDERS = [
            {
                "name": "azure",
                "icon": "fa-windows",
                "token_key": "access_token",
                "remote_app": azure_remote_app,
            }
        ]
        if os.getenv("OAUTH_TLS_INSECURE_SKIP_VERIFY", "false").lower() == "true":
            OAUTH_PROVIDERS[0]["remote_app"]["verify"] = False
            OAUTH_PROVIDERS[0]["remote_app"]["client_kwargs"]["verify"] = False
            logger.warning(
                "OAuth TLS certificate verification is DISABLED for local testing only."
            )
        CustomSsoSecurityManager.authoauthview = AzureAuthOAuthView
        CUSTOM_SECURITY_MANAGER = CustomSsoSecurityManager
        logger.info(
            "Azure SSO configured successfully for tenant '%s'. OAuth callback: %s/oauth-authorized/azure",
            AZURE_TENANT_ID,
            WEBSERVER_BASEURL,
        )
elif ENABLE_GENERIC_OAUTH:
    AUTH_TYPE = AUTH_OAUTH
    AUTH_USER_REGISTRATION = True
    AUTH_USER_REGISTRATION_ROLE = os.getenv(
        "AUTH_USER_REGISTRATION_ROLE",
        "Gamma",
    )
    AUTH_ROLES_SYNC_AT_LOGIN = True
    AUTH_ROLES_MAPPING = _get_json_env(
        "AUTH_ROLES_MAPPING_JSON",
        {},
    )

    generic_providers = _get_json_env("OAUTH_PROVIDERS_JSON", [])
    if not isinstance(generic_providers, list) or len(generic_providers) == 0:
        logger.warning("OAUTH_PROVIDERS_JSON must be a JSON array. Falling back to AUTH_DB.")
        AUTH_TYPE = AUTH_DB
    else:
        OAUTH_PROVIDERS = generic_providers
        CUSTOM_SECURITY_MANAGER = CustomSsoSecurityManager
elif ENABLE_SAML_SSO:
    AUTH_TYPE = AUTH_OAUTH
    AUTH_USER_REGISTRATION = True
    AUTH_USER_REGISTRATION_ROLE = os.getenv(
        "AUTH_USER_REGISTRATION_ROLE",
        "Gamma",
    )
    AUTH_ROLES_SYNC_AT_LOGIN = True

    AUTH_ROLES_MAPPING = _get_json_env(
        "AUTH_ROLES_MAPPING_JSON",
        {},
    )

    OAUTH_PROVIDERS = [
        {
            "name": "saml",
            "icon": "fa-address-card",
            "token_key": "access_token",
            "remote_app": {
                "client_id": os.getenv("SAML_CLIENT_ID", ""),
                "client_secret": os.getenv("SAML_CLIENT_SECRET", ""),
                "client_kwargs": {
                    "scope": os.getenv(
                        "SAML_SCOPE",
                        "openid profile email",
                    )
                },
                "server_metadata_url": os.getenv("SAML_METADATA_URL", ""),
                "authorize_url": os.getenv("SAML_AUTHORIZE_URL", ""),
                "access_token_url": os.getenv("SAML_ACCESS_TOKEN_URL", ""),
                "api_base_url": os.getenv("SAML_API_BASE_URL", ""),
            },
        }
    ]
else:
    AUTH_TYPE = AUTH_DB
 
# -----------------------------

# Logging (unchanged)

# -----------------------------

log_level_text = os.getenv("SUPERSET_LOG_LEVEL", "INFO")

LOG_LEVEL = getattr(logging, log_level_text.upper(), logging.INFO)
 
# -----------------------------

# Cypress test override (unchanged)

# -----------------------------

if os.getenv("CYPRESS_CONFIG") == "true":

    base_dir = os.path.dirname(__file__)

    module_folder = os.path.abspath(

        os.path.join(base_dir, "../../tests/integration_tests/")

    )

    sys.path.insert(0, module_folder)

    from superset_test_config import *  # noqa

    sys.path.pop(0)
 
# -----------------------------

# Optional local overrides

# -----------------------------

try:

    import superset_config_docker

    from superset_config_docker import *  # noqa: F403
 
    logger.info(

        "Loaded your Docker configuration at [%s]", superset_config_docker.__file__

    )

except ImportError:

    logger.info("Using default Docker config...")

ASK_ANALYTICS_CONNECT_ORIGINS = [
    origin.strip().rstrip("/")
    for origin in os.getenv(
        "ASK_ANALYTICS_CONNECT_ORIGINS",
        (
            os.getenv("ASK_ANALYTICS_BACKEND_BASE_URL")
            or os.getenv("ASK_ANALYTICS_BASE_URL")
            or os.getenv("ASK_ANALYTICS_API_BASE_URL")
            or ""
        ),
    ).split(",")
    if origin.strip()
]



AUDIO_MEDIA_ORIGINS = [
    origin.strip()
    for origin in os.getenv(
        "AUDIO_MEDIA_ORIGINS").split(",")
    if origin.strip()
]


EMBEDDED_PARENT_ORIGINS = _split_origin_env(
    "EMBEDDED_PARENT_ORIGINS",
    CXLOOP_URL,
)


def _append_unique_csp_sources(
    csp: dict[str, list[str] | str],
    directive: str,
    default_sources: list[str],
    sources: list[str],
) -> None:
    """Add explicitly configured sources while preserving the base CSP."""
    current_sources = csp.setdefault(directive, default_sources.copy())
    if isinstance(current_sources, str):
        current_sources = [current_sources]
        csp[directive] = current_sources

    for source in sources:
        if source not in current_sources:
            current_sources.append(source)


TALISMAN_CONFIG = deepcopy(DEFAULT_TALISMAN_CONFIG)
TALISMAN_DEV_CONFIG = deepcopy(DEFAULT_TALISMAN_DEV_CONFIG)

for talisman_config in (TALISMAN_CONFIG, TALISMAN_DEV_CONFIG):
    content_security_policy = talisman_config["content_security_policy"]
    _append_unique_csp_sources(
        content_security_policy,
        "frame-ancestors",
        ["'self'"],
        EMBEDDED_PARENT_ORIGINS,
    )
    _append_unique_csp_sources(
        content_security_policy,
        "media-src",
        ["'self'", "blob:", "data:"],
        AUDIO_MEDIA_ORIGINS,
    )
    _append_unique_csp_sources(
        content_security_policy,
        "connect-src",
        ["'self'"],
        AUDIO_MEDIA_ORIGINS + ASK_ANALYTICS_CONNECT_ORIGINS,
    )
    # CSP frame-ancestors is the allowlist; SAMEORIGIN would reject approved parents.
    talisman_config["frame_options"] = None
