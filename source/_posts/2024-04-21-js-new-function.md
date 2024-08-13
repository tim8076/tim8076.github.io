---
title: JS 基礎篇 (6) 函式的基本概念
date: 2024-04-21 13:11:11
categories: JS 基礎篇
tags: JS 基礎篇
description: '解釋function基本概念'
---

## 函式是物件的一種

在前面介紹變數型別的時候曾經說過，除了基本型別以外的都是物件。函式本身也是物件的一種，只是多了被呼叫的能力。

## 函式

「函式」指的是將一或多段程式指令包裝起來，可以重複使用，也方便維護。

宣告函式的方法有好幾種，但不管是什麼方式，通常一個函式會包含三個部分：

- 函式的名稱 (也可能沒有名稱)
- 在括號 ( ) 中的部分，稱為「參數 (arguments) 」，參數與參數之間會用逗號 , 隔開
- 在大括號 { } 內的部分，內含需要重複執行的內容，是函式功能的主要區塊。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*yEQ5TtUsQntKtxzUsqQPrQ.png)

## 定義函式的方式

- 函式宣告: 使用 function 關鍵字聲明函式，並指定函式名稱。函式聲明可以在程式碼的任何位置進行調用，因為它們會被提升（hoisted）至作用域的頂部。

``` js
function greet(name) {
    console.log("Hello, " + name + "!");
}
greet("World"); // 調用函式
```

- 函式表達式: 將函式賦值給一個變數，這種方式下，函式的名稱是可選的，也可以是匿名的。

``` js
// 將匿名函式賦予變數
var greet = function(name) {
    console.log("Hello, " + name + "!");
};
greet("World"); // 調用函式

// 將具名函式賦予變數
var functionD = function myFunc() {
  // 具名函式 myFunc 只能在函式內被調用
  console.log(functionD)
}

console.log(myFunc) // myFunc is not defined
```

- new Function

以使用 new Function 建構函式。new Function 允許你在執行時動態建立一個函式，你只需要提供函式的參數和函式體。

``` js
var myFunction = new Function(arg1, arg2, ..., body);
```

- arg1, arg2, ... 是函式的參數。這些是字串，每個字串代表一個函式參數的名稱。
- body 是函式的內容，也是一個字串，代表了函式的主體部分

範例

``` js
var addFunction = new Function('a', 'b', 'return a + b;');
console.log(addFunction(5, 3)); // 輸出: 8
console.log(b)
let b = 3;
console.log(b);
```

雖然 new Function 提供了動態建立函式的能力，但應該小心使用它，因為它的使用可能會讓程式碼難以閱讀和維護。通常情況下，函式聲明、函式表達式更加直觀和易於理解。

## 立即函式

``` js
// 將函式轉為立即函式
function myFunc() {
  console.log('call something');
}

// 步驟一 函式外層加上小括號 ()
(function myFunc() {
  console.log('call something');
})

// 步驟二 函式後方再加上小括號 ()
(function myFunc() {
  console.log('call something');
}())
```

立即函式有以下特點: 

1. 立刻執行
2. 無法在函式外被再次執行

``` js
(function myFunc() {
  console.log('call something');
}())

myFunc(); // myFunc is not defined
```

3. 可以不加上函式名稱

``` js
(function () {
  console.log('call something');
}())
```

4. () 可以移到外層

``` js
(function () {
  console.log('call something');
})()
```

5. 可傳遞參數到立即函式內

``` js
(function (where) {
  console.log(where); // 小明在這
})('小明在這');
```

6. 可以 return 值到外層

``` js
const whereMing = (function (where) {
  return where;
})('小明在這');
```

7. 常用來限制變數作用域，因為變數的作用域在函式內。

``` js
(function () {
  const Ming = '小明';
  console.log(Ming); // 小明
})();
console.log(Ming); // Ming is not defined
```

## 函式參數

``` js
function callName(a) {
  console.log(a); // 小明
  var a;
  console.log(a); // 小明
  a = '杰倫';
  console.log(a); // 杰倫
}

callName('小明');
```

參數在傳入函式時，已經定義好值，在函式內宣告一樣的變數，不會影響到原本參數。若要修改參數，就要在函式內重新賦值。

``` js
function callName(obj) {
  obj.name = '杰倫';
}
const family = {
  name: '小明';
}
callName(family);
console.log(family.name); // 杰倫
```

當把物件作為參數傳入時，因為物件傳參考的特性，若修改物件屬性的值，外層物件也會被修改。

## arguments 物件

Function被呼叫時會產生 arguments 物件，用來記錄傳入的參數。 arguments不是陣列，只是具有索引特性的物件，內建.length屬性。

``` js
function sum() {
  var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  return total;
}
console.log(sum(1, 2, 3)); // 输出：6
console.log(sum(5, 10, 20, 30)); // 输出：65
```

要注意的是箭頭函式沒有 arguments 物件，而是改用其餘參數的方式取得

`const func = (...args) => console.log(args)`;
















