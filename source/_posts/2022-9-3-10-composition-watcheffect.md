---
title: Composition Api(十) watchEffect
date: 2022-09-03 16:50:44
categories: Vue
tags: Composition api
description: "用watchEffect 監測資料"
---

## 使用 watchEffect

watchEffect 一樣可以監聽變數，並當變數的值做更動時觸發特定行為。
要使用 watchEffect 首先一樣 先解構出來

![](https://cdn-images-1.medium.com/max/1100/1*VAQXVtjD4kKRlfLgdALswA.png)

在這個範例中有兩筆資料，一個是純值，一個是物件

![](https://cdn-images-1.medium.com/max/1100/1*agWzlPkJYOzzpwri7k5V0w.png)

![](https://cdn-images-1.medium.com/max/1100/1*_WUhmapmM5hfvI-tnyvsMw.png)

並有一個變數 watchText 來接收 watchEffect 監聽的值。

在 watchEffect 帶入一個 callback function，和 watch 不同的是，不需要指定監聽的變數是哪個，只要雙向綁定的資料有出現在 watchEffect 函式裡就會被監聽。

所以在上面範例中，將監聽的值寫回 watchText 裡。

## 停止監聽

要停止 watch 監聽，只要將 watch 賦予到變數，並呼叫即可

```js
const stopWatchEffect = watchEffect(() => {
  console.log("watchEffect run", search.value);
});
stopWatchEffect();
```
