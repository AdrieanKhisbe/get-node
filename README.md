[![Codecov](https://img.shields.io/codecov/c/github/ehmicky/get-node.svg?label=tested&logo=codecov)](https://codecov.io/gh/ehmicky/get-node)
[![Travis](https://img.shields.io/badge/cross-platform-4cc61e.svg?logo=travis)](https://travis-ci.org/ehmicky/get-node)
[![Gitter](https://img.shields.io/gitter/room/ehmicky/get-node.svg?logo=gitter)](https://gitter.im/ehmicky/get-node)
[![Twitter](https://img.shields.io/badge/%E2%80%8B-twitter-4cc61e.svg?logo=twitter)](https://twitter.com/intent/follow?screen_name=ehmicky)
[![Medium](https://img.shields.io/badge/%E2%80%8B-medium-4cc61e.svg?logo=medium)](https://medium.com/@ehmicky)

Download a specific version of Node.js.

The Node.js release is downloaded, uncompressed and untared to an executable
file ready to run.

Fast:

- the download is cached
- the best compression algorithm available on your machine is used
- everything is streamed

Reliable:

- the binary is checked against
  [official checksums](https://github.com/nodejs/node#verifying-binaries)
- can be safely run concurrently
- atomic writes

Features include:

- Linux/Mac/Windows support
- works with old Node.js versions
- [progress bar](#progress)
- using [version ranges](#getnodeversion-options)
- specifying [a mirror website](#mirror) for nodejs.org
- helpful error messages

# Example

<!-- Remove 'eslint-skip' once estree supports top-level await -->
<!-- eslint-skip -->

```js
const getNode = require('get-node')

// Download a specific Node.js release
const { path, version } = await getNode('8')
console.log(path) // /home/user/.cache/nve/8.16.2/node
console.log(version) // 8.16.2

// Download Node.js latest release
const { path, version } = await getNode('*')
console.log(path) // /home/user/.cache/nve/13.0.1/node
console.log(version) // 13.0.1

// Any version range can be used
await getNode('8.12.0')
await getNode('<7')

// Specify the output directory
const { path } = await getNode('8', {
  output: '/home/user/.cache/node_releases/',
})
console.log(path) // /home/user/.cache/node_releases/13.0.1/node

// Use a mirror website
await getNode('8', { mirror: 'https://npm.taobao.org/mirrors/node' })
```

# Install

```bash
npm install get-node
```

`node >=8.12.0` must be globally installed. However any Node version can be
downloaded.

To use this module as a CLI instead, please check
[`get-node-cli`](https://github.com/ehmicky/get-node-cli).

# Usage

## getNode(version, options?)

`version`: `string`\
`options`: `object?`\
_Return value_: `Promise<object>`

`version` can be any [version range](https://github.com/npm/node-semver) such as
`12`, `12.6.0` or `<12`.

### Options

#### output

_Type_: `string`\
_Default_: [global cache directory](https://github.com/ehmicky/global-cache-dir)
such as `/home/user/.cache/nve/`.

Output directory for the `node` executable.

It the directory already has a `node` executable, no download is performed. This
enables caching.

#### progress

_Type_: `boolean` _Default_: `false`

Whether to show a progress bar.

#### mirror

_Type_: `string`\
_Default_: `https://nodejs.org/dist`

Base URL. Can be overridden (for example `https://npm.taobao.org/mirrors/node`).

The following environment variables can also be used: `NODE_MIRROR`,
`NVM_NODEJS_ORG_MIRROR`, `N_NODE_MIRROR` or `NODIST_NODE_MIRROR`.

### Return value

The returned `Promise` resolves to an object with the following properties.

#### path

_Type_: `string`

Absolute path to the `node` executable.

#### version

_Type_: `string`

[Normalized](https://github.com/ehmicky/normalize-node-version) Node.js version.

# See also

- [`get-node-cli`](https://github.com/ehmicky/get-node-cli): `get-node` as a CLI
- [`nve`](https://github.com/ehmicky/nve): Run a specific Node.js version (CLI)
- [`nvexeca`](https://github.com/ehmicky/nve): Run a specific Node.js version
  (programmatic)
- [`normalize-node-version`](https://github.com/ehmicky/normalize-node-version):
  Normalize and validate Node.js versions
- [`all-node-versions`](https://github.com/ehmicky/all-node-versions): List all
  available Node.js versions
- [`fetch-node-website`](https://github.com/ehmicky/fetch-node-website): Fetch
  releases on nodejs.org
- [`global-cache-dir`](https://github.com/ehmicky/global-cache-dir): Get the
  global cache directory

# Support

If you found a bug or would like a new feature, _don't hesitate_ to
[submit an issue on GitHub](../../issues).

For other questions, feel free to
[chat with us on Gitter](https://gitter.im/ehmicky/get-node).

Everyone is welcome regardless of personal background. We enforce a
[Code of conduct](CODE_OF_CONDUCT.md) in order to promote a positive and
inclusive environment.

# Contributing

This project was made with ❤️. The simplest way to give back is by starring and
sharing it online.

If the documentation is unclear or has a typo, please click on the page's `Edit`
button (pencil icon) and suggest a correction.

If you would like to help us fix a bug or add a new feature, please check our
[guidelines](CONTRIBUTING.md). Pull requests are welcome!

Thanks go to our wonderful contributors:

<!-- ALL-CONTRIBUTORS-LIST:START -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://twitter.com/ehmicky"><img src="https://avatars2.githubusercontent.com/u/8136211?v=4" width="100px;" alt="ehmicky"/><br /><sub><b>ehmicky</b></sub></a><br /><a href="https://github.com/ehmicky/get-node/commits?author=ehmicky" title="Code">💻</a> <a href="#design-ehmicky" title="Design">🎨</a> <a href="#ideas-ehmicky" title="Ideas, Planning, & Feedback">🤔</a> <a href="https://github.com/ehmicky/get-node/commits?author=ehmicky" title="Documentation">📖</a></td>
    <td align="center"><a href="https://tunnckoCore.com"><img src="https://avatars3.githubusercontent.com/u/5038030?v=4" width="100px;" alt="Charlike Mike Reagent"/><br /><sub><b>Charlike Mike Reagent</b></sub></a><br /><a href="https://github.com/ehmicky/get-node/issues?q=author%3AtunnckoCore" title="Bug reports">🐛</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
