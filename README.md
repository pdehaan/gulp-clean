# [gulp](https://github.com/wearefractal/gulp)-clean [![Build Status](https://secure.travis-ci.org/peter-vilja/gulp-clean.png?branch=master)](https://travis-ci.org/peter-vilja/gulp-clean) [![NPM version](https://badge.fury.io/js/gulp-clean.png)](http://badge.fury.io/js/gulp-clean)

> Removes files and folders.

## Install

Install with [npm](https://npmjs.org/package/gulp-clean).

```
npm install --save-dev gulp-clean
```

## Examples

```js
var gulp = require('gulp');
var clean = require('gulp-clean');

gulp.task('default', function () {
	gulp.src('app/tmp', {read: false})
		.pipe(clean());
});
```
Option read false prevents gulp to read the contents of the file and makes this task a lot faster.

```js
var gulp = require('gulp');
var clean = require('gulp-clean');

gulp.task('default', function () {
	gulp.src('app/tmp/index.js', {read: false})
		.pipe(clean({force: true}));
		.pipe(gulp.dest('dist'));
});
```

##### For safety files and folders outside the current working directory can be removed only with option force set to true.

Clean as a dependency:

```js
var gulp = require('gulp');
var clean = require('gulp-clean');

gulp.task('clean-scripts', function () {
  return gulp.src('app/tmp/*.js', {read: false})
    .pipe(clean());
});

gulp.task('scripts', ['clean-scripts'], function () {
  gulp.src('app/scripts/*.js')
    .pipe(gulp.dest('app/tmp'));
});

gulp.task('default', ['scripts']);
```


## License

[MIT](http://en.wikipedia.org/wiki/MIT_License) @ Peter Vilja
