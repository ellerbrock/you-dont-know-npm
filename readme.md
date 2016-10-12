![npm](https://github.frapsoft.com/top/npm-logo.png)

# You Don't Know npm

[![Javascript](https://badges.frapsoft.com/javascript/code/javascript.svg?v=100)](https://github.com/ellerbrock/javascript-badges/) [![JavaScript Style Guide](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/ellerbrock/javascript-badges/) [![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=102)](https://github.com/ellerbrock/open-source-badges/) [![Gitter Chat](https://badges.gitter.im/frapsoft/frapsoft.svg)](https://gitter.im/frapsoft/frapsoft/)

```
do one thing and do it well - and you don't know all about it!
```

## Resources

- [dealing with problematic dependencies in a restricted network environment](http://blog.npmjs.org/post/145724408060/dealing-with-problematic-dependencies-in-a)

## package.json

This is the most important file where all the configuration happens. That said this is also the place where you can mess things up like accidentaly puplishing private data or something like that. So take 10min and read it carefully before going any further.

<https://docs.npmjs.com/files/package.json>

## npm shortcuts

```
npm i:     install

npm up: update

npm un: uninstall
```

## npm dependency shortcuts

```
-S, --save: Package will appear in your dependencies.

-D, --save-dev: Package will appear in your devDependencies.

-O, --save-optional: Package will appear in your optionalDependencies.
```

<https://docs.npmjs.com/cli/install>

## whitelist files for publish

files

The "files" field is an array of files to include in your project. If you name a folder in the array, then it will also include the files inside that folder. (Unless they would be ignored by another rule.)

You can also provide a ".npmignore" file in the root of your package or in subdirectories, which will keep files from being included, even if they would be picked up by the files array. The .npmignore file works just like a .gitignore.

## os

os

You can specify which operating systems your module will run on:

"os" : [ "darwin", "linux" ] You can also blacklist instead of whitelist operating systems, just prepend the blacklisted os with a '!':

"os" : [ "!win32" ] The host operating system is determined by process.platform

It is allowed to both blacklist, and whitelist, although there isn't any good reason to do this.

## Semantic Versioning

- <http://semver.org/> - Semantic Versioning Explained
- [semver](https://docs.npmjs.com/misc/semver) - semantic versioner for npm
- [node-semver](https://github.com/npm/node-semver) - semver parser for node

## npm scripts

<https://docs.npmjs.com/misc/scripts>

## setting environment variables

<http://blog.npmjs.org/post/118393368555/deploying-with-npm-private-modules>

## setting enviroment variables via scripts

Tip 1: Install [cross-env](https://github.com/kentcdodds/cross-env) to set Cross platform environment via scripts.

Tip 2: `pre`Hooks für scripte setzen

```bash
"prod": "cross-env NODE_ENV=production COMMAND",
"dev": "cross-env NODE_ENV=development COMMAND",
```

## licence

- [license](https://docs.npmjs.com/files/package.json#license) - set a licence in your `package.json`
- [spdx](https://www.npmjs.com/package/spdx) - SPDX License Expression Syntax parser

## no comments in json allowed

```json
// comment not possible
"var": "value" // Unexpected token '/' ...
```

nice workaround:

```json
"//": "damn i am the coolest json comment ever!"
"var": "value"
```

## Semantic Releasing

- [cz-cli](https://github.com/commitizen/cz-cli) - The commitizen command line utility
- [standard-version](https://github.com/conventional-changelog/standard-version) - Replacement for `npm version` with automatic CHANGELOG generation
- [semantic-release](https://github.com/semantic-release/semantic-release) - fully automated package publishing
- [semantic-release-cli](https://github.com/semantic-release/cli) - single command setup

### Semantic Release Setup

`npm install -g semantic-release-cli semantic-release` - Installation

`semantic-release-cli setup` - Setup

Activate debug mode in your `package.json` to prevent publishing to npm or write to disc. In case you want to publish to another branch then master you have to add this to `package.json` as well:

```json
"release": {
    "debug": true,
    "branch": "myfeature"
  }
```

`semantic-release-cli` removes the version from the `package.json` file, to avoid npm warnings add this:

```json
{ "version": "0.0.0-semantic-release" }
```

Badge:

[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

`[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)`

semantic-release creates automatic depending on your changes and commit message a semanti c version. If you want more flexibility and make certain decition on your own the next topic could be your friend.

### Commitizen

`npm install commitizen -g` - Installation

`commitizen init cz-conventional-changelog --save-dev --save-exact` - Setup

Badge:

[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

`[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)`

## Releasing with Standard-Version

`npm i --save-dev standard-version` - Installation as Dev Dependency

`npm i -g standard-version` - or as global Installation

`commitizen init standard-changelog --save-dev --save-exact` - Setup

`"release": "standard-version"` - add run script to `package.json`

`"release": "standard-version --sign"` - if you use GPG for signing add `--sign`

`npm run release --first-release` - first release

`npm run release` - further releases

Badge:

[![Standard Version](https://img.shields.io/badge/release-standard%20version-brightgreen.svg)](https://github.com/conventional-changelog/standard-version)

`[![Standard Version](https://img.shields.io/badge/release-standard%20version-brightgreen.svg)](https://github.com/conventional-changelog/standard-version)`

## Automatic generate a Changelog from git metadata

`npm install --save conventional-changelog`

<https://github.com/conventional-changelog/conventional-changelog-cli>

## Setup the Enviroment Variables

- [GitHub Token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
- [npm Token](http://blog.npmjs.org/post/118393368555/deploying-with-npm-private-modules)

## Continious Integration

- [travis-ci](https://github.com/travis-ci/travis.rb) - Travis CI Client (CLI and Ruby library)
- [travis encrypt secrets](https://docs.travis-ci.com/user/encryption-keys/)
- [travis-repository-settings](https://blog.travis-ci.com/2014-03-05-repository-settings/)

## CLI Apps

link your files to run them directly

`{ "bin" : { "mycli" : "./cli.js" } }`

[preferglobal](https://docs.npmjs.com/files/package.json#preferglobal)

`preferglobal: true`

don't forget to set a shebang

`!/usr/bin/env node`

<https://docs.npmjs.com/files/package.json#bin>

## Production Mode

`npm config set -g production false`

With the --production flag (or when the NODE_ENV environment variable is set to production), npm will not install modules listed in devDependencies.

### Contact / Social Media

_Get the latest News about Web Development, Open Source, Tooling, Server & Security_

[![Twitter](https://github.frapsoft.com/social/twitter.png)](https://twitter.com/frapsoft/)[![Facebook](https://github.frapsoft.com/social/facebook.png)](https://www.facebook.com/frapsoft/)[![Google+](https://github.frapsoft.com/social/google-plus.png)](https://plus.google.com/116540931335841862774)[![Gitter](https://github.frapsoft.com/social/gitter.png)](https://gitter.im/frapsoft/frapsoft/)[![Github](https://github.frapsoft.com/social/github.png)](https://github.com/ellerbrock/)

### Development by

Developer / Author: [Maik Ellerbrock](https://github.com/ellerbrock/)<br>
Company: [Frapsoft](https://github.com/frapsoft/)

### License

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)<br>

This work by [Maik Ellerbrock](https://github.com/ellerbrock/) is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
