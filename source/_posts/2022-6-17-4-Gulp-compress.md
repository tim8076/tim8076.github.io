---
title: (9) Gulp-檔案壓縮
date: 2022-06-17 16:11:52
categories: Gulp
tags: 
- Gulp
description: '介紹gulp壓縮檔案的套件'
---

## 安裝套件

1. 壓縮 css套件: [gulp-clean-css](https://www.npmjs.com/package/gulp-clean-css)
2. 壓縮 js套件: [gulp-uglify](https://www.npmjs.com/package/gulp-uglify)

``` 
npm install gulp-clean-css gulp-uglify --save

```
## 載入設定

壓縮css的部分，可以在編譯完scss後，進行壓縮

``` js
function sassTask(){
  var plugins = [
    autoprefixer(),
  ];

  return gulp.src('./source/scss/**/*.scss')
    .pipe($.plumber())
    .pipe($.sourcemaps.init())
    .pipe(sass({
      includePaths: ['./node_modules/bootstrap/scss']
    }).on('error', sass.logError))
    .pipe($.postcss(plugins))
    .pipe($.cleanCss({ compatibility: 'ie8' })))
    .pipe($.sourcemaps.write('.'))
    .pipe(gulp.dest('./public/css'))
    .pipe(browserSync.stream())
}
```
![壓縮css程式碼](https://cdn-images-1.medium.com/max/1200/1*mpisvD3qy987427Pd2n-kg.png)

壓縮js的部分，可在babel編譯完後並且合併後( concat ) 進行壓縮

``` js
function babel(){
  return gulp.src('./source/js/**/*.js')
    .pipe($.plumber())
    .pipe($.sourcemaps.init())
    .pipe($.babel({
      presets: ['@babel/env']
    }))
    .pipe($.concat('all.js'))
    .pipe($.uglify()))
    .pipe($.sourcemaps.write('.'))
    .pipe(gulp.dest('./public/js'))
    .pipe(browserSync.stream())
}
```

![壓縮js](https://cdn-images-1.medium.com/max/1200/1*1anhKo-vPFyBKX4scALEZw.png)

## 壓縮成果

1. css被壓成一行

![css](https://cdn-images-1.medium.com/max/1200/1*tweaZBqP0_OJL3SnSgi-fQ.png)

2. js被壓成一行

![js](https://cdn-images-1.medium.com/max/1200/1*O3lohBob7h6KxqHGfVvong.png)
