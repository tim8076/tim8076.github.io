---
title: (11) Gulp 釋出開發成品
date: 2022-06-18 13:58:17
categories: Gulp
tags: 
- Gulp
description: '釋出開發成品'
---

## 安裝 gulp clean

在gulp專案中，有時我們可能在source資料夾裡有一些test檔案，是不該被編譯到public資料夾內的。但無法記得到底哪些test已經被編譯，那些沒有。此時就可以用 gulp clean、gulp-sequence來清理最終的public資料夾。

```
npm install gulp-clean --save
```

建立一個 clean 任務

``` js
function clean(){
  return gulp.src(['./public'], { read: false, allowEmpty: true })
    .pipe($.clean());
}
```
利用 clean 任務，刪除如 .tmp(暫存資料夾)、public資料夾，目的是將資料夾刪除後，重新編譯。

## gulp parallel、series

在 gulp4.0 中新增了 parallel、series兩個方法

1. parallel : 任務同時執行
2. series : 任務依序執行

我們可以用這兩個方法，讓我們之前建立的各種gulp任務，依序或同時執行。

``` js
exports.build = gulp.series(clean, ejs, sassTask, babel, vendorsJs)

exports.default = gulp.series(clean, ejs, sassTask, babel, vendorsJs, gulp.parallel(watch, browser))
```

在 `gulpfile.js` 的最後，分別輸出build跟default指令。 

- default: 為預設指令，在commend line上輸入 gulp 即可執行。
- build: 用來產出成品，在commend line上輸入 gulp build 即可執行。

在 gulp.series() 中我們依序執行 clean、ejs、sass等任務，但要注意，在 export.default是開發時使用，所以加上了watch， browser等監聽的任務，若在build成品，則不需加入。

## 完成程式碼參考

[參考範例](https://github.com/tim8076/gulp-project/blob/main/gulpfile.js)






