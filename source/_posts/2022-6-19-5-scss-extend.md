---
title: (6) SCSS練功坊-extend
date: 2022-06-19 16:50:49
categories: scss
tags: 
- scss
description: '使用 extend 合併重複的樣式'
---

## 合併樣式

當我們有一段樣式常常用到，可以用@extend來將樣式合併在一起。

使用 % +class 撰寫要合併之樣式，並用@extend 來載入樣式。

![extend](https://miro.medium.com/max/1220/1*E5-ebZ9tVXeHmwf4i4uN2w.png)

![編譯後](https://miro.medium.com/max/1134/1*gUgESgMLa1DmyLz94Rp9Rw.png)

## Mixin與extend的使用時機

基本上來說，
@mixin是將程式碼帶入到對應的class去，同時可帶入變數。
@extend則是藉由class合併，並吃到共通樣式，但沒辦法帶入變數。

所以如果你的樣式都固定不變的，不會需要用參數帶進去改變樣式的話，
那就用@extend，程式碼會比較少些。

但如果你的程式碼需要帶入多個變數進行運算時，
那用@mixin則較適合。

