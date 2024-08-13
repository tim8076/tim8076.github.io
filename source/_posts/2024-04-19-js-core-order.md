---
title: JS 核心篇 (8) 優先性與相依性
date: 2024-04-19 13:48:44
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 優先性與相依性'
---

## 優先性與相依性

![](https://cdn-images-1.medium.com/max/1000/1*Roo2ukmpSROdWPKbZuT34g.png)

```js
var a = 2 * 2 + 3 * 3;
```

- 優先性: 上面程式中，因為 * 號的優先性比 + 號大，所以會先將 乘法運算完後，兩者在相加。

- 相依性: 運算子的執行方向， * 號跟 + 號的執行方向是由左至右，等號則是由右至左，將右邊的值賦予到左邊。

詳細可參考[此網站](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Operator_precedence)

``` js
console.log(3 > 2 > 1); // false;
```
上面程式會先執行 3 > 2 結果為 true;
再執行 true > 1， true 因為型別轉換結果為 1， 1 沒有大於 1 ，所以結果為 false。

``` js
var a = 1;
var b = 2;
a = b = 3;
console.log(a, b); // 3, 3
```

上面程式中，因為等號是由右至左執行

```
a 取到的值是 3 賦予到 b 所回傳的結果，並不是直接取 b 的值。
也就是說因為 b = 3 是一個表達式，執行完後會得到 3；
a 再取到 3 這個值。
```

當有賦值行為時，因為 = 是表達式，會回傳賦予的值。

```
a = 'QQ'
那麼回傳的就是 QQ。
```









