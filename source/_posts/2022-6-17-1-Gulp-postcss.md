---
title: (5) Gulp-postcss
date: 2022-06-17 11:21:01
categories: Gulp
tags: 
- Gulp
description: 'postcss讓開發者依然撰寫 CSS，再經過擴充功能（plugin）的後製處理，將特定功能轉成瀏覽器能懂的指令。'
---

## PostCSS 是什麼 ?
PostCSS 是一個使用JavaScript 轉換CSS 的工具。
以前在撰寫css時，因為有些新的語法舊的瀏覽器不支援，所以需要加上前贅詞

![img](https://cdn-images-1.medium.com/max/1200/1*0gGNaqjQjKhcOhyBck5Bhw.png)

但這步驟如果用人工判斷很費時，此時可以用post css搭配 autoprfixer 套件，來自動加入這些前贅詞。

## 安裝流程

先安裝套件

```
npm install postcss gulp-postcss autoprfixer --save
```

然後在 `gulpfile.js` 中載入套件

``` js
const autoprefixer = require('autoprefixer');
const postcss = require('gulp-postcss');
```

在我們編譯sass的任務中，加入postcss功能

``` js
function sassTask(){
  var plugins = [
    autoprefixer(),
  ];

  return gulp.src('./source/scss/**/*.scss')
    .pipe(plumber())
    .pipe(sass().on('error', sass.logError))
    .pipe(postcss(plugins))
    .pipe(gulp.dest('./public/css'))
}
```

上面我們先新增一個 plugins 的變數，並在編譯成css後，加入 `postcss(plugins)`

此時可能會遇到這個錯誤

![error](https://cdn-images-1.medium.com/max/1200/1*r49hPlucU_l7u-wYZtzGBg.png)

這個錯誤是要我們在根目錄增加一個 .browserslistrc 的檔案，裡面放需要支援的瀏覽器版本條件，如下圖:

![browser](https://cdn-images-1.medium.com/max/1200/1*RiUzC2vYWqZEFgT0nCa7lA.png)

之後如果要調整 CSS 支援版本就只需要調整 .browserslistrc 中的 last X version X 即可，關於支援版本設定，可參考[這裡](https://github.com/browserslist/browserslist)。

以上就完成gulp-postcss的的設定囉

