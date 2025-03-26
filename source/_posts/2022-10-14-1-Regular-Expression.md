---
title: JS-正則表達式
date: 2022-10-14 10:27:15
tags: 正則表達式
description: '用於確認字串是否符合所定義的規則'
---

## 什麼是正則表達式

正則表達式(RegExp , regular expression) 用於確認字串是否符合所定義的規則。在 JavaScript 中，正規表達式也是物件，這些模式在 RegExp 的 exec 和 test  方法中，以及 String 的 match、replace、search 、split 等方法中被運用。

## 建立正規表達式

可透過下列兩種方法去建立一條正規表達式：

正規表達式字面值: 使用斜槓表示開始及結束。

``` js
const re = /ab+c/;
```

或呼叫 RegExp 物件的建構函式，如下：

``` js
var re = new RegExp('ab+c');
```

在進入規則語法之前，先介紹正則表達式的一個簡單的測試方法 test( )。test ( ) 方法用以表示參數字串是否符合正則表達式的字串格式。

## 撰寫正規表達模式

- 使用簡易模式

直接匹配 / / 內的字符，比如：/abc/ ，會符合僅僅字符 'abc' 同時出現並按照這個順序的情形。

- 使用特殊字元

如果需要更多條件的匹配，比如搜尋一或多個 'b'，或者搜尋空格，會需要特殊字元的字符。

### 符合格式

- ^ : 字串開頭須符合字串格式

``` js
const exp = /^ab/; 

exp.test('abc') // true
exp.test('cab') // false
```

- $ : 字串結尾須符合字串格式

``` js
const exp = /ab$/; 

exp.test('abc') // false
exp.test('cab') // true
```

- \d : 代表任意數字，也等同於 [0~9] 反之，\D 代表除了數字以外的字元，也等同於 [^0~9]

``` js
const exp = /\d/; 

exp.test('abc') // false
exp.test('a23') // true
```

- \w : 代表所有字母、數字及底線，也等同於 [A-Za-z0-9_] ；\W 代表除了所有字母、數字及底線以外的字元，也等同於 [^A-Za-z0-9_]

``` js
const exp = /\w/; 

exp.test('a23_') // true
exp.test('?') // false
```

- \s : 匹配任何空白字符，包括空格、製表符、換行符等。

```js
input.replace(/\s+/g, ' ').trim(); // 過濾多個空白字符到剩下一個
```

### 匹配單一字元或字串

- \[ ] 字元集合: 匹配括號內的任意單一字元:
  - /[bee]/ 等價於 /[bee]/，它會匹配以下任何一個字元：b、e。
  - 它無法實現匹配整個字串 'bee' 或 'ebb' 的功能。

- ( ) 群組: 用來表示多個字串的選項。
  - /(bee|ebb)/ 是正確的，匹配 'bee' 或 'ebb' 作為整體字串。
  

### 符號

- | : 符合前後任一值即可

``` js
const exp = /a|b/; 

exp.test('aac') // true
exp.test('ddd') // false
```

- -: 連字符，代表連續的字符，如 數字 1 - 3 可以寫成 [1-3]，英文 a-z 寫成 [a-z];

``` js
const exp = /[1-3]/; 

exp.test('2') // true
exp.test('5') // false
```
### 修飾符

- g 修飾符：欲使比較對象爲字串全部時可以加上 g 修飾符，否則在一般狀況下可能只比較第一個符合的對象就停止了。

- i 修飾符：表示比較條件不分大小寫

``` js
const exp = /HELLO/i;
console.log(exp.test('hello')); // true 
```

### 出現次數

- {n} : 使用大括號指定次數，{n} 只有一個數字代表指定次數；{n,m} 兩個數字時，代表介於 n~m 次；省略其中一個數字代表只指定下限或上限，例如 {n,} 代表至少 n 次，{,m} 代表低於 m 次。

``` js
const exp = /a{2}/; 

exp.test('aab') // true
exp.test('a') // false
```

- \* : 匹配前一字元 0 至多次。

``` js
const exp = /b*/; // 0個或多個b

exp.test('bbb') // true
exp.test('ccc') // true
```

- ? : 匹配前一字元 0 至 1 次。

``` js
const exp = /b?/; // 0 個或 1 個 b

exp.test('bbb') // false
exp.test('ccc') // true
```

- \+ : 匹配前一字元 1 至多次。

``` js
const exp = /b+/; // 1個或多個b

exp.test('bbb') // true
exp.test('ccc') // false
```

## 字串方法

- match(): 回傳比對後符合的結果陣列，若無符合對象，回傳 null

``` js
const string = 'hello world';
const exp = /\w/g;

string.match(exp); 
//  ['h', 'e', 'l', 'l', 'o', 'w', 'o', 'r', 'l', 'd']
```

- search()：回傳搜尋第一個比對後符合結果的位置，如果沒有任何符合結果，就回傳 -1;

``` js
const string = 'hello world';
const exp = /h/;
const exp2 =/\d/;

string.search(exp);  // 0
string.search(exp2); // -1
```

- replace(): 替換比對後符合的值。接收兩個參數，第一個參數爲正則表達式，第二個參數爲欲替換的值。

``` js
const string = 'hello world';
const exp = /\d/;
const exp2 =/\w/;

string.replace(exp, 'a'); // 'hello world'
string.replace(exp2, 'a'); // 'aello world'
```

如果要比對全部就加上 g 

``` js
const exp3 =/\w/g;
string.replace(exp3, 'a'); // 'aaaaa aaaaa'
```




