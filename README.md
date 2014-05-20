# grunt-ks-stylus v0.0.4 

[![NPM version](http://img.shields.io/npm/v/grunt-ks-stylus.svg)](https://www.npmjs.org/package/grunt-ks-stylus) [![Build Status](http://img.shields.io/travis/leny/grunt-ks-stylus.svg)](https://travis-ci.org/leny/grunt-ks-stylus) ![Dependency Status](https://david-dm.org/leny/grunt-ks-stylus.svg) ![Downloads counter](http://img.shields.io/npm/dm/grunt-ks-stylus.svg)

> Compile Stylus (with Kouto Swiss framework) files to CSS.

## Note

This grunt task is forked (and will be rebased when source updates) from [grunt-contrib-stylus](https://www.npmjs.org/package/grunt-contrib-stylus).  
The only difference is the inclusion of [Kouto Swiss](https://www.npmjs.org/package/kouto-swiss)' framework in the path.

When Kouto Swiss will be officialy released, and gain some users, I will proposed a pull request to the original grunt task.

**grunt-contrib-stylus** base version for the fork : `0.15.1`.  
**stylus** version included : `0.45.1`.  
**kouto-swiss** version included : `0.1.2`.  
**nib** version included : `1.0.2`.

## Getting Started
This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-contrib-stylus --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-contrib-stylus');
```

*This plugin was designed to work with Grunt 0.4.x. If you're still using grunt v0.3.x it's strongly recommended that [you upgrade](http://gruntjs.com/upgrading-from-0.3-to-0.4), but in case you can't please use [v0.3.1](https://github.com/gruntjs/grunt-contrib-stylus/tree/grunt-0.3-stable).*

## Stylus task
_Run this task with the `grunt stylus` command._

Task targets, files and options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.

This task comes preloaded with [nib](http://visionmedia.github.com/nib/) and [Kouto Swiss](https://www.npmjs.org/package/kouto-swiss).

### Options

#### compress
Type: `Boolean`  
Default: `true`

Specifies if we should compress the compiled css. Compression is always disabled when `--debug` flag is passed to grunt.

#### linenos
Type: `Boolean`  
Default: `false`

Specifies if the generated CSS file should contain comments indicating the corresponding stylus line.

#### firebug
Type: `Boolean`  
Default: `false`

Specifies if the generated CSS file should contain debug info that can be used by the FireStylus Firebug plugin

#### paths
Type: `Array`

Specifies directories to scan for @import directives when parsing.

#### define
Type: `Object`

Allows you to define global variables in Gruntfile that will be accessible in Stylus files.

#### rawDefine
Type: `Boolean|Array|String`

If set to "true", defines global variables in Gruntfile without casting objects to Stylus lists. Allows using a JavaScript object in Gruntfile to be accessible as a Stylus Hash. See Stylus's issue tracker for details. [LearnBoost/stylus#1286](https://github.com/LearnBoost/stylus/issues/1286)

Allows passing an array or string to specify individual keys to define "raw", casting all other keys as default Stylus behavior.

#### urlfunc
Type: `String|Object`

If `String`: specifies function name that should be used for embedding images as Data URI.

If `Object`:
* `name` - Type: `String`. Function name that should be used for embedding images as Data URI.
* [ `limit` ] - Type: `Number|Boolean` Default: `30000`. Bytesize limit defaulting to 30Kb (30000), use false to disable the limit.
* [ `[paths` ] - Type: `Array`, Default: `[]`. Image resolution path(s).

See [url()](http://learnboost.github.io/stylus/docs/functions.url.html) for details.

#### [use](https://github.com/LearnBoost/stylus/blob/master/docs/js.md#usefn)
Type: `Array`

Allows passing of stylus plugins to be used during compile.

#### [import](https://github.com/LearnBoost/stylus/blob/master/docs/js.md#importpath)
Type: `Array`

Import given stylus packages into every compiled `.styl` file, as if you wrote `@import '...'`
in every single one of said files.

#### include css
Type: `Boolean`  
Default: `false`

When including a css file in your app.styl by using @import "style.css", by default it will not include the full script, use `true` to compile into one script.
( **NOTICE:** the object key contains a space `"include css"` )

#### [resolve url](http://learnboost.github.io/stylus/docs/executable.html#resolving-relative-urls-inside-imports)
Type: `Boolean`  
Default: `false`

Telling Stylus to generate `url("bar/baz.png")` in the compiled CSS files accordingly from `@import "bar/bar.styl"` and `url("baz.png")`, which makes relative pathes work in Stylus.
( **NOTICE:** the object key contains a space `"resolve url"` and Stylus resolves the url only if it finds the provided file )

#### banner
Type: `String`  
Default: `''`

This string will be prepended to the beginning of the compiled output.

### Examples

```js
stylus: {
  compile: {
    options: {
      paths: ['path/to/import', 'another/to/import'],
      urlfunc: 'embedurl', // use embedurl('test.png') in our code to trigger Data URI embedding
      use: [
        require('fluidity') // use stylus plugin at compile time
      ],
      import: [      //  @import 'foo', 'bar/moo', etc. into every .styl file
        'foo',       //  that is compiled. These might be findable based on values you gave
        'bar/moo'    //  to `paths`, or a plugin you added under `use`
      ]
    },
    files: {
      'path/to/result.css': 'path/to/source.styl', // 1:1 compile
      'path/to/another.css': ['path/to/sources/*.styl', 'path/to/more/*.styl'] // compile and concat into single file
    }
  }
}
```


## Release History

* 2014-05-19   v0.0.4   Bump kouto-swiss to 0.1.2, stylus to 0.45.1
* 2014-05-19   v0.0.3   Bump kouto-swiss to 0.0.7
* 2014-05-13   v0.0.2   Bump kouto-swiss to 0.0.5
* 2014-05-11   v0.0.1   Forked from grunt-contrib-stylus.

---

Task submitted by [Eric Woroshow](http://ericw.ca)

*This file was generated on Thu May 01 2014 01:31:57.*
