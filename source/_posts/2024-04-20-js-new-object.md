---
title: JS 基礎篇 (2) 物件、陣列及型別的判斷
date: 2024-04-20 14:53:26
categories: JS 基礎篇
tags: JS 基礎篇
description: "介紹 JS 的物件、陣列及型別的判斷"
---

## 物件 Object

一個物件可以是多種屬性的集合，用來記錄一組彼此有關係的資料，比如 person 會有姓名、工作、年齡等資料。
物件可以由 new 關鍵字建立，在新增屬性及方法

```js
let person = new Object();
person.name = "Lin";
person.job = "teacher";
```

或由 { } 直接建立並指定屬性，此種方法稱為【物件實字】

```js
let person = {
  name: "Lin",
  job: "teacher",
};
```

### 物件屬性存取

使用 . 來存取

```js
let person = {
  name: "Lin",
  job: "teacher",
};
person.name; // 'Lin'
```

當屬性的值帶有小數點、空格或是數字時可以使用 [ ] 來存取，記得要加上引號 (單引號或雙引號皆可) 

```js
let person = {
  name: "Lin",
  job: "teacher",
  1: "1",
  "$-小名家": "$-小名家 string",
};
person["name"]; // 'Lin'

// 也可以帶入變數取值
let a = "name";
person[a]; // 'Lin'

// 可以帶入數字取值
person[1]; // '1'

// 可以帶入字串取值
person["$-小名家"]; // '$-小名家 string'
```

### 可選串聯

如果不確定物件下是否有某屬性，而想取值時，可用 ? 可選串聯避免錯誤

```js
const obj = {
  inner: {
    name: "小名",
  },
};

obj?.inne?.name;
```

上面使用 ?，就算 inne 屬性不存在也不會報錯

### 屬性新增

若想為物件新增屬性的話，直接用 = 指定就可以了：

```js
let person = {
  name: "Lin",
};
person.job = "teacher";
person["age"] = 18;
```

### 屬性刪除

若要刪除屬性，則透過 delete 關鍵字刪除。

```js
let person = {
  name: "Lin",
  age: 18,
};
delete person.name;
delete person["age"];
person.name; // undefined
person["age"]; // undefined
```

另外要提到一點， js 裡變數無法被刪除，屬性才可以

```js
var a = 1;
b = 2;

delete a; // false
delete b; // true

console.log(a); // 1
console.log(b); // b is not defined
```

上面 a 是經過 var 宣告的變數，不可被刪除。b 沒有經過變數宣告，會直接成為全域物件 window 內的屬性，可以被刪除。

### 判斷屬性是否存在

當要判斷物件中存不存在某個屬性時，可檢查該屬性是否為 undefined。

```js
const obj = {};
console.log(obj.name); // undefined
```

或者用 hasOwnProperty() 或 in 來檢查

```js
let obj = {
  name: "nike",
};

// 用 in 檢查
console.log("name" in obj); // true
console.log("value" in obj); // false

// hasOwnProperty()
obj.hasOwnProperty("name"); // true
obj.hasOwnProperty("value"); // false
```

### 未定義的物件屬性預設值

當查找一個物件中不存在的屬性時，會回傳 undefined，並且物件中無法在不存在的屬性上新增值

```js
let obj = {
  name: "nike",
};
obj.ming; // undefined
obj.ming.name = "小名"; // cannot set property of undefiend
```

解決方法是新增一個 空物件再去設值

```js
let obj = {
  name: "nike",
  ming: {},
};
obj.ming.name = "小名";
```

另一種是無法一開始就確定結構時，直接指定屬性為物件。

```js
let obj = {
  name: "nike",
};
obj.ming = {
  name: "小名",
};
```

## 陣列

JS 的陣列可以看做是一種特別的物件，同一個陣列內可以是原始資料類型、另一個陣列、物件或是函式。與物件不同，陣列是有順序性的集合，所以只能透過[ ]加上索引來存取。

陣列可透過 new 關鍵字建立

```js
const a = new Array();
a[0] = "apple";
```

或是陣列實字的方式

```js
const a = [];
a[0] = "apple";
a[1] = "banana";

const b = ["a", "b", "c"];
```

### 陣列長度

陣列的長度可以用 .length 取得

```js
const ary = ["a", "b", "c"];
ary.length; // 3
```

也可以由 .length 來更改

```js
const ary = ["a", "b", "c"];
ary.length; // 3

ary.length = 1;
console.log(ary); // ['a'];

ary.length = 3;
console.log(ary); // ['a', undefined, undefined]
```

### 取得陣列項目

陣列的索引由 0 開始計算，也就是說要取得陣列的第一個元素，要用 array [0]來取得，如下:

```js
const ary = ["a", "b", "c"];
ary[0]; // 'a';
```

### 判斷是否為陣列

當用 typeof 來判斷一個陣列時，會得到 Object。但若真想判斷某變數是陣列而非物件時，用 isArray():

```js
Array.isArray([]); // true
Array.isArray(new Array()); // true
Array.isArray({}); // false
```

### 陣列方法

- 項目新增: 想要在陣列末端新增元素時，可以用 push()方法

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*JS3hzXSy8Pv_NWP6B2A3ew.png)

- 移除陣列末端項目 pop()

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*6oaf0gfytvS1ulr8Orh3Gw.png)

- 移除陣列前端項目 shift()

![](https://miro.medium.com/v2/resize:fit:750/format:webp/1*_6WT-fF4krbwpznDpppeyQ.png)

- 加入項目至陣列前端 unshift()

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*Z1MJlry1VWCyA6bKw5J6kg.png)

- 在陣列中尋找項目的索引值 indexOf

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*14aphYWL3L9gmu7I_8bmCQ.png)

- 移除指定位置項目 splice()

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*ifeD-029_JeQcCpCLJE7Dw.png)
