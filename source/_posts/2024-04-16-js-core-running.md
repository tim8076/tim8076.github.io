---
title: JS 核心篇 (1) JS 是如何運行的
date: 2024-04-16 13:11:25
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 的運行方式'
---

## JS 的運行方式

``` js
var ming = '小名';
```

我們撰寫的 JS 是無法直接被瀏覽器給閱讀的，要經過解譯才能運行這段程式碼。

程式語言可以分為 直譯式語言和編譯式語言，JS就屬於 直譯式語言。

## 編譯式語言

![](https://cdn-images-1.medium.com/max/1000/1*SG3vsBwfXSaHb67XRvxU3w.png)

編譯式語言會將程式碼預先編譯，編譯完後將代碼生成出來，最後在丟給執行環境運行。好處是在編譯時就能先除錯，譯式語言的執行速度通常比直譯式語言更快。

## 直譯式語言

![](https://cdn-images-1.medium.com/max/1000/1*yZOp1b7eufv7P0JwF2SlJg.png)

直譯式語言的程式碼是由直譯器逐行解釋和執行的。當你執行一段直譯式語言的程式碼時，直譯器會一行一行地讀取程式碼，並且將其轉換成相應的機器碼或是直接執行相應的動作。
優點是它們的執行速度較快，因為它們可以立即執行程式碼而不需要經過編譯的過程，但若程式碼有錯誤，也會直接反映在環境上。


![](https://cdn-images-1.medium.com/max/1000/1*zQJFAG9_uch7FKBSuHgxyw.png)

- 語法單元化: 將 js 的符號、詞彙一一解析出來。
- 抽象結構樹: 將原始碼結構定義出來。

js 編譯過程可以參考以下網站。
[編譯網站](https://esprima.org/demo/parse.html#)

## 執行的錯誤情境 LHS, RHS

![](https://cdn-images-1.medium.com/max/1000/1*9zBrr9y5W8-aeg6U3OFW6g.png)

``` js
// LHS: 當值從右側賦予到左側時
let ming = '小名';

// 當左邊不是變數無法被賦值時，會跳錯誤
'MING' = '小名'; 
Uncaught SyntaxError: Invalid left-hand side in assignment
```

``` js
// 在 JavaScript 中，RHS 通常指代賦值操作符（=）右邊的表達式，這是一個很常見的概念。以下是一個示例：
let x = 5;
// 在這個例子中，"x = 5" 是賦值操作，而 "5" 就是 RHS。因為它是指賦值操作符右邊的值，它是表達式的一部分。
```

RHS 不會在編譯過程中出現錯誤，而是在執行階段才發現變數無法取得

``` js
let ming = 5;
console.log(min);
Uncaught ReferenceError: min is not defined
```


