# test-corepack-local-version
Tests behavior of corepack when local version of package manager is available

## Setup

1. Clone this repository.
2. Test with fresh installation of Node.js.

## Pre-requisites

Install Node.js with network connection enabled

Example run with fresh installation of Node.js 20.x using [nvm][nvm]:
```console
$ nvm ls
            N/A
...

$ nvm install 20
...
Now using node v20.18.1 (npm v10.8.2)
Creating default alias: default -> 20 (-> v20.18.1)

$ node -v
v20.18.1

```

## Test

Run the following commands after disabling network

```console
$ yarn --version
zsh: command not found: yarn

$ which yarn
yarn not found

$ corepack enable

$ yarn --version
! Corepack is about to download https://repo.yarnpkg.com/4.5.1/packages/yarnpkg-cli/bin/yarn.js
? Do you want to continue? [Y/n] Y

/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21609
    throw new Error(
          ^

Error: Error when performing the request to https://repo.yarnpkg.com/4.5.1/packages/yarnpkg-cli/bin/yarn.js; for troubleshooting help, see https://github.com/nodejs/corepack#troubleshooting
    at fetch (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21609:11)
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async fetchUrlStream (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21639:20)
    ... 4 lines matching cause stack trace ...
    at async Object.runMain (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:23096:5) {
  [cause]: TypeError: fetch failed
      at node:internal/deps/undici/undici:13392:13
      at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
      at async fetch (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21603:16)
      at async fetchUrlStream (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21639:20)
      at async download (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21762:18)
      at async installVersion (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:21854:55)
      at async Engine.ensurePackageManager (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:22310:32)
      at async Engine.executePackageManagerRequest (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:22410:25)
      at async Object.runMain (/Users/trivikr/.nvm/versions/node/v20.18.1/lib/node_modules/corepack/dist/lib/corepack.cjs:23096:5) {
    [cause]: Error: getaddrinfo ENOTFOUND repo.yarnpkg.com
        at GetAddrInfoReqWrap.onlookupall [as oncomplete] (node:dns:120:26) {
      errno: -3008,
      code: 'ENOTFOUND',
      syscall: 'getaddrinfo',
      hostname: 'repo.yarnpkg.com'
    }
  }
}

Node.js v20.18.1

$ which yarn
/Users/trivikr/.nvm/versions/node/v20.18.1/bin/yarn

$ cat /Users/trivikr/.nvm/versions/node/v20.18.1/bin/yarn
#!/usr/bin/env node
process.env.COREPACK_ENABLE_DOWNLOAD_PROMPT??='1'
require('./lib/corepack.cjs').runMain(['yarn', ...process.argv.slice(2)]);
```

[nvm]: https://github.com/nvm-sh/nvm
