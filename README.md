# es-aggregate-error <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![Build Status][travis-svg]][travis-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES Proposal spec-compliant shim for AggregateError. Invoke its "shim" method to shim `AggregateError` if it is unavailable or noncompliant.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment, and complies with the [proposed spec](https://tc39.es/proposal-promise-any/#sec-aggregate-error-object-structure).

Most common usage:
```js
var assert = require('assert');
var AggregateError = require('es-aggregate-error');

var oneError = new RangeError('hi!');
var otherError = new EvalError('oops');
var error = new AggregateError([oneError, otherError], 'this is two kinds of errors');

assert.deepEqual(error.errors, [oneError, otherError]);
assert.equal(error.message, 'this is two kinds of errors');

AggregateError.shim(); // will be a no-op if not needed

assert.equal(globalThis.AggregateError, AggregateError);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/es-aggregate-error
[npm-version-svg]: http://versionbadg.es/es-shims/AggregateError.svg
[travis-svg]: https://travis-ci.org/es-shims/AggregateError.svg
[travis-url]: https://travis-ci.org/es-shims/AggregateError
[deps-svg]: https://david-dm.org/es-shims/AggregateError.svg
[deps-url]: https://david-dm.org/es-shims/AggregateError
[dev-deps-svg]: https://david-dm.org/es-shims/AggregateError/dev-status.svg
[dev-deps-url]: https://david-dm.org/es-shims/AggregateError#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/es-aggregate-error.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/es-aggregate-error.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/es-aggregate-error.svg
[downloads-url]: http://npm-stat.com/charts.html?package=es-aggregate-error
