---
title: Mongoose (2) 建立model與schema
date: 2022-07-17 14:26:39
tags:
- Mongoose
description: '建立model與schema'
---

## Mongoose 觀念與名詞

Mongoose 提供了 schema-based 的解決方案讓我們直接操作資料，在透過 Mongoose 操作資料庫時，有幾個名詞要先有概念:

- Schema: 存資料庫模型的檔案
- Model: 由 Schema 當參數產生的 instance 可以用來操作資料庫
- collection: 在 MongoDB 中的表

## Mongoose Schema 設計

要使用 Mongoose 操作的第一步就是要從定義 Schema 開始，定義完成後 Schema 會自動對應到 MongoDB 中的一個 collection，另外因為不像傳統資料庫那樣有 join 的概念，所以拿資料的時候可以依照我們的使用情境去設計，像是以撈取為主的話就可以透過雙向參照的設計去加速，詳細可以參考MongoDB Schema 設計指南。

## 建立 Schema

![](https://miro.medium.com/max/842/1*kzEelgX6y-K3JF6dTMFElA.png)

![](https://miro.medium.com/max/1400/1*DkN-K-S-ONv16m1V4wFJAQ.png)

在model資料夾裡，建立js檔，並利用 monggose.Schema({})，來建立所有document的結構。只有在 Schema 裡建立的屬性如 name，才會傳入mogodb資料庫。

建立好 Schema 結構， 在將schema建立成一個model實體 可以用來操作資料庫(crud)。

``` js
module.exports = mongoose.model('Product', productSchema);
```

## schema 拆分

![](https://miro.medium.com/max/1376/1*MTktN8cHSR_vVoz5N_yWhA.png)

當要定義的物件過於複雜時，可以另外拆分一個schema來定義，如上圖address的值是定義在 addressSchema裡。

## schema 驗證

![](https://miro.medium.com/max/1400/1*Tzl9Vg6A_Z4nPDE3KumAHw.png)

schema 裡資料格式的也可做驗證，可用方法:

- type: String | Number | Boolean | Date  // 指定屬性的型別 
- required: true | false  //是否必填
- trim: true | false  //是否去頭尾空白
- maxlength: 最多字數。
- min: 最小值。
- max: 最大值。
- default: 預設值。
- lowercase: true | false  //是否要小寫
- uppercase: true | false  //是否要大寫
- immutable:  true | false  //是否可修改

補充日期預設方法:

``` js
createAt: {
  type: Date,
  default: () => Date.now(), // 每次建立物件時，會給新的日期。
}
```
validate: 自訂驗證函式(validator)，並可回傳message

![](https://miro.medium.com/max/1400/1*A_uOjCJwU-B83LJsIYYnpw.png)

## schema 加上方法
我們可以在 schema加上方法，讓每個new出來的document使用。

``` js
const person = new mongoose.Schema({
  name: {
    type: String,
  },
})
person.methods.sayHi = function() {
  console.log(`Hi My name is ${Kyle}`)
}
```
方法建立在schema可以在每個實體使用

``` js
const person = await person.find({ name: 'Kyle' }); 
person.sayHi(); // Hi My name is Kyle
```
## model操作資料

![](https://miro.medium.com/max/1362/1*we3LBZ7EKHPeN3mNiXkhXA.png)

在我們controllers裡的js檔裡，可以將剛才export的model引入。

![](https://miro.medium.com/max/1164/1*RwDqw3zkTCV5XXHAdgOzLw.png)

上面是post方法對應的函式，可以使用 Task.create()方法，將使用者傳來的資料，建立成一筆 document。詳細的Model操作方法下一章節介紹。


