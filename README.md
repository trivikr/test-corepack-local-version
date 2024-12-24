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
4.2.2

$ which yarn
/Users/trivikr/.nvm/versions/node/v20.18.1/bin/yarn

$ cat /Users/trivikr/.nvm/versions/node/v20.18.1/bin/yarn
#!/usr/bin/env node
process.env.COREPACK_ENABLE_DOWNLOAD_PROMPT??='1'
require('./lib/corepack.cjs').runMain(['yarn', ...process.argv.slice(2)]);
```

[nvm]: https://github.com/nvm-sh/nvm
