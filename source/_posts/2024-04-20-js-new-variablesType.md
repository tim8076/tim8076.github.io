---
title: JS 基礎篇 (1) 變數與資料型別
date: 2024-04-20 14:08:42
categories: JS 基礎篇
tags: JS 基礎篇
description: '介紹 JS 的變數'
---

## 變數

變數是用來儲存資料和運算的基本單位，可以將變數想像成存放資料的盒子。使用時，記得要先宣告、在使用。

### 變數命名規則:
  1. 開頭不能是數字
  2. 第一個字母必須為英文、底線_、或是錢字號$
  3. 英文大小寫有區分
  4. 變數建議語意化，如跟價格有關 可用 price 作為名稱
  5. 不能使用 if for in var 等JS原本內建的 [關鍵字](https://pydoing.blogspot.com/2010/12/javascript-reserved.html)

JS 為弱型別語言，變數在宣告時，無須指定型別，型別的資訊只存在【值】或【物件】本身。

``` js
var a = 'Hello'; // 型別為字串，由 'Hello' 這個值決定。
```

### 變數宣告

``` js
var a = 1; 
let a = 1; // ES6 變數
const a = 1; // ES6  常數
```

ES6以前變數可以用 var 來宣告 ，ES6以後則多了 let 、const 來宣告。

## 變數的資料型別

- 基本型別(Primitives): `string 、number、boolean、null、undefined、Symbol。`
- 物件型別(Object): 除了基本型別以外，都是物件型別。

### String 字串

字串會用一組 '' 或 "" 包住， 兩者不可混用，意即用單引號開頭就要單引號收合。

``` js
var str = '這是一個字串';
var hello = 'Hello, ' + 'world'; // 字串相加
var hello = '第一行\
第二行\
第三行'; // 換行要用 \ 符號，\後方不得有空白。
```

es6 新增樣板字面值字串，由一組反引號 `` $ {} 組成，可帶入變數。

``` js
const name = '小名';
const str = `這是 ${name} 的家`; // 這是小名的家
```

### Number 數字

JS 中只有一種數值型別就是 Number， number 可以是整數或小數點或負數。

``` js
var a = 10 ;
var b = 12.5; 
let c = -2;
```

``` 
特殊數字
Infinity: 無限大  // 正數除以0
-Infinity: 負無限大 // 負數除以0
NaN: 不是數值(Not a number)
```

NaN 字面上來說不是數字，但若用 typeof 判斷型態，會得到 number
``` js
typeof NaN; // number`
```

NaN 與任何數字運算都會是 NaN，甚至是自己。

``` js
NaN === NaN // false;
```

可以用 isNaN() 來檢查一個變數是否為 NaN

``` js
isNaN(123) // false
isNaN('小名') // ture
isNaN('123') // false 因為字串 '123'，會透過隱含的 Number()轉成數字。
```

## Boolean 布林值

boolean 值只有兩種， true 以及 false，常用在判斷式當中。

## null 與 undefined

undefined 代表 此變數還沒有給值，所以不知道是什麼。

null 代表的是以前可能有或沒有值，但現在沒有值， 代表是一個空值。













