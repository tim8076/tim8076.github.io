---
title: Composition api (一) setup取代option
date: 2022-09-03 15:07:47
categories: Vue
tags: Composition api
---

![](https://cdn-images-1.medium.com/max/1100/1*g_Xxrt6tkYtSxDIui2irAw.png)

![](https://cdn-images-1.medium.com/max/1100/1*T-bYsCjFfbFxiY3isQs7Ig.png)

## 使用setup取代option

和以往option api 程式邏輯被拆分到各處不同，在composition api 裡，我們將程式都寫在setup裡。

![](https://cdn-images-1.medium.com/max/1100/1*V7_oID5_6cWdv1TxxIRbiA.png)

- ref: 定義資料使用，要取出資料加上.value

- function: 定義函式相當於以前的methods。

- return: 資料、方法都要 return，才能在畫面上使用。
