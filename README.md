# test-corepack-local-version
Tests behavior of corepack when local version of package manager is available

## Setup

1. Clone this repository.
2. Test either with fresh installation of Node.js, or one where corepack is not enabled.

## Test

Example run with fresh installation of Node.js 20.x using fnm:

```console
$ fnm ls
* system

$ fnm install 20
Installing Node v20.18.1 (x64)

$ fnm use 20
Using Node v20.18.1

$ yarn --version
-bash: /run/user/1000/fnm_multishells/32097_1735069336815/bin/yarn: No such file or directory

$ corepack enable

$ yarn --version
! Corepack is about to download https://repo.yarnpkg.com/4.2.2/packages/yarnpkg-cli/bin/yarn.js
? Do you want to continue? [Y/n]
```
