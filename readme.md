# remark-defsplit

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Chat][chat-badge]][chat]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]

Change links and images to be references with separate definitions with
[**remark**][remark].

## Installation

[npm][]:

```sh
npm install remark-defsplit
```

## Usage

Say we have the following file, `example.md`.

```markdown
[![Build Status](https://travis-ci.org/remarkjs/remark-defsplit.svg?branch=master)](https://travis-ci.org/remarkjs/remark-defsplit)
```

And our script, `example.js`, looks as follows:

```js
var vfile = require('to-vfile')
var remark = require('remark')
var defsplit = require('remark-defsplit')

remark()
  .use(defsplit, {id: ['travis-badge', 'travis']})
  .process(vfile.readSync('example.md'), function(err, file) {
    if (err) throw err
    console.log(String(file))
  })
```

Now, running `node example` yields:

```markdown
[![Build Status][travis-badge]][travis]

[travis-badge]: https://travis-ci.org/remarkjs/remark-defsplit.svg?branch=master

[travis]: https://travis-ci.org/remarkjs/remark-defsplit
```

## API

### `remark().use(defsplit[, options])`

Transform the tree to replaces links and images with references and definitions.

###### `options.id`

Identifiers to use for new definitions instead of autogenerated ones (`string`
or `Array.<String>`, default: `[]`).

## Related

*   [`remark-reference-links`][remark-reference-links]
    — Practically the same as `remark-defsplit`, but with numeric identifiers
    instead of URI-based ones
*   [`remark-inline-links`][remark-inline-links]
    — Reverse, thus rewriting references and definitions into links and images

## Contribute

See [`contributing.md` in `remarkjs/remark`][contributing] for ways to get
started.

This organisation has a [Code of Conduct][coc].  By interacting with this
repository, organisation, or community you agree to abide by its terms.

## License

[MIT][license] © Eugene Sharygin

[build-badge]: https://img.shields.io/travis/remarkjs/remark-defsplit.svg

[build]: https://travis-ci.org/remarkjs/remark-defsplit

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-defsplit.svg

[coverage]: https://codecov.io/github/remarkjs/remark-defsplit

[downloads-badge]: https://img.shields.io/npm/dm/remark-defsplit.svg

[downloads]: https://www.npmjs.com/package/remark-defsplit

[chat-badge]: https://img.shields.io/badge/join%20the%20community-on%20spectrum-7b16ff.svg

[chat]: https://spectrum.chat/unified/remark

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[license]: license

[npm]: https://docs.npmjs.com/cli/install

[contributing]: https://github.com/remarkjs/remark/blob/master/contributing.md

[coc]: https://github.com/remarkjs/remark/blob/master/code-of-conduct.md

[remark]: https://github.com/remarkjs/remark

[remark-reference-links]: https://github.com/remarkjs/remark-reference-links

[remark-inline-links]: https://github.com/remarkjs/remark-inline-links
