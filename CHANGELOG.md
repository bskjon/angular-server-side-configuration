# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

### [14.0.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v14.0.0...v14.0.1) (2022-06-04)


### Bug Fixes

* update peer dependencies version range ([04d6f55](https://github.com/kyubisation/angular-server-side-configuration/commit/04d6f55ca276cd4a1007b116f8befe4bf82942c3))

## [14.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v13.2.1...v14.0.0) (2022-06-04)


### ⚠ BREAKING CHANGES

* Update to Angular 14

* update to Angular 14 ([875ce64](https://github.com/kyubisation/angular-server-side-configuration/commit/875ce64e209c1d0dd01ce919d0a883b68d8feeab))

### [13.2.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v13.2.0...v13.2.1) (2022-04-14)

## [13.2.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v13.1.0...v13.2.0) (2022-04-14)


### Features

* add `global` insert variant ([#69](https://github.com/kyubisation/angular-server-side-configuration/issues/69)) ([fe6677a](https://github.com/kyubisation/angular-server-side-configuration/commit/fe6677a3b2b3452711a64f9cdc84861f4279e017))

## [13.1.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v13.0.0...v13.1.0) (2022-02-06)


### Features

* add --nginx flags for native cli command ([#67](https://github.com/kyubisation/angular-server-side-configuration/issues/67)) ([bbcda62](https://github.com/kyubisation/angular-server-side-configuration/commit/bbcda624777f5128466a06e8a1dd3ecd8a1d6d54))
* implement `substitute` command for the native CLI ([#65](https://github.com/kyubisation/angular-server-side-configuration/issues/65)) ([f234c6b](https://github.com/kyubisation/angular-server-side-configuration/commit/f234c6ba099207264663ba379aa9146941d50c0a)), closes [#64](https://github.com/kyubisation/angular-server-side-configuration/issues/64)


### Bug Fixes

* mark process and ng-env imports as having side effects ([#66](https://github.com/kyubisation/angular-server-side-configuration/issues/66)) ([bae19f1](https://github.com/kyubisation/angular-server-side-configuration/commit/bae19f1912aefe27e134b03905a8f6506f1b900c))

## [13.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v12.0.0...v13.0.0) (2021-11-18)


### ⚠ BREAKING CHANGES

* This also refactors the ngsscbuild builder extensively.
This breaking change will only affect you, if you used the internals of this library.
* Switch to Ivy and the new Angular Package Format.

### Features

* enable VariableDetector to also detect index access usages ([702dac3](https://github.com/kyubisation/angular-server-side-configuration/commit/702dac3c0a92dbc113227e49425d761f1b6ca34d))
* implement experimental builders for `build` (browser) and `server` (dev-browser) targets ([5b5c022](https://github.com/kyubisation/angular-server-side-configuration/commit/5b5c022e24f570c8b3f22da7ba4799ecbbe4e565))
* update to Angular 13 ([df5949f](https://github.com/kyubisation/angular-server-side-configuration/commit/df5949f745a3d67dd87a28bb533f6e5ee390df84))


### Bug Fixes

* deprecate NG_ENV variant ([501ee6c](https://github.com/kyubisation/angular-server-side-configuration/commit/501ee6ce4b9aef40821ae38998507b1667a3f12a))

## [12.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v11.0.2...v12.0.0) (2021-05-18)

### ⚠ BREAKING CHANGES

- Updated to support version 12 of Angular

- update to Angular 12 ([e9c7378](https://github.com/kyubisation/angular-server-side-configuration/commit/e9c7378f3f15e56339d1781c0808bf883adf23fe))

### [11.0.2](https://github.com/kyubisation/angular-server-side-configuration/compare/v11.0.1...v11.0.2) (2020-12-03)

### Bug Fixes

- don't use deprecated default options for non aotSupport builds ([e0b431e](https://github.com/kyubisation/angular-server-side-configuration/commit/e0b431ec36ada22fd6f103855850c7c029b21fc1))

### [11.0.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v11.0.0...v11.0.1) (2020-11-16)

## [11.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v10.2.0...v11.0.0) (2020-11-16)

## [10.2.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v10.1.0...v10.2.0) (2020-10-25)

### Features

- update download url of Dockerfiles if available ([368e5eb](https://github.com/kyubisation/angular-server-side-configuration/commit/368e5eba3a6f23ef13ca47ad32c0cc30be8e54f4))

## [10.1.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v10.0.1...v10.1.0) (2020-10-18)

### Features

- add ngsw.json detection and updating to native cli ([1dd77fa](https://github.com/kyubisation/angular-server-side-configuration/commit/1dd77fa943793b6aaa83f34efa87dbc2ef4c4015))

### [10.0.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v10.0.0...v10.0.1) (2020-07-05)

### Bug Fixes

- correct linting ([3ac1181](https://github.com/kyubisation/angular-server-side-configuration/commit/3ac1181c74227b7d99a295f66b5f44995eab26f4))

## [10.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v9.0.2...v10.0.0) (2020-07-05)

### ⚠ BREAKING CHANGES

- Updating to Angular 10.

### Features

- add ngssc binaries for OSX (darwin) ([0561921](https://github.com/kyubisation/angular-server-side-configuration/commit/05619218bf7c748ebfefa94b27d74c9c5fe89a23))

- update to Angular 10 ([2b3e6b7](https://github.com/kyubisation/angular-server-side-configuration/commit/2b3e6b7f49ab4988deac1d8765ab7e394e967e82))

### [9.0.2](https://github.com/kyubisation/angular-server-side-configuration/compare/v9.0.1...v9.0.2) (2020-03-03)

### Bug Fixes

- export schematics factories named ([8c44ff3](https://github.com/kyubisation/angular-server-side-configuration/commit/8c44ff3aadce1764a28a2c53e00d895c81a24fc8))

### [9.0.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v9.0.0...v9.0.1) (2020-03-02)

### Bug Fixes

- export ngsscBuild as a function and builder as default ([dc2ae70](https://github.com/kyubisation/angular-server-side-configuration/commit/dc2ae70397697701ced82fb5aaba467adb0b2c93))

## [9.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v9.0.0-next.0...v9.0.0) (2020-02-07)

## [9.0.0-next.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v8.2.1...v9.0.0-next.0) (2020-02-01)

### Features

- make insert commands idempotent ([3c55e34](https://github.com/kyubisation/angular-server-side-configuration/commit/3c55e34eb210033b976c4a8208023d8ef98580f6))
- upgrade to angular 9-rc ([f948ae5](https://github.com/kyubisation/angular-server-side-configuration/commit/f948ae5d5e5085bda112ffa77f9ee5f43713628d))

### [8.2.1](https://github.com/kyubisation/angular-server-side-configuration/compare/v8.2.0...v8.2.1) (2020-01-23)

### Bug Fixes

- mark new filePattern option as optional ([b43ca20](https://github.com/kyubisation/angular-server-side-configuration/commit/b43ca20ed3db86336e3322fc78085fb70e1723ef))

## [8.2.0](https://github.com/kyubisation/angular-server-side-configuration/compare/v8.1.3...v8.2.0) (2020-01-23)

### Features

- add filePattern option to builder ([e7d51be](https://github.com/kyubisation/angular-server-side-configuration/commit/e7d51be81926dd1d0d9199d06b077b219831b396)), closes [#37](https://github.com/kyubisation/angular-server-side-configuration/issues/37)

### [8.1.3](https://github.com/kyubisation/angular-server-side-configuration/compare/v8.1.2...v8.1.3) (2020-01-20)

### Bug Fixes

- tokenizer should not short circuit ([d849f6c](https://github.com/kyubisation/angular-server-side-configuration/commit/d849f6cb5b9575fbf85e7daae084957f8b4433e5)), closes [#38](https://github.com/kyubisation/angular-server-side-configuration/issues/38)

### [8.1.2](https://github.com/kyubisation/angular-server-side-configuration/compare/v8.1.1...v8.1.2) (2020-01-12)

### Bug Fixes

- bump handlebars from 4.1.2 to 4.5.3 ([#35](https://github.com/kyubisation/angular-server-side-configuration/issues/35)) ([de53338](https://github.com/kyubisation/angular-server-side-configuration/commit/de533381723afd94f18f1a9decf3e93c6d566600))

### [8.1.1](https://github.com/kyubisation/angular-server-side-configuration/compare/8.1.0...8.1.1) (2019-10-23)

### Refactor

- No longer changing working directory in the cli

### [8.1.0](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0...8.1.0) (2019-10-23)

### Features

- Add uncompressed binaries

### [8.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0-beta.4...8.0.0) (2019-08-25)

### Bugfix

- Fixed issue with native cli --recursive

### [8.0.0-beta.4](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0-beta.3...8.0.0-beta.4) (2019-07-19)

### Bugfix

- Fixed iife insertion

### [8.0.0-beta.3](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0-beta.2...8.0.0-beta.3) (2019-07-19)

### Bugfix

- Fixed dependency issue with glob-to-regexp

### [8.0.0-beta.2](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0-beta.1...8.0.0-beta.2) (2019-07-19)

### Features

- Implemented insert function (`import { insert } from 'angular-server-side-configuration';`)

### Bugfix

- Fixed issue in native cli

### [8.0.0-beta.1](https://github.com/kyubisation/angular-server-side-configuration/compare/8.0.0-beta.0...8.0.0-beta.1) (2019-07-14)

### Features

- Added additionalEnvironmentVariables to builder options
- Implemented ng update migration

### [8.0.0-beta.0](https://github.com/kyubisation/angular-server-side-configuration/compare/2.0.0...8.0.0-beta.0) (2019-06-30)

### Features

- Rewrote the library to use Angular schematics and builders
- Added --recursive flag to the native CLI

### Breaking Changes

- Removed the npm CLI and most of the existing internal implementation
- Dropped support for configuration embedded in html

### [2.0.0](https://github.com/kyubisation/angular-server-side-configuration/compare/2.0.0-beta.1...2.0.0) (2019-04-14)

### Features

- Added documentation for the native cli

### [2.0.0-beta.1](https://github.com/kyubisation/angular-server-side-configuration/compare/2.0.0-beta.0...2.0.0-beta.1) (2019-04-13)

The detection and insertion of environment variables has been separated.
Detection is now executed at build time by wrapping the ng build command (e.g. `ngssc ng build`).
This will generate an ngssc.json file, which can be used by the `ngssc insert` command.
See the README for more information.

### Features

- New command `ngssc` for detecting environment variable usage

### Breaking Changes

- The `ngssc wrap-aot` has been merged into the `ngssc` command as an optional flag `--wrap-aot`.
- The `ngssc insert` command requires an ngssc.json file or embedded configuration in the html files.

### [2.0.0-beta.0](https://github.com/kyubisation/angular-server-side-configuration/compare/1.3.0...2.0.0-beta.0) (2019-03-10)

### Features

- Implemented NG_ENV variant as an alternative for process.env

### Breaking Changes

- Removed deprecated ProcessEnvConfiguration

### [1.3.0](https://github.com/kyubisation/angular-server-side-configuration/compare/1.2.1...1.3.0) (2019-03-09)

### Features

- Created ProcessEnvConfiguration, which will replace EnvironmentVariablesConfiguration
- Created class Configuration, which is the base implementation for ProcessEnvConfiguration and EnvironmentVariablesConfiguration

### Deprecation

- EnvironmentVariablesConfiguration has been deprecated. Use ProcessEnvConfiguration instead

### Internal Changes

- Switched testing framework from mocha/chai/nyc to jest
