---
title: ES6 解構賦值
date: 2022-07-05 16:43:10
categories: Javascript
tags: 
- ES6
description: '解構賦值是一個在ES6的新特性，用於提取(extract)陣列或物件中的資料'
---

## 傳統陣列賦值方式

![傳統傳統賦值](https://miro.medium.com/max/1348/1*WRcYmXNDmWXhrmOBVYS34Q.png)

以往作法我們會將 family 裡的值一一取出，在分別賦予到新的變數上。

## 陣列解構賦值

![陣列解構](https://miro.medium.com/max/1330/1*KVVs3jLuIIJLivh1ni2xnA.png)

將右方 family 的陣列資料，鏡射到左方的陣列中，如此左方陣列裡的變數就可以被賦予family陣列裡的值。

若鏡射時左右數量不同，則剩下的值不會做解構賦值，如下圖，老媽、老爸就不會作賦值。

![陣列解構](https://miro.medium.com/max/1318/1*DWgYoQQAPpEH_tUejL1ujg.png)

若左方陣列有空白，則空白會被跳過，不會被賦值。

![空白跳過](https://miro.medium.com/max/1314/1*rTlQeB9E5esDJJQKr5vJBg.png)

## 字串解構

字串也可以用類似陣列的手法，進行解構賦值。

![字串解構](https://miro.medium.com/max/1100/1*YIo9Qm5uJ2rHAFPOd3o3dw.png)

## 物件解構

![物件解構](https://miro.medium.com/max/932/1*W0aj9nt9dyVof6E0vQiQeg.png)

我們可以 利用一個 { } ，取出右方GinyuTeam物件裡Ginyu屬性的值，

賦予到 Ginyu這個變數上。

![物件解構](https://miro.medium.com/max/952/1*jzBRrM81reRf7TMxA6rfQw.png)

也可以賦予 Ginyu 一個新的變數名稱 kobe，此時 kobe就被賦予Ginyu的值。

## 預設值

![預設值](https://miro.medium.com/max/1184/1*xJW3YCVIfO6gx1zapA8sOg.png)

我們也可以使用預設值的方式，當左方變數沒有被右方賦值時，就使用預設值

## 範例

![物件解構](https://miro.medium.com/max/982/1*ryzueSCVtqdlplZdq8u-pg.png)

將 GinyuTeam 用…拆出裡面的值，再放到新的 { }中，然後再將這個物件，賦予到 newTeam，此時 newTeam和GinyuTeam是兩個不同物件。

## 解構加展開

解構和展開也可以同時使用

``` js
const people = {
  Ming: {
    name: '小名',
    age: 18
  },
  Jay: {
    name: '杰倫',
    age: 35,
  },
  Bob: {
    name: '包柏',
    age: 16
  }
}

const { Ming, ...others } = people;
```

如上，Ming 會被單獨解構， Jay 跟 Bob 則會被一起解構到 others 物件。





