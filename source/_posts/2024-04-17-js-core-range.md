---
title: JS 核心篇 (4) JS 的範圍鍊
date: 2024-04-17 13:27:56
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 的範圍鍊'
---

## 範圍練

```js
var value = 1;
function fn1() {
  console.log(value);
}
function fn2() {
  var value = 2;
  fn1();
}
fn2();
```

上面範例中，console.log(value) 的值會是 1 , 因為js屬於靜態作用域，在程式碼撰寫完就確定作用域，和執行環境無關。
而範圍鍊的意思是，當函式本身沒有這個變數時，會向外尋找，所以 `fn1()` 向外就會找到全域的 `value = 1`；