---
title: 從 0 開始的 webpack 5 專案(3) html-webpack-plugin
date: 2022-10-07 11:15:09
tags: Webpack
description: '使用 html template 動態載入js內容'
---

## html-webpack-plugin

目前我們已經可以打包隨機名稱的 js 到 dist 資料夾。但因為每次打包 js 名稱都是隨機的，我們需要一個能動態引入js檔名的html template，這邊會用到 html-webpack-plugin 這個插件。

- html-webpack-plugin : 從template模板產生 html

首先安裝插件

```
npm i -D html-webpack-plugin
```

然後在 src 資料夾裡 新增 template.html，html裡的 head 可以用變數的方式帶入。

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>

  <body>
    <div id="root"></div>
  </body>
</html>
```

在 congif 檔新增 plugin ，輸出的 filename 設定為 index.html，template則連結到目前template的位置。

``` js
webpack.config.js
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
  /* ... */

  plugins: [
    new HtmlWebpackPlugin({
      title: 'webpack Boilerplate',
      template: path.resolve(__dirname, './src/template.html'), // template file
      filename: 'index.html', // output file
    }),
  ],
}
```

最後執行 npm run build 就會產生 dist 資料夾，而裡頭有輸出好的 index.html。
