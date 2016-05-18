> New Generation Build System

<div align="center">
  <a href="https://github.com/Bj/fly">
    <img width=280px src="https://cloud.githubusercontent.com/assets/8317250/8733685/0be81080-2c40-11e5-98d2-c634f076ccd7.png">
  </a>
</div>
<br>

<p align="center"><big>

</big></p>

<p align="center">
  <a href="https://npmjs.org/package/fly">
    <img src="https://img.shields.io/npm/v/fly.svg?style=flat-square"
         alt="NPM Version">
  </a>

  <a href="https://coveralls.io/r/flyjs/fly">
    <img src="https://img.shields.io/coveralls/flyjs/fly.svg?style=flat-square"
         alt="Coverage Status">
  </a>

  <a href="https://travis-ci.org/Bj/fly">
    <img src="https://img.shields.io/travis/Bj/fly.svg?style=flat-square"
         alt="Build Status">
  </a>

  <a href="https://npmjs.org/package/fly">
    <img src="http://img.shields.io/npm/dm/fly.svg?style=flat-square"
         alt="Downloads">
  </a>

  <a href="https://david-dm.org/Bj/fly">
    <img src="https://david-dm.org/Bj/fly.svg?style=flat-square"
         alt="Dependency Status">
  </a>

  <a href="https://github.com/Bj/fly/blob/master/LICENSE">
    <img src="https://img.shields.io/npm/l/fly.svg?style=flat-square"
         alt="License">
  </a>

  <a href="https://gitter.im/Bj/fly">
    <img src="https://img.shields.io/badge/gitter-join-FF2B6E.svg?style=flat-square"
         alt="Gitt">
  </a>
</p>

<p align="center">
  <b><a href="#about">About</a></b>
  |
  <b><a href="#usage">Usage</a></b>
  |
  <b><a href="/docs/README.md">Documentation</a></b>
  |
  <b><a href="https://github.com/Bj/fly/wiki#plugins">Plugins</a></b>
  |
  <b><a href="#contributing">Contributing</a></b>

</p>

<br>

## About

_Fly_ is a modern [build system](https://en.wikipedia.org/wiki/Build_automation) for [Node](https://nodejs.org/) based in [_co_-routines](https://medium.com/@tjholowaychuk/callbacks-vs-coroutines-174f1fe66127), [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) and [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).

_Fly_ has [callback _heaven_](http://jakearchibald.com/2014/es7-async-functions/), [concurrent tasks](https://github.com/flyjs/fly/blob/master/docs/README.md#features), [robust error handling](https://medium.com/@tjholowaychuk/callbacks-vs-coroutines-174f1fe66127), [cascading tasks](https://github.com/flyjs/fly/blob/master/CHANGELOG.md#cascading-tasks) and a simple [API](https://github.com/flyjs/fly/blob/master/docs/README.md#api).

See the [documentation](/docs/README.md) to learn more about Fly.

## Install

```
npm install fly
```

## `flyfile.js` Samples

### ES5

Out of the box, a `flyfile.js` should be written in native ES5:

```js
var x = module.exports
var paths = {
  scripts: ['src/**/*.js', '!src/ignore/**/*.js']
}

x.default = function * () {
  yield this.watch(paths.scripts, 'build')
}

x.build = function * () {
  yield this.source(paths.scripts)
    .eslint({
      rules: {'no-extra-semi': 0}
    })

  yield this.source(paths.scripts)
    .babel({
      presets: ['es2015', 'stage-0']
    })
    .concat('app.js')
    .target('dist')
}
```

### ES2015 and ES7 Support

If you'd prefer to write your [`flyfile.js`](https://github.com/Bj/fly/blob/master/docs/README.md#flyfiles) and [plugins](https://github.com/Bj/fly/blob/master/docs/README.md#plugins) with ES6 or ES7 syntax, all you have to do is download [fly-esnext](https://github.com/lukeed/fly-esnext)! Seriously. :)

```
npm i -D fly-esnext
```

```js
const paths = {
  scripts: ['src/**/*.js', '!src/ignore/**/*.js']
}

export default async function () {
  await this.watch(paths.scripts, 'build')
}

export async function build() {
  await this.source(paths.scripts)
    .eslint({
      rules: {'no-extra-semi': 0}
    })

  await this.source(paths.scripts)
    .babel({
      presets: ['es2015', 'stage-0']
    })
    .concat('app.js')
    .target('dist')
}
```

# Contributing

Contributions are _absolutely_ welcome. Check out our [contribution guide](/CONTRIBUTING.md).

<!-- -->

[author]:         http://github.com/Bj
[contributors]:   https://github.com/Bj/fly/graphs/contributors

[fly]:            https://www.github.com/Bj/fly

[npm-pkg-link]:   https://www.npmjs.org/package/fly
[npm-ver-link]:   https://img.shields.io/npm/v/fly.svg?style=flat-square

[dl-badge]:       http://img.shields.io/npm/dm/fly.svg?style=flat-square

[travis-badge]:   http://img.shields.io/travis/Bj/fly.svg?style=flat-square
[travis-link]:    https://travis-ci.org/Bj/fly

[mit-badge]:      https://img.shields.io/badge/license-MIT-444444.svg?style=flat-square

[es6-example]:    https://github.com/Bj/fly/blob/master/examples/babel/flyfile.js
[es7-example]:    https://github.com/Bj/fly/blob/master/examples/async/flyfile.js
