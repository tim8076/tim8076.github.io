---
title: (6) Gulp-babel
date: 2022-06-17 14:04:45
categories: Gulp
tags: 
- Gulp
- gulp-babel
description: '使用babel套件，可以將 一些新的js語法，如箭頭函式、let、const，編譯為舊版瀏覽器看得懂的語法。'
---

## 什麼是 babel
使用babel套件，可以將 一些新的js語法，如箭頭函式、let、const，編譯為舊版瀏覽器看得懂的語法。

## 安裝套件

```
npm install --save-dev gulp-babel @babel/core @babel/preset-env
npm install --save gulp-sourcemaps  //壓縮後，可標記原始碼位置
npm install --save gulp-concat  //合併程式碼用
```

在 gulpfile.js 中引入任務

``` js
function babel(){
  return gulp.src('./source/js/**/*.js')
    .pipe($.plumber())
    .pipe($.babel({
      presets: ['@babel/env']
    }))
    .pipe($.concat('all.js'))
    .pipe(gulp.dest('./public/js'))
}
```

函式中，我們指定source資料夾裡的 js檔案進行用babel編譯，
並用concat套件將多支js檔案在輸出時合併成一支，最後用dest輸出到public資料夾。

## sourcemap套件

因為多支js檔案，最後會被編譯成同一支js。為了在最終編譯的js中，查找原先程式碼的位置，可以使用 sourcemap套件。

``` js
function babel(){
  return gulp.src('./source/js/**/*.js')
    .pipe($.plumber())
    .pipe($.sourcemaps.init())
    .pipe($.babel({
      presets: ['@babel/env']
    }))
    .pipe($.concat('all.js'))
    .pipe($.sourcemaps.write('.'))
    .pipe(gulp.dest('./public/js'))
}
```

![sourcemaps](https://cdn-images-1.medium.com/max/1200/1*ZT2zdCDxGvinb_v13KRccQ.png)

sourcemap 除了js檔案以外，也可以用在如scss檔案

![scss-source](https://cdn-images-1.medium.com/max/1200/1*nQzF8npRYhWcAaXJAzGgDw.png)
















