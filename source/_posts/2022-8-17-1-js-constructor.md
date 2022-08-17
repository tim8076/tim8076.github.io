---
title: JS 建構函式
date: 2022-08-17 14:06:48
categories: Javascript
description: '使用建構函式產生物件'
---

![](https://miro.medium.com/max/1330/1*plHyXH3Pw_nJME6HKoZCBw.png)

在 JS 中可以用一個函式建構式作為原型的藍圖，並利用this的方式，將函式的參數綁定在自己身上。以上圖為例，this.name 就是在 Dog() 裡面新增 name 屬性，而他的值就是 new Dog 傳進的 ‘比比’

若要將藍圖轉為實體，必須透過 new 這個運算子，創造一個新的空白物件，並連結回原本的函式建構式，再將新產生物件的this 綁定在函式之上。

![](https://miro.medium.com/max/1400/1*NKTq194Iry-MevyisZwzVw.png)

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



