---
title: 從 0 開始的 webpack 5 專案(8) 圖片
date: 2022-10-07 17:25:35
tags: Webpack
description: '在 webpack 裡 打包圖片'
---

## 圖片

js 預設是不能直接載入圖片的，可以先新增 src/images 資料夾，並新增圖片到資料夾裡，最後試試將圖片看引入 js 檔裡。

``` js
import example from './images/example.png'
```

然後執行 npm run build 會發現錯誤發生。

為了解析圖片，webpack 有內建的 asset modules 可以用在靜態資源上。我們會使用 asset/resource 在圖片類型上。

``` js
module.exports = {
  /* ... */
  module: {
    rules: [
      // Images
      {
        test: /\.(?:ico|gif|png|jpg|jpeg)$/i,
        type: 'asset/resource',
      },
    ],
  },
}
```

最後在執行 npm run build 就可以成功打包圖片囉。






