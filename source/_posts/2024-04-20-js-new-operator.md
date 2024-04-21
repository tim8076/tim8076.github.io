---
title: JS 基礎篇 (3) 運算式與運算子
date: 2024-04-20 16:39:26
categories: JS 基礎篇
tags: JS 基礎篇
description: '介紹 JS 的運算式與運算子'
---

JavaScript 的語法基本上可以分為兩大類，「敘述句 (Statement)」 與 「運算式 (Expression)」。

- 敘述句 (Statement)：
簡單來說，敘述句就是執行某個動作。 像是變數的宣告、賦值，迴圈和 if 判斷式等等都可以被歸類於此。

- 運算式 (Expression)：
而運算式最大的特性，就是它會產生一個「值」。
像是我們在呼叫 function 時的參數 (arguments)，或者透過 = 賦值時，在 = 「右側」的部分都屬於運算式的部分。

## 算術運算子

JavaScript 各種運算子當中，最常見的就屬「算術運算子」了。簡單來說，算術運算子包括了大家所熟知的數學四則運算「加、減、乘、除」等。

### 加號 (+)

加號 + 的使用非常簡單，如果你想要表示 1 + 2 這個算式的話，可以這樣寫：

![](https://miro.medium.com/v2/resize:fit:580/format:webp/1*yv2Fb7hdT8YopTeai5YueA.png)

到目前為止還只是單純數字的狀況。 那麼，假設加號 + 兩側的其中一方，不是數字而是「字串」呢？

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*PX68pOqL44vQdON240yuHQ.png)

當加號 + 兩側的其中一方是字串的情況下，加號 + 會將兩者都視為「字串」連接在一起。也就是說，其中一方是字串，另一端會被「自動轉型」為字串後，連接在一起。

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*SrySdeJUtmSIy5nTuM9Yxw.png)

### 減號 (-)

再來是減號 -。 如同前面的加法一樣，如果只是單純的數字算式：

![](https://miro.medium.com/v2/resize:fit:606/format:webp/1*-IH0mAnn_q74Ge2drneqMw.png)

基本型別 (如 string 、 boolean 、 undefined 與 null)在做減法運算時，若其中一方屬於基本型別且不是數字的情況，那麼 JavaScript 會在先在背後透過 Number() 嘗試將數值轉為「數字」，再進行運算。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*_cF6n5xRjjuo_Y1wwlW1DA.png)

### 乘號 (*)

相較前面的加法、減法的規則，乘法運算子就單純許多。乘法運算子由一個「星號」 * 來代表，用來計算前後兩個數值的乘積。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*ZTtVdAcmmn3adiU_X58UQA.png)

如果有其中一個不是數字的話，那麼 JavaScript 就會先在背後以 Nubmer() 作轉換後再進行計算，如：

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*5n-6VcbFWf0lBlroT8O8jw.png)

### 除號 (/)

除法與乘法的規則類似。 除號在 JavaScript 用一個「斜線」/ 來表示。

![](https://miro.medium.com/v2/resize:fit:616/format:webp/1*qPiJH4-U4b-vDt0EwU5VRw.png)

如果有其中一個不是數字的話，那麼 JavaScript 就會先在背後以 Nubmer() 作轉換後再進行計算。

### 取餘數 (%)

除了基本的四則運算之外，JavaScript 也有取餘數的運算子，以「百分比符號」 % 來表示。使用方式與除號類似，但得到的值是除法運算後的「餘數」：

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*oTTmoNXHKKamjTNyrBuAZg.png)

與除法一樣的是，如果有其中一個不是數字的話，那麼 JavaScript 就會先在背後以 Nubmer() 作轉換後再進行計算。


## 遞增 ++ 遞減 --

當變數遇到了++ 就會+1 如 a++

a = a+1

當變數遇到了 -- 就會 -1 如 a--

a = a-1

## 相等＝＝ 與全等 ＝＝＝

在２個等號＝＝的情形下，數值會自動轉型，如下：

＂１０＂ ＝＝ １０ // true

