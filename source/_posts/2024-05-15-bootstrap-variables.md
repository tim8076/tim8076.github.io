---
title: Bootstrap (1) SCSS 客製化-基礎環境建立
date: 2024-05-15 11:30:14
categories: Bootstrap
tags:
  - Bootstrap
description: "更改SCSS以客製化 Bootstrap"
---

## 基礎環境建立

首先開一個資料夾，裡面有 index.html，和一個 scss 資料夾，裏頭有三隻 scss 檔案，

scss 則透過 vscode 內建插件 live scsss complie 進行編譯。

![](https://cdn-images-1.medium.com/max/1000/1*ljXEd-fRUB83xzOT2jmdSA.png)

## 下載 Bootstrap

1. 來到 [bootstrap 官網](https://getbootstrap.com/docs/5.3/getting-started/download/) 下載 bootstrap

   選擇 source code 下載

   ![](https://cdn-images-1.medium.com/max/1000/1*hWjzmqta0Yq-KkkYho1KuA.png)

2. 下載解壓縮後，在資料夾內找到 scss 資料夾，改名為 bootstrap 後，複製到一份自己的專案

![](https://cdn-images-1.medium.com/max/1000/1*OZLwWy0IKndZz9MiusJDXw.png)

![](https://cdn-images-1.medium.com/max/1000/1*KQSWVUTCbvmLI0OI8Y43YA.png)

3. 在 all.scss 中 import bootstrap

```
// all.scss
@import './bootstrap/bootstrap.scss';
@import './faq';
@import './index';
```

4. 在 index.html 中 css 的連結要選擇加入 bootstrap 編譯後的檔案

```html
<!DOCTYPE html>
<html lang="zh-Hant-TW">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="./style/all.css" />
  </head>
  <body>
    <h1>Hello World</h1>
    <a href="#" class="btn btn-primary">我是按鈕</a>
  </body>
</html>
```

![](https://i.imgur.com/Ja5djoR.png)

6. 到這邊就將 bootstrap 引入完成囉

![](https://cdn-images-1.medium.com/max/1000/1*GLy0I1Kvjl613M-R2tCFng.png)

## NPM 與 SCSS 下載方式 (vite 環境)

在專案中使用 npm 安裝 bootstrap

```js
npm install bootstrap@5.3.3
```

安裝完後我們的專案中 node_modules 資料夾會有 bootstrap

```
your-project/
├── scss/
│   └── all.scss
└── node_modules/
│   └── bootstrap/
│       ├── js/
│       └── scss/
└── index.html
```

在自己專案的 all.scss 中引入

```scss
// Custom.scss
// Option B: Include parts of Bootstrap

// 1. Include functions first (so you can manipulate colors, SVGs, calc, etc)
@import "bootstrap/scss/functions";

// 2. Include any default variable overrides here

// 客製化用的 variables
@import "./helpers/variables-dark";
@import "./helpers/variables";

// 3. Include remainder of required Bootstrap stylesheets (including any separate color mode stylesheets)
@import "bootstrap/scss/variables";
@import "bootstrap/scss/variables-dark";

// 5. Include remainder of required parts
@import "bootstrap/scss/maps";
@import "bootstrap/scss/mixins";
@import "bootstrap/scss/root";

@import "bootstrap/scss/bootstrap";
```

在 scss 資料夾中新增 helpers 資料夾，將 node_modules 裡的 bootstrap/scss/variables 、bootstrap/scss/variables-dark 檔案各複製一份放入。

![](https://cdn-images-1.medium.com/max/1000/1*olXn8F_ZcW5yTtl4GCGdkA.png)
