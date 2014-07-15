grunt-tt2-bem
=============

> Template Toolkit 2 to BEM bridge.

[![Build Status](https://travis-ci.org/Wu-Wu/grunt-tt2-bem.svg?branch=master)](https://travis-ci.org/Wu-Wu/grunt-tt2-bem)
[![Coverage Status](https://img.shields.io/coveralls/Wu-Wu/grunt-tt2-bem.svg)](https://coveralls.io/r/Wu-Wu/grunt-tt2-bem?branch=master)
[![Dependency Status](https://david-dm.org/Wu-Wu/grunt-tt2-bem.svg)](https://david-dm.org/Wu-Wu/grunt-tt2-bem)
[![NPM version](https://badge.fury.io/js/grunt-tt2-bem.svg)](http://badge.fury.io/js/grunt-tt2-bem)

## Getting Started

This plugin requires Grunt ~0.4.1

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-tt2-bem --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-tt2-bem');
```

## The "bemdecl" task

TODO

### Overview

In your project's Gruntfile, add a section named `bemdecl` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
    bemdecl: {
        someTarget: {
            options: {
                // Target-specific options go here.
                root: 'path/to/root',
                includes: [ 'includes', 'inc' ]    // relative to $root
            },
            src: [ 'templates/**/*.html' ],
            dest: 'bem/bundles.generated'
        }
    }
})
```

Each target defines a specific task that can be run.

### Options

#### options.root

Type: `String`
Default: `Gruntfile.* directory`

Templates root directory.

#### options.includes

Type: `Array`
Default: `[ '.' ]` (root directory)

List of directories contains include files.

#### options.prefixes

Type: `Array`
Default: `[ 'b', 'i', 'l' ]`

Valid BEM prefixes.

> Will catch all BEM-blocks started with (like `b-foo__bar`, `i-rel`) and skip others (like `d-quux__foo`).

#### options.allowed

Type: `Array`
Default: `[ ]`

Allowed BEM-blocks. Not allowed blocks will be filtered out from `*.bemdecl.js` files.

> An empty list means that all BEM-blocks considered valid.

#### options.extSrc

Type: `String`
Default: `.html`

Source files (templates) extension.

#### options.extDst

Type: `String`
Default: `.bemdecl.js`

Destination files (declarations) extension.

#### options.sep

Type: `String`
Default: `-`

Separator for flattened files and directories.

>Suppose we have source template called `choose/domain/index.html` the bemdecl file for it would be like `choose-domain-index.bemdecl.js`. So path parts will be joined with `options.sep` value.

#### options.cut

Type: `Number`
Default: `0`

The numbers of levels in source file path which should be skipped.

>Used to get flatten path for a template. For the `templates/choose/domain/index.html` and value of `1` the part `templates/` would be skipped.

#### options.indentSize

Type: `Number`
Default: `4`

The indentation levels for bemdecl structure.

### Usage Example

TODO

### Source (templates) and destination (declarations) files

Source and destination files should be pointed through the `src` and `dest` properties respectively.
Both propereties are required to work the plugin. The `dest` accepts only `String` value, the `src` accepts `String`, `Array` or `Object`.

As `String`

```js
bemdecl: {
    all: {
        options: { },
        src: 'templates/**/*.html',
        dest: 'bem/bundles.generated'
    }
}
```

As `Array`

```js
bemdecl: {
    all: {
        options: { },
        src: [ 'templates/**/*.html' ],
        dest: 'bem/bundles.generated'
    }
}
```

As `Object`. All values are plain `String` or `Array`. Duplicates and undefined members will be filtered.

```js
bemdecl: {
    all: {
        options: { },
        src: {
            foo: [
                'templates/foo/*.html',
                'templates/bar/*.html'
            ],
            qux: 'templates/qux/**/*.html'
        },
        dest: 'bem/bundles.generated'
    }
}
```

## Release History

### v0.1.1
  - Initial release

## License
_grunt-tt2-bem_ is licensed under the [MIT license][].

[MIT license]: http://www.tldrlegal.com/license/mit-license
