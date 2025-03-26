---
title: JS 表單取值
date: 2024-12-07 11:43:15
categories: Javascript
tags: Javascript
description: '介紹 JS 表單取值方法'
---

## .value 取出的值是「字串」

這邊以 input 的 value 取值為例，請觀看以下範例：

```html
<input type="text" id="targetInput">
<button type="button" id="triggerBtn">觸發按鈕</button>
```

```js
const el = document.querySelector('#targetInput');
const triggerBtn = document.querySelector('#triggerBtn');

triggerBtn.addEventListener('click', function(e){
    console.log(el.value);
    console.log(typeof(el.value));
})
```

如果在 input 輸入數字 123 以後點選「觸發按鈕」，可以在 console 中觀察到以下結果：

```js
// '123'
// 'string'
```

.value 取出來的值為字串，因此如果要對表單的「數值」進行運算，請記得要先使用 parseInt 做型別轉換。

```js
let newValue = parseInt(el.value);
```

## .value, .getAttribute('value') 的差異

```html
<input type="text" id="targetInput" value="123">
<button type="button" id="triggerBtn">觸發按鈕</button>
```

```js
const el = document.querySelector('#targetInput');
const triggerBtn = document.querySelector('#triggerBtn');
console.log(`el.value: ${el.value}`);

triggerBtn.addEventListener('click', function(e){
  el.value = "任意填入的值";
  console.log(`el.value: ${el.value}`);
  console.log(`el.getAttribute('value'): ${el.getAttribute('value')}`);
})
```

點擊按鈕後可以發現， el.value 被更換為 "任意填入的值"，但 el.getAttribute 取得的還是預設的值 123。

統整:

- el.value 對應的是 input 欄位目前「輸入的值」
- el.getAttribute('value') 對應的是 input 標籤的「預設屬性值」
- 修改 el.value 並不會影響 input 標籤的 value 預設屬性，使用 setAttribute() 才會。







