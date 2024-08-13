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

在vue裡面，我們會先撰寫template，之後 vue 會將 template 轉為 JS 的物件，也就是vurtual dom，最後在將 vurtual dom 轉為真正的dom。

至於為什麼要先轉成 vurtual dom 是因為 vue 會拿這個 vurtual dom 去和舊的 vurtual dom 比較，看哪邊不一樣，並只更新不一樣的地方，不會像 innerHtml 是整個 dom 重新渲染，從而提升網頁效能。

## 安裝

``` js
// 用npm安裝 vue
npm create vue@latest

// 直接引入 cdn
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
``` 

安裝好後，可以在網頁上建立 vue 的實體

``` js
<div id="app">{{ message }}</div>

<script>
  // vue3 寫法
  const { createApp } = Vue;

  const vm = createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  });
  vm.mount('#app');
</script>
```

這個物件的 data 就是 vue.js 儲存的資料，而生成後的物件則透過 mount 和 html 綁定。當在建立物件實體時，還會引入一個物件參數，也就是 vue.js 實體的核心，稱為 options 物件。在這個 options 物件中會定義與ui相關的狀態、事件與方法。

## 模板語法

當 vue 實體掛載完成後，可以將data內的資料用 `{{ }}` 綁定到畫面。 `{{ }}` 可以做資料的簡單運算

``` js
<div id="app">
  數量: {{ quantity }}
  金額: {{ price }}
  總金額: {{ quantity * price }}
</div>

<script>
  // vue3 寫法
  const { createApp } = Vue;

  const vm = createApp({
    data() {
      return {
        price: 800,
        quantity: 10,
      }
    }
  });
  vm.mount('#app');
</script>
```

`{{ }}` 內可以帶入表達式進行運算

``` html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

非表達式不能被帶入 `{{ }}`

``` html
<!-- this is a statement, not an expression: -->
{{ var a = 1 }}

<!-- flow control won't work either, use ternary expressions -->
{{ if (ok) { return message } }}
```

## 模板可使用的window方法

只有特定的 window 方法，可以在template 內使用，如 Math、Date
可用方法參考[這裡](https://github.com/vuejs/core/blob/main/packages/shared/src/globalsAllowList.ts#L3)

 
## 共用data的汙染問題

當有多個 vue 實體想共用同樣的 data 格式時，會將 data 在實體外定義。此時 vue 物件內的 data 應該 return 解構後的 { ...dataObj }，避免兩個vue實體都修改到同一個物件。

``` js
<div id="app">{{ message }}</div>
<div id="app2">{{ message }}</div>

<script>
  // vue3 寫法
  const { createApp } = Vue;
  const dataObj = {
    message: 'Hello Vue!'
  }

  const vm1 = createApp({
    data() {
      return {
        return { ...dataObj }
      }
    }
  }).mount('#app');

  const vm2 = createApp({
    data() {
      return {
        return { ...dataObj }
      }
    }
  }).mount('#app2');
</script>
```










