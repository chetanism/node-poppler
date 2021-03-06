# node-poppler

[![GitHub Release](https://img.shields.io/github/release/Fdawgs/node-poppler.svg)](https://github.com/Fdawgs/node-poppler/releases/latest/) [![npm version](https://img.shields.io/npm/v/node-poppler)](https://www.npmjs.com/package/node-poppler)
[![Build Status](https://travis-ci.org/Fdawgs/node-poppler.svg?branch=master)](https://travis-ci.org/Fdawgs/node-poppler) [![Coverage Status](https://coveralls.io/repos/github/Fdawgs/node-poppler/badge.svg?branch=master)](https://coveralls.io/github/Fdawgs/node-poppler?branch=master) [![Dependabot Status](https://api.dependabot.com/badges/status?host=github&identifier=214626138)](https://dependabot.com) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

> Promise-based node.js wrapper for the Poppler PDF rendering library

## Intro

The node-poppler module was created out of a need for a PDF-to-HTML conversion module at [Yeovil District Hospital NHSFT](https://yeovilhospital.co.uk/) to convert clinical documents in PDF format to HTML.

## Installation

Install using [`yarn`](https://yarnpkg.com/en/package/node-poppler):

```bash
yarn add node-poppler
```

Or [`npm`](https://www.npmjs.com/package/node-poppler):

```bash
npm install node-poppler
```

node-poppler's test scripts use yarn commands.

### Linux support

Windows and OSX/Darwin binaries are provided with this repository.
For Linux users, you will need to download the `poppler-data` and `poppler-utils` binaries seperately.

An example of downloading the binaries on a Debian system:

```
sudo apt-get install poppler-data
sudo apt-get install poppler-utils
```

Once they have been installed you will need to pass the `poppler-utils` installation directory in as parameters to an instance of the Poppler class:

```js
const { Poppler } = require('node-poppler');
const poppler = new Poppler('./usr/bin');
```

## API

```js
const { Poppler } = require('node-poppler');
```

[API Documentation can be found here](https://github.com/Fdawgs/node-poppler/blob/master/API.md)

## Examples

### poppler.pdfToCairo

`options` object requires atleast one of the following to be set: `jpegFile`; `pdfFile`; `pngFile`; `psFile`; `svgFile`; `tiffFile`.

Example of calling poppler.pdfToCairo with a promise, to convert only the first and second page of a PDF file to PNG:

```js
const { Poppler } = require('node-poppler');

const file = 'test_document.pdf';
const poppler = new Poppler();
const options = {
	firstPageToConvert: 1,
	lastPageToConvert: 2,
	pngFile: true
};

await poppler.pdfToCairo(options, file).then((res) => {
	console.log(res);
});
```

### poppler.pdfToHtml

Every field of the `options` object is entirely optional.

Example of calling poppler.pdfToHtml with a promise:

```js
const { Poppler } = require('node-poppler');

const file = 'test_document.pdf';
const poppler = new Poppler();
const options = {
	firstPageToConvert: 1,
	lastPageToConvert: 2
};

await poppler.pdfToHtml(options, file).then((res) => {
	console.log(res);
});
```

### poppler.pdfToText

Every field of the `options` object is entirely optional.

Example of calling poppler.pdfToText with a promise:

```js
const { Poppler } = require('node-poppler');

const file = 'test_document.pdf';
const poppler = new Poppler();
const options = {
	firstPageToConvert: 1,
	lastPageToConvert: 2
};

await poppler.pdfToText(options, file).then((res) => {
	console.log(res);
});
```

## Contributing

Please see [CONTRIBUTING.md](https://github.com/Fdawgs/node-poppler/blob/master/CONTRIBUTING.md) for more details regarding contributing to this project.

## License

`node-poppler` is licensed under the [MIT](https://github.com/Fdawgs/node-poppler/blob/master/LICENSE) license.
