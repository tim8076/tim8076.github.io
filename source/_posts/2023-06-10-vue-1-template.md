---
title: vue (1) 宣告式模板渲染
date: 2023-06-10 10:17:49
categories: Vue
tags: vue
description: 'vue 宣告式模板渲染'
---

## 宣告式與命令式

在純js裡，我們是用命令式的方式來寫程式。

- 命令式: 我們寫的每一行程式來命令電腦執行。

``` js
const btn = document.querySelector('bitton');
btn.addEventListener('click', clickHandler);

// 先命令電腦找出btn元素，再命令將btn綁上事件監聽
```

在vue裡，直接在模板上宣告想要的功能，vue會幫我們完成後面的動作。

- 宣告式: 直接在模板上宣告要使用的功能

``` html
<template>
  <button @click="clickHandler">
    開始
  </button>  
</template>

<!-- 直接在模板上綁定功能 -->
```

## Virtual Dom

[教學連結](https://youtu.be/DTJspLLm8Rs?list=PLEfh-m_KG4dbjf0YCJ7i0FFGK3FtQpanL&t=1800)

在vue裡面，我們會先撰寫template，之後 vue 會將 template 轉為 JS 的物件，也就是vurtual dom，最後在將 vurtual dom
轉為真正的dom。

至於為什麼要先轉成 vurtual dom 是因為 vue 會拿這個 vurtual dom 去和舊的 vurtual dom 比較，看哪邊不一樣，
並只更新不一樣的地方，不會像 innerHtml 是整個 dom 重新渲染，從而提升網頁效能。






