root@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker compose -f docker-compose-non-dev.yml up -d
[+] up 5/6
 ✔ Container superset_cache       Running                                                                                       0.0s
 ✔ Container superset_db          Running                                                                                       0.0s
 ⠋ Container superset_init        Waiting                                                                                      24.5s
 ✔ Container superset_app         Recreated                                                                                     0.1s
 ✔ Container superset_worker      Recreated                                                                                     0.1s
 ✔ Container superset_worker_beat Recreated                                                                                     0.1s
service "superset-init" didn't complete successfully: exit 1
root@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker compose -f docker-compose-non-dev.yml logs superset-init
superset_init  | Checking for stale uv lock files...
superset_init  | Installing superset-core in editable mode
superset_init  | Resolved 1 package in 3ms
superset_init  |    Building apache-superset-core @ file:///app/superset-core
superset_init  |       Built apache-superset-core @ file:///app/superset-core
superset_init  | Prepared 1 package in 1.42s
superset_init  | Uninstalled 1 package in 16ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 1 package in 5ms
superset_init  |  ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
superset_init  | Reinstalling the app in editable mode
superset_init  | Resolved 162 packages in 2.27s
superset_init  |    Building apache-superset @ file:///app
superset_init  |    Building apache-superset-core @ file:///app/superset-core
superset_init  |       Built apache-superset @ file:///app
superset_init  |       Built apache-superset-core @ file:///app/superset-core
superset_init  | Prepared 2 packages in 1.23s
superset_init  | Uninstalled 2 packages in 11ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 2 packages in 8ms
superset_init  |  ~ apache-superset==1.0.7 (from file:///app)
superset_init  |  ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
superset_init  | Installing postgres requirements
superset_init  | Resolved 163 packages in 1.75s
superset_init  |    Building apache-superset @ file:///app
superset_init  |       Built apache-superset @ file:///app
superset_init  | Prepared 1 package in 843ms
superset_init  | Uninstalled 1 package in 1ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 1 package in 6ms
superset_init  |  ~ apache-superset==1.0.7 (from file:///app)
superset_init  | Skipping local overrides
superset_init  | Unknown Operation!!!
superset_init  | ######################################################################
superset_init  | Init Step 1/3 [Starting] -- Applying DB migrations
superset_init  | ######################################################################
superset_init  | Loaded your LOCAL configuration at [/app/pythonpath/superset_config.py]
superset_init  | 2026-06-18 12:04:28,605:INFO:alembic.runtime.migration:Context impl PostgresqlImpl.
superset_init  | 2026-06-18 12:04:28,606:INFO:alembic.runtime.migration:Will assume transactional DDL.
superset_init  | 2026-06-18 12:04:29,233:INFO:superset.app:Pending database migrations: run 'superset db upgrade'
superset_init  | 2026-06-18 12:04:29,881:ERROR:superset.app:Failed to create app
superset_init  | Traceback (most recent call last):
superset_init  |   File "/app/superset/app.py", line 75, in create_app
superset_init  |     app_initializer.init_app()
superset_init  |   File "/app/superset/initialization/__init__.py", line 771, in init_app
superset_init  |     self.init_app_in_ctx()
superset_init  |   File "/app/superset/initialization/__init__.py", line 642, in init_app_in_ctx
superset_init  |     self.init_views()
superset_init  |   File "/app/superset/initialization/__init__.py", line 165, in init_views
superset_init  |     from superset.dashboards.api import DashboardRestApi
superset_init  |   File "/app/superset/dashboards/api.py", line 24, in <module>
superset_init  |     from superset.commands.dashboard.export_data import ExportDashboardCommand
superset_init  |   File "/app/superset/commands/dashboard/export_data.py", line 12, in <module>
superset_init  |     from superset.errors import DashboardAccessDeniedError, DashboardNotFoundError
superset_init  | ImportError: cannot import name 'DashboardAccessDeniedError' from 'superset.errors' (/app/superset/errors.py)
superset_init  | Traceback (most recent call last):
superset_init  |   File "/app/.venv/bin/superset", line 10, in <module>
superset_init  |     sys.exit(superset())
superset_init  |              ^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1442, in __call__
superset_init  |     return self.main(*args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1363, in main
superset_init  |     rv = self.invoke(ctx)
superset_init  |          ^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1827, in invoke
superset_init  |     super().invoke(ctx)
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1226, in invoke
superset_init  |     return ctx.invoke(self.callback, **ctx.params)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 794, in invoke
superset_init  |     return callback(*args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/decorators.py", line 34, in new_func
superset_init  |     return f(get_current_context(), *args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/flask/cli.py", line 355, in decorator
superset_init  |     app = __ctx.ensure_object(ScriptInfo).load_app()
superset_init  |           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/flask/cli.py", line 302, in load_app
superset_init  |     app = self.create_app()
superset_init  |           ^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/superset/cli/main.py", line 52, in create_app
superset_init  |     return create_superset_app()
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/superset/app.py", line 75, in create_app
superset_init  |     app_initializer.init_app()
superset_init  |   File "/app/superset/initialization/__init__.py", line 771, in init_app
superset_init  |     self.init_app_in_ctx()
superset_init  |   File "/app/superset/initialization/__init__.py", line 642, in init_app_in_ctx
superset_init  |     self.init_views()
superset_init  |   File "/app/superset/initialization/__init__.py", line 165, in init_views
superset_init  |     from superset.dashboards.api import DashboardRestApi
superset_init  |   File "/app/superset/dashboards/api.py", line 24, in <module>
superset_init  |     from superset.commands.dashboard.export_data import ExportDashboardCommand
superset_init  |   File "/app/superset/commands/dashboard/export_data.py", line 12, in <module>
superset_init  |     from superset.errors import DashboardAccessDeniedError, DashboardNotFoundError
superset_init  | ImportError: cannot import name 'DashboardAccessDeniedError' from 'superset.errors' (/app/superset/errors.py)
