---
title: 從 0 開始的 webpack 5 專案(2) configuration
date: 2022-10-06 15:04:36
tags: Webpack
---

上一篇安裝完好後，我們的專案目前是這樣

``` 
node_modules
src
package.json
package-lock.json
```

現在可以來設定 ‵webpack.config.js`。

## Mode

通常我們在開發時，都會有開發模式、部署模式這兩種模式，在此就主要是透過 mode 屬性來設置。

``` js
module.exports =  {
  /* ... */
  mode: 'development',
}
```

## Entry

第一步要設定的是 entry point，也就是 webpack 會以哪支檔案作為進入點來開始打包檔案。換句話說，所有要被編譯的檔案都要import到進入點。

此範例中，我們將進入點設在 `src/index.js`

``` js
const path = require('path')

module.exports = {
  entry: {
    main: path.resolve(__dirname, './src/index.js'),
  },
```

## Output 

Output 是打包後檔案輸出的位置，設定在 `/dist` 資料夾。這邊的 [name] 會自動帶入 entry 設定的 main。[contenthash] 則是會生成一組 hash 而這個生成邏輯會依據提取的內容來生成。

為什麼會使用到 hash，最主要是避免瀏覽器的緩存問題，我們在開發時，通常會瘋狂的重新整理，而這過程就有可能導致緩存發生而無法確定我們修改的內容，那麼透過 hash 每一次存擋就重新生成不同的檔案名稱，這樣子瀏覽器就不會緩存內容了。

``` JS
module.exports = {
  /* ... */

  output: {
    path: path.resolve(__dirname, './dist'),
    filename: '[name].[contenthash].bundle.js',
  },
}
```

最後在 package.json 中的 scripts 屬性增加一行啟動指令

``` js
"scripts": {
    "build": "webpack"
},
```

然後在終端機輸入 `npm run build` 就可以成功打包檔案。此時專案資料夾下會多出一個 dist 資料夾。









