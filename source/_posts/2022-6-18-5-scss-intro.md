---
title: (1) SCSS練功坊-基礎介紹
date: 2022-06-18 16:06:16
categories: scss
tags: 
- scss
description: 'scss 基礎介紹'
---

## 前言

scss屬於css的預處理器，他加入了程式語言所用的變數、迴圈、模組化等概念，讓我們更方便管理css。
現今較為主流的 CSS 預處理器有三種，分別是 Sass/SCSS、Less、Stylus，其中的 Sass/SCSS 是目前較多人使用的選擇。

## scss 語法介紹

### 巢狀寫法（Nesting）

以往寫css時，為了選取到某個元素底下的標籤，我們可能會重複選取該元素許多次，例如:

``` css
.card ul {
  list-style: none;
}
.card li {
  display: inline-block;
}
.card a {
  display: block;
}
```

上面程式碼中，我們重複寫了 .card 3次。

在scss中我們可以用巢狀的寫法來減少重複的code，並且當父元素的class更改時，也只需要改一次即可:


``` scss
.card {
  ul {
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    display: block;
  }
}
```

## 小結

scss的功能除了上述介紹的巢狀語法以外，還有許多如變數、函式、mixin、模組化等概念會在之後等章節來介紹喔。






