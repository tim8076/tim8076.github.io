---
title: JS 建構函式
date: 2022-08-17 14:06:48
categories: Javascript
description: '使用建構函式產生物件'
---

![](https://miro.medium.com/max/1330/1*plHyXH3Pw_nJME6HKoZCBw.png)

在 JS 中可以用一個函式建構式作為原型的藍圖，並利用this的方式，將函式的參數綁定在自己身上。以上圖為例，this.name 就是在 Dog() 裡面新增 name 屬性，而他的值就是 new Dog 傳進的 ‘比比’

若要將藍圖轉為實體，必須透過 new 這個運算子:

``` js
function Dog(name) {
  // const this = {}
  this.name = name;
  // return this
}

const dog = new Dog('mimi');
```

當使用 new 運算子建立物件時，實際上會先建立一個 this 的空物件，綁定屬性到 this物件上後，再回傳this物件。


``` js
function Person() {
  this.age = 12;
}

const me = new Person();

console.log(me.age) // 12

Person.prototype.age  // undefined
```

另外建構函式裡的 this 的值，只會綁定在 new 出來的物件實體中，並不在建構函式本身的property裡面。
所以我們會將每個物件不同的屬性用 this 來綁定，而每個物件共用的方法，則用 Prototype 的方式建立如下

``` js
function Person(name) {
  this.name = name;
}

Person.propotype.run = function () {}
Person.propotype.talk = function () {}
```

## 在藍圖上新增方法

在 Dog 這個函式物件中，我們可以找到特有的屬性 Prototype，透過Prototype所建立的屬性，就會變成原型上的方法。

以下我們在 Dog這個藍圖中，利用 Prototype 建立 bark()這個方法。

![](https://miro.medium.com/max/904/1*JPXBzFA0j9XfE2fFVSXMHg.png)

因為透過藍圖產生的不同物件，其原型是同一個建構函式，所以當我們在原型中新增方法時，就可以同時套用至所有產生的物件。好處是能減少記憶體

## 純值的包裹物件

在 JS 中新增純值時，會帶有包裹物件，

包裹物件會有特定的方法可以取用，如下圖

![](https://miro.medium.com/max/824/1*_ZWf6dKEo9HFxRP2b8n38w.png)

![](https://miro.medium.com/max/546/1*G766dfSEg775Y4pmHy_jTg.png)

也可以在包裹物件中，新增自定義 prototype 方法

![](https://miro.medium.com/max/1068/1*DWkNiANU1gO6prqXYOKQIA.png)


## prototype

``` js
function Person(name) {
  this.name = name;
}
const me = new Person('Sina');

me.prototype // undefined
Person.prototype // { contructor: f }
```
用建構式製造的物件實體，並沒有 prototype，  prototype 屬性是在原本的建構函式上。

``` js
me.__proto__ === Person.prototype // true;
```

物件實體有的是 __proto__ 屬性，和建構函式的 prototype 是一樣的。

