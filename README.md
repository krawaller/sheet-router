# sheet-router [![stability][0]][1]
[![npm version][2]][3] [![build status][4]][5] [![test coverage][6]][7]
[![downloads][8]][9] [![js-standard-style][10]][11]

sheet-router is a fast, modular client-side router. It enables view composition
and is tuned for performance by statically declaring routes in a
[radix-trie][12].

## Installation
```sh
$ npm install sheet-router
```

## Features
- View composition through functions
- Tuned for performance by generating a [radix-trie][12]
- Not bound to any framework
- Minimal dependencies and tiny code size

## Usage
```js
const sheetRouter = require('sheet-router')
const h = require('virtual-dom/h')

const router = sheetRouter('/404', function (route) {
  return [
    route('/', (params, h, state) => h('div', 'index path')),
    route('/foo', [
      route('/baz', (params, h, state) => h('div', 'foo path')),
      route('/bar/text', (params, h, state) => h('div', state.text))
    ])
  ]
})

router('/', h, { text: 'hello world' })
```

## API
### router = sheetRouter(dft?, createTree(route))
Create a new router from a nested array. Takes an optional default path as the
first argument.

### router(route, [,...])
Match a route on the router. Takes a path and an arbitrary list of arguments
that are then passed to the matched routes.

## License
[MIT](https://tldrlegal.com/license/mit-license)

[0]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/sheet-router.svg?style=flat-square
[3]: https://npmjs.org/package/sheet-router
[4]: https://img.shields.io/travis/yoshuawuyts/sheet-router/master.svg?style=flat-square
[5]: https://travis-ci.org/yoshuawuyts/sheet-router
[6]: https://img.shields.io/codecov/c/github/yoshuawuyts/sheet-router/master.svg?style=flat-square
[7]: https://codecov.io/github/yoshuawuyts/sheet-router
[8]: http://img.shields.io/npm/dm/sheet-router.svg?style=flat-square
[9]: https://npmjs.org/package/sheet-router
[10]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[11]: https://github.com/feross/standard
[12]: https://github.com/yoshuawuyts/wayfarer
