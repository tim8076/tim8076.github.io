---
title: JS 核心篇 (2) JS 的作用域
date: 2024-04-16 13:59:52
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 的作用域'
---

## 靜態與動態作用域

![](https://cdn-images-1.medium.com/max/1000/1*_-44uYqBfkpzwjuyWvjdqg.png)

- 靜態作用域: 變數的作用域在語法解析就已經決定，不會改變。 JS屬於此類
- 動態作用域: 變數的作用域在函式調用時才決定。

範例:

``` js
var value = 1;
function fn1() {
  console.log(value); // 1
}
function fn2() {
  var value = 2;
  fn1();
}
fn2(); 
```
因為 js 是靜態作用域，所以 fn1()被執行時會去取得外層 1 的值，而不是fn2被調用後才改變的值。

## 作用域

![](https://cdn-images-1.medium.com/max/1000/1*WE0NuL_9ntARx1kiJQP9Sg.png)

JS 的作用域是一層一層向內的，最外層會有一個全域的作用域，內層則由function 所包著，每個 function 的作用域是獨立的。
當這個 function 要讀取某個變數，但函式內沒有時，會向外查找，若外層也沒有則會出現錯誤。






