---
title: 從 0 開始的 webpack 5 專案(4) webpack-clean
date: 2022-10-07 11:35:07
tags: Webpack
description: '使用 webpack-clean 清除舊檔案'
---

## 清除檔案

開發時如果不斷執行 npm run dev 、npm run build ，會在 dist 產生許多打包後的檔案。為了讓每次打包時都能清除上一次打包的檔案，會用到 clean-webpack-plugin 這個 plugin。

``` 
npm i -D clean-webpack-plugin
```

安裝後引入config

``` js
const path = require('path')

const HtmlWebpackPlugin = require('html-webpack-plugin')
const { CleanWebpackPlugin } = require('clean-webpack-plugin')

module.exports = {
  /* ... */

  plugins: [
    /* ... */
    new CleanWebpackPlugin(),
  ],
}
```

這樣就完成囉。




