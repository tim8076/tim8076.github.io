---
title: 從 0 開始的 webpack 5 專案(6) Babel
date: 2022-10-07 13:52:33
tags: Webpack
description: '使用 Babel loader 來編譯 js'
---

## Babel

為了兼容較舊版本的瀏覽器，需要將比較新的 js 語法利用 babel 這個 loader 來轉換成舊的語法。

- babel-loader - Transpile files with Babel and webpack.
- @babel/core - Transpile ES2015+ to backwards compatible JavaScript
- @babel/preset-env - Smart defaults for Babel

```
npm install -D babel-loader @babel/core @babel/preset-env webpack
```

安裝好 loader 後，在 config 檔裡設定新的 rule

``` js
module: {
  rules: [
    {
      test: /\.m?js$/,
      exclude: /node_modules/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: [
            ['@babel/preset-env', { targets: "defaults" }]
          ]
        }
      }
    }
  ]
}
```

為了測試用，在 src/index.js 新增一些新的 js 語法

``` js
// Create a class property without a constructor
class Game {
  name = 'Violin Charades'
}
const myGame = new Game()
// Create paragraph node
const p = document.createElement('p')
```

最後執行 npm run dev 就可以成功轉換成較舊的語法。



