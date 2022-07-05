---
title: ES6 let、const、var的區別
date: 2022-06-21 21:01:42
categories: Javascript
tags: 
- ES6
description: '不同變數的宣告方法'
---

## 前言

在es6以前，我們會用 var 來宣告一個變數。而在es6推出後，新增了 let 與 const的變數宣告方法，改善了使用 var 宣告變數的一些缺點，以下用講解 var 與 let const 宣告的差異。

## 區塊與函式作用域

var是函式作用域的設計，在函式內宣告的變數，函式外讀取不到。
但在一些使用了區塊語句(用花括號的語句)的像if, else, for, while等等區塊語句中，在這裡面用var宣告的變數仍然是會曝露到全域之中可被存取，例如:

![函式作用域](https://miro.medium.com/max/1178/1*iO1BqGOT_318PIkF8jjxJQ.png)

let或const來宣告是區塊作用域，就是以區塊語句 { } 為分界的作用域:

不管是在函式內宣告的變數，或是 在 if, else, for, while等等區塊語句{ }中宣告的變數，都不會在全域中被讀取到。

![區塊作用域](https://miro.medium.com/max/964/1*1IltRn_k3xANnY6fWcZW1A.png)

## 重複宣告的問題

以往用 var 宣告變數，是可以進行重複宣告的: 

``` js
var a = 1;
var a = 2;
```

這樣可能會不小心複寫了變數的值，導致專案出錯。

用 const let 告的變數，在同一個作用域下，則無法重新再被宣告。

![const let](https://miro.medium.com/max/440/1*06HErRPc-Jcyhazl3fuj7w.png)

![error](https://miro.medium.com/max/1286/1*zsSWcfXZBnj3Ap1D5JE7Pg.png)

## 常數

const 針對是常數的定義，常數在一宣告時就必定要指定給值，不然會產生錯誤。而對於常數在ES6的定義是: 不可再指定。

![const](https://miro.medium.com/max/1278/1*lpOInYC-ccAVD_dBcv5csg.png)

上面因為再次賦予 a = 20 而出現錯誤。

如果你宣告的常數是一個物件或陣列類型，像這種參照類型的值，裡面的值是可以作改變的，如下:

![array](https://miro.medium.com/max/336/1*IP1XW0OtYFB_Am976yXjNA.png)

所以對於物件、陣列、函式來說，使用 const 常數來宣告就可以，除非你有需要再指定這個陣列或物件的參照。

## Hoisting 向上提升特性

var 跟 function 都有向上提升特性，在宣告後會自動提升到 js 最上面 ，縱使還沒賦予值，還是先建立好記憶體位置。

``` js
console.log(a); // undefined
var a =3;
console.log(a); // 3
```

如上面程式，我們在第 2 行宣告了 a 變數等於3，但在第一行就讀取a變數，此時並不會報錯，因為 a 已經有記憶體位置了，只是還沒給予值，所以會是 undefined。 在第3行讀取a變數就可以正確讀到 3 的值。

let 跟 const 沒有向上提升， 必須先宣告、後使用。

``` js
console.log(b);  // b is not defined
let b = 3;
console.log(b);  // 3
```









