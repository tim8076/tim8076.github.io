---
title: 從 0 開始的 webpack 5 專案(7) Style
date: 2022-10-07 14:14:23
tags: Webpack
description: '使用 sass-loader 來編譯 sass'
---

現在前端開發的樣式處理方面可能會用到

- sass: css 的預處理器，新增了變數、模組化等功能到樣式的開發上
- postcss: css 的後處理器，幫樣式新增必要的前贅詞，以兼容舊版瀏覽器。

而在 webpack 裡為了將 css import 到 index.js裡，需要對應的 loader

- sass-loader - Load SCSS and compile to CSS
- sass - sass
- postcss-loader - Process CSS with PostCSS
- postcss-preset-env - Sensible defaults for PostCSS
- css-loader - Resolve CSS imports
- style-loader - Inject CSS into the DOM

``` 
npm i -D  sass-loader sass postcss-loader css-loader style-loader postcss-preset-env
```

在 config 檔裡新增 postcss的設定

``` js
module.exports = {
  plugins: {
    'postcss-preset-env': {
      browsers: 'last 2 versions',
    },
  },
}
```

在 src 資料夾裡新增 styles 資料夾，裡頭新增 main.scss 檔案

``` scss
$font-size: 1rem;
$font-color: lch(53 105 40);

html {
  font-size: $font-size;
  color: $font-color;
}
```

在 index.js 裡引入 main.scss

``` js
import './styles/main.scss'
```

然後在 config 裡新增 sass 的 rule

``` js
module.exports = {
  /* ... */
  module: {
    rules: [
      // CSS, PostCSS, and Sass
      {
        test: /\.s[ac]ss$/i,
        use: ['style-loader', 'css-loader', 'postcss-loader', 'sass-loader'],
      },
    ],
  },
}
```

最後執行 npm run dev 就可以成功編譯囉。




