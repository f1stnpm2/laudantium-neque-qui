# @f1stnpm2/laudantium-neque-qui <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `String.prototype.at` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-item-method/).

Because `String.prototype.at` depends on a receiver (the `this` value), the main export takes the string to operate on as the first argument.

Note that versions of this package before v1.0.0 reflect an earlier, now-inactive proposal (https://github.com/mathiasbynens/String.prototype.at).

## Getting started

```sh
npm install --save @f1stnpm2/laudantium-neque-qui
```

## Usage/Examples

```js
var at = require('@f1stnpm2/laudantium-neque-qui');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = at(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var at = require('@f1stnpm2/laudantium-neque-qui');
var assert = require('assert');
/* when String#at is not present */
delete String.prototype.at;
var shimmedFlatMap = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, at.getPolyfill());
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

```js
var at = require('@f1stnpm2/laudantium-neque-qui');
var assert = require('assert');
/* when String#at is present */
var shimmedIncludes = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, String.prototype.at);
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@f1stnpm2/laudantium-neque-qui
[npm-version-svg]: https://versionbadg.es/f1stnpm2/laudantium-neque-qui.svg
[deps-svg]: https://david-dm.org/f1stnpm2/laudantium-neque-qui.svg
[deps-url]: https://david-dm.org/f1stnpm2/laudantium-neque-qui
[dev-deps-svg]: https://david-dm.org/f1stnpm2/laudantium-neque-qui/dev-status.svg
[dev-deps-url]: https://david-dm.org/f1stnpm2/laudantium-neque-qui#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@f1stnpm2/laudantium-neque-qui.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@f1stnpm2/laudantium-neque-qui.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@f1stnpm2/laudantium-neque-qui.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@f1stnpm2/laudantium-neque-qui
[codecov-image]: https://codecov.io/gh/f1stnpm2/laudantium-neque-qui/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/f1stnpm2/laudantium-neque-qui/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/f1stnpm2/laudantium-neque-qui
[actions-url]: https://github.com/f1stnpm2/laudantium-neque-qui/actions
