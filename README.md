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
Installing Node v20.14.0 (arm64)

$ fnm use 20
Using Node v20.14.0

$ yarn --version
zsh: command not found: yarn

$ corepack enable

$ yarn --version
4.2.2
```