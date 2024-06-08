---
title: JS 核心篇 (8) 物件的原型鍊與繼承
date: 2024-04-30 12:38:31
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 物件的原型鍊'
---

## 原型鍊

javascript是一門基於原形的物件導向語言，透過原形的繼承可以讓本來沒有某個屬性的物件去存取其他物件的屬性。

## 指定原形關係

在js裡，我們可以透過 Object.setPrototypeOf ，來指定物件間的原形關係

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*BgXiOk3A6Q5_X4gN6oDxeg.png)

透過 setPrototypeOf， spiderman就繼承了superman的 superPower的屬性，透過 in 可以判斷 superPower屬性存在 spiderman裡。

但在原形繼承裡，同一個物件無法同時繼承兩個原形物件，假使再新增一個 lightman，並用setPrototypeOf指定屬性light給 spiderman，原本的superPower屬性就會消失。

![](https://miro.medium.com/v2/resize:fit:750/format:webp/1*dqunA4axz1fpjSRhpZicAg.png)

如果想讓spiderman同時繼承 superman跟 lightman的能力，可以利用原形鍊的觀念，當一個物件要去存取不存在的屬性時，會往原形物件去查找。

讓 spiderman 去繼承 superman，superman再去繼承 lightman，如此spiderman就同時繼承 superman跟 lightman的能力。

![](https://miro.medium.com/v2/resize:fit:750/format:webp/1*bGKUnyzQx5F9FdFsCRZerA.png)

[範例](https://codepen.io/tim-chou/pen/WNOooBv?editors=1011)

### 最頂層的原形物件: Object.prototype

如原型鍊的觀念，當一個物件要去存取不存在的屬性時，會往原形物件去查找，那找到何時才會停止呢 ?

答案是 Object.prototype，最頂層的物件，也是所有物件的起源。也就是說Object.prototype 所有的方法，在javascript裡的所以所有物件都可以使用。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*_cOIW52aFJ1fMLnCFyMqfA.png)

## Object.create 繼承方法

除了上面介紹的 Object. setPrototypeOf，來指定物件的原形以外，也可透過Object.create來指定原形關係。

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*abe-94jNq0DrTZ5kbtvXnw.png)

首先定義一個物件作為原形，然後透過Object.create建立一個新的物件，此時新物件的prototype就會是那個原形物件。