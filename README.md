# test-corepack-local-version
Tests behavior of corepack when local version of package manager is available

## Setup

1. Clone this repository.
2. Test either with fresh installation of Node.js, or one where corepack is not enabled.

## Test

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

$ yarn --version
-bash: yarn: command not found

$ which yarn
/usr/bin/which: no yarn in (/home/ec2-user/.nvm/versions/node/v20.18.1/bin:/run/user/1000/fnm_multishells/33476_1735070711467/bin:/home/ec2-user/.local/share/fnm:/home/ec2-user/.local/bin:/home/ec2-user/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin

$ corepack enable

$ yarn --version
4.2.2

$ which yarn
~/.nvm/versions/node/v20.18.1/bin/yarn

$ cat ~/.nvm/versions/node/v20.18.1/bin/yarn
#!/usr/bin/env node
process.env.COREPACK_ENABLE_DOWNLOAD_PROMPT??='1'
require('./lib/corepack.cjs').runMain(['yarn', ...process.argv.slice(2)]);
```

[nvm]: https://github.com/nvm-sh/nvm
