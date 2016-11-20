#HTTP Yarn

__Fast__: 
##### Yarn caches every package it downloads so it never needs to download the same package again. It also parallelizes operations to maximize resource utilization so install times are faster than ever.

__Reliable__: 
##### Using a detailed, concise lockfile format and a deterministic algorithm for installs, Yarn is able to guarantee that an install that worked on one system will work exactly the same way on any other system.

__Secure__:
##### Yarn uses checksums to verify the integrity of every installed package before its code is executed.

#VSLIDE

## WHo?

Facebook but also Google, Tile & Eposent

## Why?

Npm caveats:
* not reliable
* not always the same resolution path
* shrinkwrap not by default
* can't be offline

#VSLIDE

##How?

Yarn resolves these issues around versioning and non-determinism by using lockfiles and an install algorithm that is deterministic and reliable.

#VSLIDE

## Workflow

3steps:

__Resolution__: Resolve dependencies by making requests to the registry and recursively looking up each dependency.
__Fetching__: Looks in a global cache directory t. If it's missing, Yarn fetches the tarball for the package and places it in the global cache. Support source control full offline installs.
__Linking__: Finally, Links everything together by copying to the local node_modules folder.

#HVSLIDE

Installation:

C'est un binaire autonome

MacOsX

```
brew update
brew install yarn
```

Linux

* Debian/Ubuntu Linux
* CentOS / Fedora / RHEL
* Arch Linux
* Solus


#HSLIDE

First try

```
/usr/local/Cellar/yarn/0.17.3/libexec/lib/node_modules/yarn/bin/yarn.js:47
      throw err;
      ^

Error: ENOENT: no such file or directory, open '/Users/calvy/Library/Caches/Yarn/.roadrunner.json'
    at Error (native)
    at Object.fs.openSync (fs.js:640:18)
    at Object.fs.writeFileSync (fs.js:1333:33)
    at /usr/local/Cellar/yarn/0.17.3/libexec/lib/node_modules/yarn/node_modules/roadrunner/index.js:25:6
    at /usr/local/Cellar/yarn/0.17.3/libexec/lib/node_modules/yarn/node_modules/roadrunner/index.js:12:12
    at emitOne (events.js:101:20)
    at process.emit (events.js:188:7)
    at processEmit [as emit] (/usr/local/Cellar/yarn/0.17.3/libexec/lib/node_modules/yarn/node_modules/signal-exit/index.js:140:35)
    at process.exit (internal/process.js:146:15)
    at Command.<anonymous> (/usr/local/Cellar/yarn/0.17.3/libexec/lib/node_modules/yarn/node_modules/commander/index.js:825:13)
```

#VSLIDE

https://github.com/yarnpkg/yarn/issues/1724

```
mkdir -p ~/Library/Caches/Yarn
```

=====>

```
yarn --version
0.17.3
```

#HSLIDE

Side effect of brew instal yarn

* not os consistent
* must change the path 
`export PATH="$PATH:$HOME/.yarn/bin"`
* brew install node and break nvm

wait really instal like that?

consider using npm

```
npm i -g yarn 
```

```
yarn --version
0.17.4
```

![](./assets/img/yarn.0.16.1.png)

#VSLIDE

Ok let's go

```
info No lockfile found.
error npm-shrinkwrap.json found. This will not be updated or respected. See https://yarnpkg.com/en/docs/migrating-from-npm for more information.
warning @coorpacademy/coorpacademy@4.60.1: No license field
[1/4] 🔍  Resolving packages...
error An unexpected error occurred: "https://registry.yarnpkg.com/@coorpacademy%2fcoorpacademy-core: User not found".
info If you think this is a bug, please open a bug report with the information provided in "/Users/calvy/Documents/Boulot/Sources/coorpacademy/yarn-error.log".
info Visit https://yarnpkg.com/en/docs/cli/install for documentation about this command.
```

WHAT?

```
_auth="xxxxxx="
email=lc@coorpacademy.com
//registry.npmjs.org/:_authToken=xxxxxxxxxx
@coorpacademy:registry=http://registry.npmjs.org/
```

