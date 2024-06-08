---
title: (5) CSS基礎篇 Block 與 Inline
date: 2024-05-02 11:23:18
categories: CSS
tags: 
- CSS基礎篇
description: '介紹區塊與行內元素'
---

## 什麼是display(顯示模式)?

CSS中的display屬性用於指定元素的渲染方式，即指定元素在網頁中如何顯示。這個屬性控制元素是以何種方式佔據空間，以及如何與其它元素相互作用。

## Block 區塊元素

``` css
.box {
  display: block;
} 
```

block 區塊元素有以下特點

- 元素寬度預設會佔滿一整行，無法與其他元素並列
- 元素即使設置了寬度,仍然是獨占一行
- 可以設定高度和寬度
- 可以設置 margin 和 padding 属性

常見的預設為 block 元素標籤有: div、ul li、p、h1


## Inline 行內元素

``` css
.img {
  display: inline;
} 
```

inline 元素有以下特點

- 元素可在同一行內呈現，可與其他元素並列
- 無法調整元素的寬高，元素的寬高由它的內容撐開
- 設置上下 margin 無效，左右 margin 有效
  設置上下 padding 無效，左右 padding 有效

常見的預設為 inline 元素標籤有: span、a、input、img

## inline-block

``` css
.container {
  display: inline-block;
}
```

inline-block 元素有以下特點

- 可與其他元素並列
- 可以設定高度和寬度
- 可以設定 margin/padding



