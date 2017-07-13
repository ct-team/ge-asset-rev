## gulp-asset-rev

a plugin for gulp.js to replace file's name by adding content hash

## Installation

```bash
npm install ge-asset-rev
```

## Usage

```js
var gulp = require('gulp');
var assetRev = require('ge-asset-rev');

gulp.task('rev',function() {
    gulp.src("./test/test.html")
        .pipe(assetRev())
        .pipe(gulp.dest('./'));
});
```

## Options

### hashLen: length of hash version string
Type: `Number` default: 7

### verConnecter: version connect char
Type: `String` default: '-'

### rootPath: it should be assigned when the asset's path is an absolute path
Type: `String` default: ""

### verStr: use custom version string 
Type: `String` 

## Example

```js
var gulp = require('gulp');
var assetRev = require('./index.js');

gulp.task('rev',['revCss'],function() {
    gulp.src("./test/test.html")
        .pipe(assetRev())
        .pipe(gulp.dest('./dest'));
});

gulp.task('revCss',function () {
    return gulp.src('./test/styles/test.css')
        .pipe(assetRev())
        .pipe(gulp.dest('./dest/styles/'))
});
gulp.task('default',['rev']);
```

### before: test.css
```css
body{background:url('../images/bg.png')}
```

### after: test.css
```css
body{background:url("../images/bg.png?v=2769acd"}
```
### before: test.html
```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test.css" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test.png" />
    </div>
    <script src="./scripts/test.js" type="text/javascript"></script>
</body>
</html>
```
### after: test.html

```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test.css?v=0ede2cf" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test.png?v=25cf2b4" />
    </div>
    <script src="./scripts/test.js?v=8ced4e6" type="text/javascript"></script>
</body>
</html>
```



