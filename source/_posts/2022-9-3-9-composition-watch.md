---
title: Composition Api (九) watch
date: 2022-09-03 16:46:33
categories: Vue
tags: Composition api
description: "用watch 監測資料"
---

## 使用 watch

要使用 watch 方法，一樣先從 vue 中解構出來

![](https://cdn-images-1.medium.com/max/1100/1*Dw-eJPBN1vBUrrLxLZF0cg.png)

## 監聽純值

![](https://cdn-images-1.medium.com/max/1100/1*ubEKCZ8Az-DwaBKxfdcCjw.png)

上圖中，使用 watch 方法監聽 productName 這個值，並在 productName 這個值更動時，將值寫回 watchText 裡。

要注意的是，當今天監聽的是物件，如上圖 person 物件裡的值，要在第一個參數前方補上箭頭函式。

![](https://cdn-images-1.medium.com/max/1100/1*9Y_o_Bf5qLPp6iboKar4Sg.png)

## 深層監聽

```js
watch(
  product,
  (newValue, oldValue) => {
    console.log(newValue, oldValue);
  },
  { deep: true }
);
```

當監聽的是整包物件時，要加上 { deep: true } ，來進行深層監聽。

## 多項目監聽

```js
watch(
  [productName, product],
  ([productNameVal, productVal], [productNamePre, productPre]) => {
    console.log("純值", productNameVal, productNamePre);
    console.log("物件", productVal, productPre);
  },
  { deep: true }
);
```

當同時監聽多個項目時，用陣列帶入參數。

## 停止監聽

要停止 watch 監聽，只要將 watch 賦予到變數，並呼叫即可

```js
const stopWath = watch(search, () => {
  console.log("watching");
});
stopWath();
```
