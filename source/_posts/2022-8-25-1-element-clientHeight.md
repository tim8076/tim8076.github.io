---
title: JS中元素的clientHeight、offsetHeight 與 scrollHeight
date: 2022-08-25 15:56:22
categories: Javascript
description: '解說元素的clientHeight、offsetHeight等等指的是什麼'
---

## clientHeight 與 clientTop

![](https://cdn-images-1.medium.com/max/1200/1*4fwuwle44US_DYi5lJo9WA.png)

- clientHeight: 元素包含padding但不包括 margin 、border、 水平滾動條的高度。單位為px、唯讀元素。

- clientWidth:  元素包含padding但不包括 margin 、border、 垂直滾動條的寬度。單位為px、唯讀元素。

- clientTop: 元素頂部邊框寬度單位為 px，可以理解為 border-top。如没有设置 border-top的值，则 element.clientTop 的值为 0

## offsetHeight 與 offsetTop

![](blob:https://medium.com/58fee995-a9c2-4324-9262-ddc7ce538e55)

- offsetHeight: 元素包含padding 、 border 、 水平滾動條的高度 但不包括 margin。

- offsetWidth: 元素包含padding 、 border 、 垂直滾動條的寬度 但不包括 margin。