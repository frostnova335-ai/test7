=> ERROR [superset-worker superset-node-ci 11/12] RUN --mount=type=cache,target=/root/.npm     --mount=type=cache,target=/root/.cache     if [ "fa  197.3s
------
 > [superset-worker superset-node-ci 11/12] RUN --mount=type=cache,target=/root/.npm     --mount=type=cache,target=/root/.cache     if [ "false" = "false" ]; then       npm ci --workspaces --include-workspace-root ||       npm install --workspaces --include-workspace-root;     else       echo "Skipping 'npm ci' in dev mode - will run in docker-frontend.sh";     fi:
5.834 npm error code EUSAGE
5.834 npm error
5.834 npm error `npm ci` can only install packages when your package.json and package-lock.json or npm-shrinkwrap.json are in sync. Please update your lock file with `npm install` before continuing.
5.834 npm error
5.834 npm error Missing: core-js@3.40.0 from lock file
5.834 npm error Missing: d3-color@1.4.1 from lock file
5.834 npm error
5.834 npm error Clean install a project
5.834 npm error
5.834 npm error Usage:
5.834 npm error npm ci
5.834 npm error
5.834 npm error Options:
5.834 npm error [--install-strategy <hoisted|nested|shallow|linked>] [--legacy-bundling]
5.834 npm error [--global-style] [--omit <dev|optional|peer> [--omit <dev|optional|peer> ...]]
5.834 npm error [--include <prod|dev|optional|peer> [--include <prod|dev|optional|peer> ...]]
5.834 npm error [--strict-peer-deps] [--foreground-scripts] [--ignore-scripts] [--no-audit]
5.834 npm error [--no-bin-links] [--no-fund] [--dry-run]
5.834 npm error [-w|--workspace <workspace-name> [-w|--workspace <workspace-name> ...]]
5.834 npm error [-ws|--workspaces] [--include-workspace-root] [--install-links]
5.834 npm error
5.834 npm error aliases: clean-install, ic, install-clean, isntall-clean
5.834 npm error
5.834 npm error Run "npm help ci" for more info
5.837 npm notice
5.837 npm notice New major version of npm available! 10.8.2 -> 11.17.0
5.837 npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.17.0
5.837 npm notice To update run: npm install -g npm@11.17.0
5.837 npm notice
5.838 npm error A complete log of this run can be found in: /root/.npm/_logs/2026-06-22T06_20_31_468Z-debug-0.log
28.37 npm warn deprecated whatwg-encoding@3.1.1: Use @exodus/bytes instead for a more spec-conformant and faster implementation
28.74 npm warn deprecated viewport-mercator-project@7.0.4: Package no longer supported. Contact Support at https://www.npmjs.com/support for more info.
31.49 npm warn deprecated semver-diff@5.0.0: Deprecated as the semver package now supports this built-in.
31.78 npm warn deprecated rimraf@3.0.2: Rimraf versions prior to v4 are no longer supported
32.67 npm warn deprecated tar@6.2.1: Old versions of tar are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
33.92 npm warn deprecated topojson@1.6.27: Use topojson-client, topojson-server or topojson-simplify directly.
35.17 npm warn deprecated nomnom@1.8.1: Package no longer supported. Contact support@npmjs.com for more info.
36.20 npm warn deprecated lodash.isequal@4.5.0: This package is deprecated. Use require('node:util').isDeepStrictEqual instead.
36.20 npm warn deprecated lodash.get@4.4.2: This package is deprecated. Use the optional chaining (?.) operator instead.
36.64 npm warn deprecated node-domexception@1.0.0: Use your platform's native DOMException instead
37.69 npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
38.09 npm warn deprecated puppeteer@22.15.0: < 24.15.0 is no longer supported
38.24 npm warn deprecated glob@7.2.3: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
40.43 npm warn deprecated domexception@4.0.0: Use your platform's native DOMException instead
43.23 npm warn deprecated abab@2.0.6: Use your platform's native atob() and btoa() methods instead
44.43 npm warn deprecated @types/react-virtualized-auto-sizer@1.0.8: This is a stub types definition. react-virtualized-auto-sizer provides its own type definitions, so you do not need this installed.
48.97 npm warn deprecated @humanwhocodes/config-array@0.13.0: Use @eslint/config-array instead
48.97 npm warn deprecated @humanwhocodes/object-schema@2.0.3: Use @eslint/object-schema instead
52.68 npm warn deprecated @babel/polyfill@7.12.1: 🚨 This package has been deprecated in favor of separate inclusion of a polyfill and regenerator-runtime (when needed). See the @babel/polyfill docs (https://babeljs.io/docs/en/babel-polyfill) for more information.
53.35 npm warn deprecated rimraf@2.6.3: Rimraf versions prior to v4 are no longer supported
57.37 npm warn deprecated whatwg-encoding@2.0.0: Use @exodus/bytes instead for a more spec-conformant and faster implementation
61.44 npm warn deprecated glob@8.1.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
64.38 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
64.62 npm warn deprecated glob@9.3.5: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
65.55 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
66.41 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
68.20 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
69.74 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
70.21 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
70.41 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
70.44 npm warn deprecated glob@9.3.5: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
70.55 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
70.75 npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
75.25 npm warn deprecated eslint@8.57.1: This version is no longer supported. Please see https://eslint.org/version-support for other options.
196.3 npm error code ECONNRESET
196.3 npm error network aborted
196.3 npm error network This is a problem related to network connectivity.
196.3 npm error network In most cases you are behind a proxy or have bad network settings.
196.3 npm error network
196.3 npm error network If you are behind a proxy, please make sure that the
196.3 npm error network 'proxy' config is set properly.  See: 'npm help config'
196.3 npm error A complete log of this run can be found in: /root/.npm/_logs/2026-06-22T06_20_36_895Z-debug-0.log
------
target superset-worker: failed to solve: process "/bin/bash -o pipefail -c if [ \"${DEV_MODE}\" = \"false\" ]; then       npm ci --workspaces --include-workspace-root ||       npm install --workspaces --include-workspace-root;     else       echo \"Skipping 'npm ci' in dev mode - will run in docker-frontend.sh\";     fi" did not complete successfully: exit code: 1

root@EC03-B17-
