---
title: (7) Gulp-browserSync
date: 2022-06-17 14:58:42
categories: Gulp
tags: 
- Gulp
description: 'browserSync 能建立起一個暫時性的開發用伺服器。搭配 gulp 使用，就能達成檔案修改時，browserSnyc 會自動重整畫面'
---

## 什麼是 broswer sync

browserSync 能建立起一個暫時性的開發用伺服器。搭配 gulp 使用，就能達成檔案修改時，browserSnyc 會自動重整畫面，讓開發者能在瀏覽器上即時看到修改後的畫面。

## 安裝流程

網址: [https://browsersync.io/docs/gulp](https://browsersync.io/docs/gulp)

安裝套件

``` 
npm install browser-sync gulp --save
```

在gulpfile.js中引入

``` js
const browserSync = require('browser-sync').create();
```

建立任務，指定伺服器位置為最後輸出的public資料夾

``` js
function browser(){
  browserSync.init({
    server: { baseDir: "./public" },
    reloadDebounce: 2000
  });
}
```

在其他gulp任務輸出的最後加上 `.pipe(browserSync.stream())`

如在babel任務加上，就會在babel更新後，自動同步到瀏覽器。

``` js
function babel(){
  return gulp.src(path.js.src)
    .pipe($.plumber())
    .pipe($.sourcemaps.init())
    .pipe($.babel({
      presets: ['@babel/env']
    }))
    .pipe($.concat('all.js'))
    .pipe($.if(options.env === 'prod', $.uglify()))
    .pipe($.sourcemaps.write('.'))
    .pipe(gulp.dest(path.js.des))
    .pipe(browserSync.stream())
}
```





