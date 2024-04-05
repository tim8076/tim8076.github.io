---
title: 閉包 closures
date: 2023-08-30 21:44:50
categories: Javascript
description: '閉包介紹'
---

## 閉包說明

當一個函式 return 另一個函式出來時，就是閉包的概念。

``` js
function count() {
  let count = 0;
  return function () {
    count += 1;
    console.log(count);
  }
}

const counter1 = count();
const counter2 = count();

counter1() // 1
counter1() // 2

counter2() // 1
counter2() // 2
```

在內層的函式能取得外層函式的變數，讓 counter1、counter2 都是獨立的計算器。
並避免將 count 設定成全域變數，產生錯誤的風險。


``` js
function clickHandler(size) {
  return function() {
    document.body.style.fontSize = `${size}px`
  }
}

document.getElementById('size-12').onClick = clickHandler(12);
```

上面是另一個閉包範例，我們將 size 以參數傳入，並回傳一個設定字體大小的函式。

