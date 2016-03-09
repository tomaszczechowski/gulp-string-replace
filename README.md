# gulp-string-replace [![NPM version][npm-image]][npm-url] [![Build status][travis-image]][travis-url] [![dependencies][gulp-string-replace-dependencies-image]][gulp-string-replace-dependencies-url]
> Replaces strings in files by using string or regex patterns. Works with Gulp 3!

## Usage

```shell
npm install gulp-string-replace --save-dev
```
### Regex Replace
```javascript
var replace = require('gulp-string-replace');

gulp.task('replace_1', function() {
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace(new RegExp('@env@', 'g'), 'production'))
    .pipe(gulp.dest('./build/config.js'))
});

gulp.task('replace_2', function() {
  gulp.src(["./index.html"]) // Every file allown.
    .pipe(replace(/version(={1})/g, '$1v0.2.2'))
    .pipe(gulp.dest('./build/index.html'))
});

gulp.task('replace_3', function() {
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace(/foo/g, function () {
        return 'bar';
    }))
    .pipe(gulp.dest('./build/config.js'))
});
```
### String Replace
```javascript
gulp.task('replace_1', function() {
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace('environment', 'production'))
    .pipe(gulp.dest('./build/config.js'))
});
```
### Function Replace
```javascript
gulp.task('replace_1', function() {
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace('environment', function () {
        return 'production';
    }))
    .pipe(gulp.dest('./build/config.js'))
});

gulp.task('replace_2', function() {
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace('environment', function (replacement) {
        return replacement + '_mocked';
    }))
    .pipe(gulp.dest('./build/config.js'))
});

```

### API

#### replace(string, replacement)

##### string
Type: `String`

The string to search for.

##### replacement
Type: `String` or `Function`

The replacement string or function. Called once for each match.

#### replace(regex, replacement)

##### regex
Type: `RegExp`

More details here: [MDN documentation for RegExp].

##### replacement
Type: `String` or `Function`

More details here: [MDN documentation for String.replace].



### Release History
 * 2016-03-09  v0.1.0  Initial version of plugin.


Task submitted by [Tomasz Czechowski](http://czechowski.pl/)

[MDN documentation for RegExp]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp
[MDN documentation for String.replace]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#Specifying_a_string_as_a_parameter
[travis-url]: http://travis-ci.org/tomaszczechowski/gulp-string-replace
[travis-image]: https://secure.travis-ci.org/tomaszczechowski/gulp-string-replace.svg?branch=master
[npm-url]: https://npmjs.org/package/gulp-string-replace
[npm-image]: https://badge.fury.io/js/gulp-string-replace.svg
[gulp-string-replace-dependencies-image]: https://david-dm.org/tomaszczechowski/gulp-string-replace/status.png
[gulp-string-replace-dependencies-url]: https://david-dm.org/tomaszczechowski/gulp-string-replace#info=dependencies