---
title: JS 基礎篇 (4) 自動轉型
date: 2024-04-20 21:23:44
categories: JS 基礎篇
tags: JS 基礎篇
description: '介紹 JS 的自動轉型'
---

## 自動轉型的規則

JS 在運算與比較的過程中，常會為兩側的數值做自動轉型。
在兩個等號的 == 的比較運算式下，若雙方資料類型不同時，會「自動轉型」。
規則如下:

``` js
// 其中一個值為 Boolean 的情形下，true 轉型為數字 1，false 轉型為數字 0
1 == true // true
0 == false // true

// 字串與數字做比較時，將字串透過Number()轉型為數字後比較
1 == '1' // true

// 其中一方為物件時，另一方為基本型別時，會透過物件的 valueof 取得對應的基本型別的值後比較
// 定義一個自定義的物件
var myObject = {
  valueOf: function() {
    return 5; // 返回基本型別的值
  }
};

// 將物件與基本型別進行比較
console.log(myObject == 5); // 輸出: true
console.log([10] == 10) // true
console.log(['a'] == 'a') //true
console.log({ 'A': A } == 'A'); // false {'A': A } 被轉換為字符串 "[object Object]"

```

## 數值的大於 > 與 小於 <

在 JavaScript 中，當使用大於 > 或小於 < 的比較運算符時，如果兩側的值不是同一種類型，JavaScript 會嘗試將它們轉換為相同的類型，然後再進行比較。這種自動轉型的過程被稱為類型轉換或類型強制轉換。

下面是一些類型轉換的規則：

1. 如果兩側都是字符串，則直接比較字符串的 Unicode 字符序列。
2. 如果一側是字符串，另一側是數字，則將字符串轉換為數字後進行比較。
3. 如果一側是布爾值，則將布爾值轉換為數字後進行比較（true 轉換為 1，false 轉換為 0）。
4. 如果其中一側是物件，會先使用 valueOf 方法嘗試轉換為基本型別值，如果 valueOf 返回的不是基本型別值，則使用 toString 方法轉換為字符串後進行比較。
5. 如果以上都不符合，則會返回 false。

``` js
console.log(5 > "3");      // 輸出: true，"3" 被轉換為數字 3
console.log("10" < 5);      // 輸出: false，"10" 被轉換為數字 10
console.log(true > 0);      // 輸出: true，true 被轉換為數字 1
console.log(false < 1);     // 輸出: true，false 被轉換為數字 0
console.log({} > null);     // 輸出: false，{} 被轉換為字符串 "[object Object]"，null 被轉換為數字 0
console.log([] > []);       // 輸出: false，兩個空陣列都被轉換為字符串 ""，然後比較字符串的 Unicode 字符序列，相等返回 false
```
