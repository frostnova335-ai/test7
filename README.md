Hi Shivam,

 

Please find the detailed steps for the implementation of SAML in Superset.

 

1. Requirements

Superset Installed locally or using Docker Domain Public or internal domain SSL Certs For signing SAML requests Identity Provider Azure AD, Okta, ADFS, etc. HTTPS Required for secure SAML communication

2. Project Structure

superset-saml/
├── docker-compose.yml
├── superset_config.py
├── certs/
│ ├── private.key
│ └── public.crt
3. Generate SSL Certs (for signing SAML requests)

mkdir -p certs
openssl req -newkey rsa:2048 -nodes -keyout certs/private.key -x509 -days 365 -out certs/public.crt
Use your domain (e.g. superset.mycompany.com) as the Common Name when prompted.

4. Update superset_config.py

Create or edit superset_config.py with the following full config:

from flask_appbuilder.security.manager import AUTH_SAML
import os

# Enable SAML authentication
AUTH_TYPE = AUTH_SAML
AUTH_USER_REGISTRATION = True
AUTH_USER_REGISTRATION_ROLE = "Gamma" # Default role for new users
AUTH_ROLE_ADMIN = "Admin" # Optional: grant admin access

# SAML Metadata from your IdP (use either URL or local file)
SAML_METADATA_URL = "https://login.microsoftonline.com/<your-tenant-id>/federationmetadata/2007-06/federationmetadata.xml"
# SAML_METADATA_LOCAL_FILE_PATH = "/app/saml/metadata.xml"

# SP Configuration (your Superset server)
SAML_ENTITY_ID = "https://superset.mycompany.com/saml/metadata"
SAML_ASSERTION_CONSUMER_SERVICE_URL = "https://superset.mycompany.com/saml/acs"

# SSL keys for signing SAML requests
SAML_SP_PUBLIC_CERT = open("/app/certs/public.crt").read()
SAML_SP_PRIVATE_KEY = open("/app/certs/private.key").read()

# Map SAML attributes to Superset fields
SAML_ATTRIBUTE_MAP = {
"User.email": ("email", ),
"User.username": ("username", ),
"User.firstname": ("first_name", ),
"User.lastname": ("last_name", ),
# Optional group-based role mapping:
# "User.groups": ("roles", )
}

ENABLE_PROXY_FIX = True # If using behind Nginx or HTTPS proxy
5. Update docker-compose.yml

Mount your configuration and certs:

services:
superset:
image: apache/superset
ports:
- "8088:8088"
volumes:
- ./superset_config.py:/app/pythonpath/superset_config.py
- ./certs:/app/certs
6. Configure Your Identity Provider (e.g. Azure AD)

Azure AD → Enterprise Applications → New App (Non-Gallery)

Set Identifier (Entity ID):
https://superset.mycompany.com/saml/metadata
Set Reply URL (ACS):
https://superset.mycompany.com/saml/acs
Set Sign-on URL (optional):
https://superset.mycompany.com/login/
Upload Superset's public.crt to Azure AD:
Go to "SAML Signing Certificate" > Upload base64-encoded X.509 certificate
Edit Attributes to Send:

User.email user.mail User.username user.userprincipalname User.firstname user.givenname User.lastname user.surname, These must match what you defined in SAML_ATTRIBUTE_MAP.

7. Restart Superset

docker-compose down
docker-compose up -d
8. Validate the Flow

Open: https://superset.mycompany.com/login/
You are redirected to your IdP (e.g., Azure login)
After login, you are redirected back to Superset
A new user is created with the correct role (Gamma/Admin)
9. Debugging Tools

Use SAML-tracer browser plugin (Firefox) to inspect SAML assertions.
Check Docker logs:
docker-compose logs superset
Ensure server time is synchronized (SAML is time-sensitive)
10. Security & Best Practices

Certs should be rotated periodically (openssl with -days 365)
Use HTTPS for production deployments
Validate your domain is protected with WAF/SSL
Configure SAML logout endpoints (SAML_SINGLE_LOGOUT_URL) if needed
Use roles claim for access control enforcement