字串的１０被自動轉型成數字，所以兩邊相等。

三個等號不會自動轉型，所以

＂１０＂ ＝＝＝ １０ // false

只會在雙方的數值與型態都相同的情況下回傳 true。

所以盡量用 ＝＝＝ 取代 ＝＝

## 不等於！＝ 與 ！＝＝

！＝ 會自動轉型

！＝＝不會自動轉型

## 指派運算子

在 JavaScript 中，指派運算子用於將值賦給變數。除了簡單的賦值 = 之外，還有一些複合指派運算子，如 +=、-=、*= 等等。這些運算子允許您對變數的值進行運算並將結果賦給同一個變數。

以下是 JavaScript 中常見的指派運算子：

1. 賦值運算子 (=)：將右側的值賦給左側的變數。
`var x = 10;`
2. 複合指派運算子：將運算結果賦給左側的變數。
- +=：加法指派
`x += 5; // 相當於 x = x + 5;`
- -=：減法指派
`x -= 5; // 相當於 x = x - 5;`
- *=：乘法指派
`x *= 2; // 相當於 x = x * 2;`
- /=：除法指派
`x /= 2; // 相當於 x = x / 2;`
- %=：取餘指派
`x %= 3; // 相當於 x = x % 3;`

## 逗號運算子

在 JavaScript 中，逗號運算子（,）用於將多個表達式連接在一起，並按照從左到右的順序依次求值。

以下是逗號運算子的用法和示例：

1. 在變數聲明中使用：在聲明變數的同時，可以使用逗號運算子定義多個變數。
```js
var a = 1, b = 2, c = 3;
```
2. 在函數調用中使用：可以在函數調用時使用逗號運算子傳遞多個參數。
```js
myFunction(param1, param2, param3);
```
3. 在表達式中使用：可以在表達式中使用逗號運算子串聯多個表達式，並返回最後一個表達式的結果。
``` js
var x = (1 + 2, 3 + 4); // x 等於 7，先計算 (1 + 2)，然後計算 3 + 4，返回 7
```
4. 在迴圈中使用：可以在迴圈中使用逗號運算子來執行多個操作。
```js
for (var i = 0, j = 10; i < j; i++, j--) {
    // do something
}
```

## 邏輯運算子 (Logical Operator)

- 「&&」：
當 && 左右兩側的值同時為 true 時，則會得到 true 的結果。 若其中一方是 false 的情況下，則得到 false 。

- 「||」：
當 || 左右兩側的值只要有一方為 true，則結果為 true。 只有在兩側皆為 false 的情況下才會得到 false 。

- 「!」：以一個 ! 驚嘆號來表示，原本是 true 的結果經過 ! 轉換後會得到 false，而 false 會變成 true。 所以你可能會看到很多人用 !!xxx 來取代 Boolean(xxx)，透過兩次的「NOT」操作，即可判斷某數值 Boolean 轉換後的結果。

``` js
var result = true && false; // result 為 false
var result = true || false; // result 為 true
var result = !true; // result 為 false
```

&& 和 || 所回傳的值不一定是布林值，而是兩者其中之一。
&& 和 || 再做判斷時，會先對左邊的值檢查:

1. 如果是 Boolean 類型就再作後續判斷，若不是就會透過 ToBoolean 判斷是 falsy 或 truthy 來轉換成對應的 true 或 false。

``` js
expr1 && expr2 : 如果expr1 為假值，就回傳 expr1，否則回傳 expr2

expr1 || expr2 : 如果expr1 為真值，就回傳 expr1，否則回傳 expr2
```
![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*i1OT9EqwLLC1prlADlh71A.png)

## Truthy 與 Falsy

邏輯判斷中，為 false 的並非真的為 false 這個值；而被判定為 true 的也並非為這個值，因此我們給他 Falsy(假值) 與 Truthy(真值)

Falsy 有 null、undefined、0、NaN、””(空值) 以及 false。

這裡只要記住 Falsy 有哪些就好了，其他都為 Truthy。
