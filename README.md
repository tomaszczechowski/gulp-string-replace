# gulp-string-replace [![NPM version][npm-image]][npm-url] [![Build status][travis-image]][travis-url] [![dependencies][gulp-string-replace-dependencies-image]][gulp-string-replace-dependencies-url]
> Replaces strings on files by using string or regex patterns. Works with Gulp 3!

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
  gulp.src(["./config.js"]) // Every file allown.
    .pipe(replace(/@env@/g, '$1production'))
    .pipe(gulp.dest('./build/config.js'))
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
    .pipe(replace('@env@', 'production'))
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

## Release History
 * 2016-03-09   v0.0.1   Initial version of plugin.
---

Task submitted by [Tomasz Czechowski](http://czechowski.pl/)

[travis-url]: http://travis-ci.org/tomaszczechowski/gulp-string-replace
[travis-image]: https://secure.travis-ci.org/tomaszczechowski/gulp-string-replace.svg?branch=master
[npm-url]: https://npmjs.org/package/gulp-string-replace
[npm-image]: https://badge.fury.io/js/gulp-string-replace.svg
[gulp-string-replace-dependencies-image]: https://david-dm.org/tomaszczechowski/gulp-string-replace/status.png
[gulp-string-replace-dependencies-url]: https://david-dm.org/tomaszczechowski/gulp-string-replace#info=dependencies