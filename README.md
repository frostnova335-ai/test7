root@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker ps -a
CONTAINER ID   IMAGE                                                 COMMAND                  CREATED         STATUS                     PORTS                        NAMES
ed0dee00c401   bu-digital-insightshub-backend-superset-worker        "/bin/bash -lc 'expo…"   6 minutes ago   Created                                                 superset_worker
d8832a28b0e9   bu-digital-insightshub-backend-superset               "/bin/bash -lc 'expo…"   6 minutes ago   Created                                                 superset_app
a4205a02262d   bu-digital-insightshub-backend-superset-worker-beat   "/bin/bash -lc 'expo…"   6 minutes ago   Created                                                 superset_worker_beat
30ced6e4fd90   bu-digital-insightshub-backend-superset-init          "/bin/bash -lc 'expo…"   6 minutes ago   Exited (1) 5 minutes ago                                superset_init
9294550d33c3   postgres:16                                           "docker-entrypoint.s…"   6 minutes ago   Up 6 minutes               10.91.41.82:5432->5432/tcp   superset_db
92f9f113863a   redis:7                                               "docker-entrypoint.s…"   4 months ago    Up 5 weeks                 6379/tcp                     superset_cache
