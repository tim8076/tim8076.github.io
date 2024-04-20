---
title: JS 核心篇 (5) JS 的提升
date: 2024-04-17 13:51:35
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 的提升'
---

## 提升

當我們在建立一個執行環境時，分為兩個階段，創造環境和執行。

![](https://cdn-images-1.medium.com/max/1000/1*LXm5uSoMkdHf8lD-FYu6tQ.png)

當使用 var 宣告變數或用 function 建立函式時，會有`提升 hoisting`的現象。
也就是在創造環境就先將變數放入記憶體，但此時還沒給值，所以是 undfined。到執行時才會將值賦予到變數。

![創造環境階段](https://cdn-images-1.medium.com/max/1000/1*BlVgvBz_VAVht4P-aLQMYw.png)

![執行階段](https://cdn-images-1.medium.com/max/1000/1*XFhNGWc651xhzUR2eE7DQA.png)

![](https://cdn-images-1.medium.com/max/1000/1*eSZE8EDxCleZSKCeqRw54w.png)

函數陳述式和var變數不同的是，在創造階段完整的函式就會被放入記憶體。

``` js
fn1();
function fn1() {
  console.log(1)
}
```
如上，因為完整的函式fn1()在創造階段就放入記憶體了，所以可以在宣告前使用函式。

``` js
fn1(); // fn1() is not a function
console.log(fn1) // undefined
var fn1 = function() {
  console.log(1);
}
```
若是函式表達式，因為只有變數名稱被存入記憶體，會出現 undefined，無法提前使用。

## 函式優先

若同時有函數陳述式和用var宣告的變數，在創造階段含是會優先被提昇。

``` js
// 創造環境
function fn1() {
  console.log(ming);
}
var ming;

// 執行階段
fn1();
ming = '小名';
```

如上，執行 fn1() 會出現 undefined， 因為值在執行階段才給予。