#HSLIDE
```
info No lockfile found.
error npm-shrinkwrap.json found. This will not be updated or respected. See https://yarnpkg.com/en/docs/migrating-from-npm for more information.
warning @coorpacademy/coorpacademy@4.60.1: No license field
[1/4] 🔍  Resolving packages...
warning minimatch@2.0.10: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning grunt > minimatch@0.2.14: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning cli > glob > minimatch@0.3.0: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning grunt > glob > minimatch@0.2.14: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning kraken-devtools > minimatch@0.2.14: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning bower > glob > minimatch@2.0.10: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
warning grunt > glob > graceful-fs@1.2.3: graceful-fs v3.0.0 and before will fail on node releases >= v7.0. Please update to graceful-fs@^4.0.0 as soon as possible. Use 'npm ls graceful-fs' to find it in the tree.
warning grunt-html2js > jade@1.11.0: Jade has been renamed to pug, please install the latest version of pug instead of jade
warning request > node-uuid@1.4.7: use uuid module instead
warning bower > request > node-uuid@1.4.7: use uuid module instead
warning bower > bower-json > graceful-fs@2.0.3: graceful-fs v3.0.0 and before will fail on node releases >= v7.0. Please update to graceful-fs@^4.0.0 as soon as possible. Use 'npm ls graceful-fs' to find it in the tree.
warning bower > insight > tough-cookie@0.12.1: ReDoS vulnerability parsing Set-Cookie https://nodesecurity.io/advisories/130
warning grunt-html2js > jade > transformers@2.1.0: Deprecated, use jstransformer
warning grunt-favicons > cheerio > cheerio-select > CSSselect@0.7.0: the module is now available as 'css-select'
warning grunt-favicons > cheerio > cheerio-select > CSSselect > CSSwhat@0.4.7: the module is now available as 'css-what'
[2/4] 🚚  Fetching packages...
error An unexpected error occurred: "https://registry.yarnpkg.com/@coorpacademy/squirrel/-/squirrel-2.3.0.tgz: invalid tar file".
```

`yarn config set registry https://registry.npmjs.org/`

```
# THIS IS AN AUTOGENERATED FILE. DO NOT EDIT THIS FILE DIRECTLY.
# yarn lockfile v1


registry "https://registry.npmjs.org/"
email system@coorpacademy.com
username coorpadmin
```

#VSLIDE

run

```
  battleMapper function
    1) "before all" hook
Bugsnag:  Bugsnag: error notifying bugsnag.com - Error: Current release stage not permitted to send events to Bugsnag.
Bugsnag:  Error: Could not locate the bindings file. Tried:
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/build/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/build/Debug/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/build/Release/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/out/Debug/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/Debug/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/out/Release/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/Release/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/build/default/bcrypt_lib.node
 → /Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/bcrypt/compiled/6.5.0/darwin/x64/bcrypt_lib.node
    at bindings (node_modules/bindings/bindings.js:88:9)
    at Object.<anonymous> (node_modules/bcrypt/bcrypt.js:3:35)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (core/models/user.js:8:16)
    at require (internal/module.js:20:19)
    at loadSchema (core/models/index.js:42:24)
    at apply (node_modules/lodash/lodash.js:499:17)
    at wrapper (node_modules/lodash/lodash.js:5383:16)
    at Array.reduce (native)
    at createConnection (core/models/index.js:38:17)
    at db (test/server/context.js:28:26)
    at apply (node_modules/lodash/lodash.js:497:27)
    at wrapper (node_modules/lodash/lodash.js:5383:16)
    at node_modules/async/lib/async.js:718:13
    at Immediate.iterate (node_modules/async/lib/async.js:262:13)


```

????

`npm rebuild`


#HSLIDE

##Advices

To make sure your app works consistently, you should always save the yarn.lock file in your code repository.

## Caveats

Don't use npm-shrinkwrap.json on first yarn.lock
Missing assets in --production

```
Error: Cannot find module 'semver'
    at Function.Module._resolveFilename (module.js:455:15)
    at Function.Module._load (module.js:403:25)
    at Function._load (/Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/pmx/lib/transaction.js:62:21)
    at Module.require (module.js:483:17)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (/Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/baucis/Api/index.js:3:14)
    at Module._compile (module.js:556:32)
    at Object.Module._extensions..js (module.js:565:10)
    at Module.load (module.js:473:32)
    at tryModuleLoad (module.js:432:12)
    at Function.Module._load (module.js:424:3)
    at Function._load (/Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/pmx/lib/transaction.js:62:21)
    at Module.require (module.js:483:17)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (/Users/calvy/Documents/Boulot/Sources/coorpacademy/node_modules/baucis/index.js:
```

No support on heroku

#VSLIDE

`yarn outdated`

![](./assets/img/yarn outdated.png)

#VSLIDE

##Perf

`time npm i`                   ===> real  4m22.777s

`time $(yarn && npm rebuild)`  ===> real   1m34.147s

