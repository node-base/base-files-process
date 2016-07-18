# base-files-process [![NPM version](https://img.shields.io/npm/v/base-files-process.svg?style=flat)](https://www.npmjs.com/package/base-files-process) [![NPM downloads](https://img.shields.io/npm/dm/base-files-process.svg?style=flat)](https://npmjs.org/package/base-files-process) [![Build Status](https://img.shields.io/travis/node-base/base-files-process.svg?style=flat)](https://travis-ci.org/node-base/base-files-process)

Plugin for processing files from a declarative configuration.

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [Example](#example)
- [API](#api)
- [History](#history)
  * [v0.2.0 - 2016-07-18](#v020---2016-07-18)
- [About](#about)
  * [Related projects](#related-projects)
  * [Contributing](#contributing)
  * [Building docs](#building-docs)
  * [Running tests](#running-tests)
  * [Author](#author)
  * [License](#license)

_(TOC generated by [verb](https://github.com/verbose/verb) using [markdown-toc](https://github.com/jonschlinkert/markdown-toc))_

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save base-files-process
```

## Usage

```js
var files = require('base-files-process');
```

## Example

```js
var Base = require('base-app');
var expand = require('expand-files');
var pipeline = require('base-pipeline');
var files = require('base-files-process');
var app = new Base();

app.use(pipeline());
app.use(files());

// register pipeline plugins using the `.plugin` method
app.plugin('foo', function(options) {
  return through.obj(function(file, enc, next) {
    // do plugin stuff
    next(null, file);
  });
});

// use `expand-files` to expand a declarative configuration object
var config = expand({
  cwd: fixtures,
  src: '*.txt',
  dest: actual
});

// pass the config object to `.processFiles()`
app.processFiles(config)
  .on('end', function() {
    console.log('done!');
  });
```

## API

### [.processFiles](index.js#L48)

Process an array of `files` objects, where each object has a `src` and `dest` property.

**Params**

* `files` **{Array}**
* `options` **{Object}**
* `returns` **{Stream}**

**Example**

```js
var expand = require('expand-files');
var config = expand({
  cwd: fixtures,
  src: 'b.txt',
  dest: actual
});

app.processFiles(config)
  .on('error', console.log)
  .on('end', console.log);
```

## History

### v0.2.0 - 2016-07-18

**Breaking changes**

* renamed the `.process` method to `.processFiles`

## About

### Related projects

* [base-fs](https://www.npmjs.com/package/base-fs): base-methods plugin that adds vinyl-fs methods to your 'base' application for working with the file… [more](https://github.com/node-base/base-fs) | [homepage](https://github.com/node-base/base-fs "base-methods plugin that adds vinyl-fs methods to your 'base' application for working with the file system, like src, dest, copy and symlink.")
* [base-pipeline](https://www.npmjs.com/package/base-pipeline): base-methods plugin that adds pipeline and plugin methods for dynamically composing streaming plugin pipelines. | [homepage](https://github.com/node-base/base-pipeline "base-methods plugin that adds pipeline and plugin methods for dynamically composing streaming plugin pipelines.")
* [base-task](https://www.npmjs.com/package/base-task): base plugin that provides a very thin wrapper around [https://github.com/doowb/composer](https://github.com/doowb/composer) for adding task methods to… [more](https://github.com/node-base/base-task) | [homepage](https://github.com/node-base/base-task "base plugin that provides a very thin wrapper around <https://github.com/doowb/composer> for adding task methods to your application.")
* [base](https://www.npmjs.com/package/base): base is the foundation for creating modular, unit testable and highly pluggable node.js applications, starting… [more](https://github.com/node-base/base) | [homepage](https://github.com/node-base/base "base is the foundation for creating modular, unit testable and highly pluggable node.js applications, starting with a handful of common methods, like `set`, `get`, `del` and `use`.")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

### Building docs

_(This document was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme) (a [verb](https://github.com/verbose/verb) generator), please don't edit the readme directly. Any changes to the readme must be made in [.verb.md](.verb.md).)_

To generate the readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install -g verb verb-generate-readme && verb
```

### Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

### License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/node-base/base-files-process/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on July 18, 2016._