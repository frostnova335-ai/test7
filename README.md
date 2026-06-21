oot@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker compose -f docker-compose-non-dev.yml up -d
[+] up 5/6
 ✔ Container superset_cache       Running                                                                                                              0.0s
 ✔ Container superset_db          Recreated                                                                                                            1.0s
 ⠙ Container superset_init        Waiting                                                                                                             32.2s
 ✔ Container superset_worker_beat Recreated                                                                                                            0.3s
 ✔ Container superset_worker      Recreated                                                                                                            0.3s
 ✔ Container superset_app         Recreated                                                                                                            0.3s
service "superset-init" didn't complete successfully: exit 1
root@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker logs superset_init
Checking for stale uv lock files...
Installing superset-core in editable mode
Resolved 1 package in 3ms
   Building apache-superset-core @ file:///app/superset-core
      Built apache-superset-core @ file:///app/superset-core
Prepared 1 package in 1.34s
Uninstalled 1 package in 15ms
warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
         If the cache and target directories are on different filesystems, hardlinking may not be supported.
         If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
Installed 1 package in 5ms
 ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
Reinstalling the app in editable mode
Resolved 154 packages in 2.58s
   Building apache-superset @ file:///app
   Building apache-superset-core @ file:///app/superset-core
      Built apache-superset @ file:///app
      Built apache-superset-core @ file:///app/superset-core
Prepared 2 packages in 1.12s
Uninstalled 2 packages in 16ms
warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
         If the cache and target directories are on different filesystems, hardlinking may not be supported.
         If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
Installed 2 packages in 6ms
 ~ apache-superset==1.0.7 (from file:///app)
 ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
Installing postgres requirements
Resolved 155 packages in 1.80s
   Building apache-superset @ file:///app
      Built apache-superset @ file:///app
Prepared 1 package in 941ms
Uninstalled 1 package in 1ms
warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
         If the cache and target directories are on different filesystems, hardlinking may not be supported.
         If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
Installed 1 package in 5ms
 ~ apache-superset==1.0.7 (from file:///app)
Skipping local overrides
Unknown Operation!!!
######################################################################
Init Step 1/3 [Starting] -- Applying DB migrations
######################################################################
Loaded your LOCAL configuration at [/app/pythonpath/superset_config.py]
2026-06-21 19:24:26,337:INFO:alembic.runtime.migration:Context impl PostgresqlImpl.
2026-06-21 19:24:26,337:INFO:alembic.runtime.migration:Will assume transactional DDL.
2026-06-21 19:24:26,797:INFO:superset.app:Pending database migrations: run 'superset db upgrade'
INFO  [alembic.env] Starting the migration scripts.
INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
INFO  [alembic.runtime.migration] Will assume transactional DDL.
ERROR [flask_migrate] Error: Can't locate revision identified by 'b8d1f3a5c7e9'
root@EC03
