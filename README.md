 => ERROR [superset-worker-beat lean 3/6] RUN --mount=type=cache,target=/app/superset_home/.cache/uv     /app/docker/pip-inst  10.9s
------
 > [superset-worker-beat lean 3/6] RUN --mount=type=cache,target=/app/superset_home/.cache/uv     /app/docker/pip-install.sh --requires-build-essential -r requirements/base.txt &&     uv pip install -e ".[postgres,duckdb]":
0.234 Installing build-essential for package builds...
4.079 W: OpenPGP signature verification failed: http://deb.debian.org/debian-security trixie-security InRelease: Sub-process /usr/bin/sqv returned an error code (1), error message is: Signature by B0CAB9266E8C3929798B3EEEBDE6D2B9216EC7A8 was created after the --not-after date. Signature by 89C87ACEA5DD6B8E6A7068808E9F831205B4BA95 was created after the --not-after date.
4.079 E: The repository 'http://deb.debian.org/debian-security trixie-security InRelease' is not signed.
4.082 Using pip cache...
7.407 Resolved 165 packages in 2.94s
7.420    Building apache-superset-core @ file:///app/superset-core
7.450 Downloading babel (9.7MiB)
7.460 Downloading pandas (11.7MiB)
7.477 Downloading pillow (6.3MiB)
7.477 Downloading numpy (17.4MiB)
7.479 Downloading pygments (1.2MiB)
7.480 Downloading apsw (6.5MiB)
7.481 Downloading cryptography (4.0MiB)
7.481 Downloading zstandard (5.2MiB)
7.482 Downloading selenium (8.9MiB)
7.483 Downloading flask-appbuilder (2.1MiB)
7.525 Downloading brotli (2.8MiB)
7.526 Downloading pyarrow (38.9MiB)
7.527 Downloading pydantic-core (1.9MiB)
7.561 Downloading sqlalchemy (1.6MiB)
9.261    Building python-geohash==0.8.5
9.261    Building odfpy==1.4.1
9.263    Building pgsanity==0.2.9
9.278    Building wtforms-json==0.3.5
9.835  Downloaded pydantic-core
10.45   × Failed to build `python-geohash==0.8.5`
10.45   ├─▶ The build backend returned an error
10.45   ╰─▶ Call to `setuptools.build_meta:__legacy__.build_wheel` failed (exit
10.45       status: 1)
10.45
10.45       [stdout]
10.45       running bdist_wheel
10.45       running build
10.45       running build_py
10.45       creating build/lib.linux-x86_64-cpython-311
10.45       copying geohash.py -> build/lib.linux-x86_64-cpython-311
10.45       copying quadtree.py -> build/lib.linux-x86_64-cpython-311
10.45       copying jpgrid.py -> build/lib.linux-x86_64-cpython-311
10.45       copying jpiarea.py -> build/lib.linux-x86_64-cpython-311
10.45       running build_ext
10.45       building '_geohash' extension
10.45       creating build/temp.linux-x86_64-cpython-311/src
10.45       g++ -Wsign-compare -DNDEBUG -g -fwrapv -O3 -Wall -fPIC -DPYTHON_MODULE=1
10.45       -I/app/superset_home/.cache/uv/builds-v0/.tmpv9jzMj/include
10.45       -I/usr/local/include/python3.11 -c src/geohash.cpp -o
10.45       build/temp.linux-x86_64-cpython-311/src/geohash.o
10.45
10.45       [stderr]
10.45       error: command 'g++' failed: No such file or directory
10.45
10.45
10.45 hint: Build failures usually indicate a problem with the package or the build environment
------
[+] build 0/4
 ⠙ Image bu-digital-insightshub-backend-superset-init        Building                                                         643.1s
 ⠙ Image bu-digital-insightshub-backend-superset-worker      Building                                                         643.1s
 ⠙ Image bu-digital-insightshub-backend-superset-worker-beat Building                                                         643.1s
 ⠙ Image bu-digital-insightshub-backend-superset             Building                                                         643.1s
target superset-worker: failed to solve: process "/bin/bash -o pipefail -c /app/docker/pip-install.sh --requires-build-essential -r requirements/base.txt &&     uv pip install -e \".[postgres,duckdb]\"" did not complete successfully: exit code: 1
