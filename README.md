# gulp-markoc

[![npm](https://nodei.co/npm/gulp-markoc.svg?downloads=true)](https://nodei.co/npm/gulp-markoc/)

> Compile Marko templates as part of your Gulp build process.

## Usage

```js
var marko = require('gulp-markoc');

gulp.task('marko', function() {
  gulp.src('./src/*.marko')
    .pipe(marko({preserveWhitespace: true}).on('error', gutil.log))
    .pipe(gulp.dest('./public/'))
});
```

### Error handling

gulp-markoc will emit an error for cases such as invalid Marko syntax. If uncaught, the error will crash gulp.

You will need to attach a listener (i.e. `.on('error')`) for the error event emitted by gulp-markoc:

```javascript
var markoStream = marko({preserveWhitespace: true});

// Attach listener
markoStream.on('error', function(err) {});
```

In addition, you may utilize [gulp-util](https://github.com/wearefractal/gulp-util)'s logging function:

```javascript
var gutil = require('gulp-util');

gulp.src('./src/*.marko')
  .pipe(marko({preserveWhitespace: true}).on('error', gutil.log))
  // ...
```

## Options

The options object supports the same [options](http://markojs.com/docs/marko/javascript-api/#require'markocompiler') as the standard Marko compiler

## TODO

Fully comply with [Gulp plugin guidelines](https://github.com/gulpjs/gulp/blob/master/docs/writing-a-plugin/guidelines.md) AKA write some tests

## License

MIT License
