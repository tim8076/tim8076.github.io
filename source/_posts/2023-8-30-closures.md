---
title: 閉包 closures
date: 2023-08-30 21:44:50
categories: Javascript
description: "閉包介紹"
---

## 閉包說明

當一個函式 return 另一個函式出來時，就是閉包的概念。

因為我們在呼叫函式以前，範圍鍊就已經建立，被 return 出來的函式，可以取得父層函式內部的變數。
所以閉包的概念就是，在另外一個作用域去參考他外層的變數，就會形成閉包。

```js
function count() {
  let count = 0;
  return function () {
    count += 1;
    console.log(count);
  };
}

const counter1 = count();
const counter2 = count();

counter1(); // 1
counter1(); // 2

counter2(); // 1
counter2(); // 2
```

因為每個 count()被執行時，會產生獨立的執行環境，讓 counter1、counter2 內部的 count 變數都是獨立的變數，並避免將 count 設定成全域變數，產生錯誤的風險。

```js
function clickHandler(size) {
  return function () {
    document.body.style.fontSize = `${size}px`;
  };
}

document.getElementById("size-12").onClick = clickHandler(12);
```

上面是另一個閉包範例，我們將 size 以參數傳入，並回傳一個設定字體大小的函式。

## 閉包回傳物件

```js
function storeMoney(initValue) {
  let money = initValue || 1000;
  return {
    increase: function (price) {
      money += price;
    },
    decrease: function (price) {
      money -= price;
    },
    value: function (price) {
      return money;
    },
  };
}
```

我們也可以在函式內回傳一個物件，利用物件內的函式去取得父層函式的變數值。
