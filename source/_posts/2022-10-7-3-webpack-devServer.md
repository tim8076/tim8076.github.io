---
title: 從 0 開始的 webpack 5 專案(5) webpack-dev-server
date: 2022-10-07 13:27:39
tags: Webpack
description: '使用 web-dev-server 開啟 模擬伺服器'
---

## webpack-dev-server

每當有修改檔案就要 `npm run build` 來打包會很麻煩，而且當檔案越多包時間就越久。所以可以新增模擬伺服器的插件，它會自動開啟一個瀏覽器以便我們即時看到畫面上的修改與變化。

``` 
npm i -D webpack-dev-server
```

然後在 config 裡新增 devServer 選項

``` js
const path = require('path');

module.exports = {
  mode: 'development',
  devServer: {
    static: {
      directory: path.resolve(__dirname, './dist'),
    },
    port: 3000,
    open: true,
    hot: true,
    compress: true,
  },
}
```

- port: 選擇開啟網頁的 port
- compress: 將我們所有的檔案壓縮變成 .gzip 的檔案，這樣子在我開啟瀏覽器時的速度就會比較快
- open: 你執行模擬伺服器時是否要自動開啟瀏覽器的意思
- hot: 又稱之為 HMR (Hot Module Replacement)，透過啟用這個屬性，當我們修改 src 底下的資源時，也會同時更新模擬伺服器。

最後在 package.json 裡新增 dev 指令

``` js
"scripts": {
  "build": "webpack",
  "dev": "webpack serve",
},
```

接下來只需要輸入 npm run dev 就可以開啟模擬伺服器了。

