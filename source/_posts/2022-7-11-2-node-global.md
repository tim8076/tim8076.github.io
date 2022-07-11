---
title:  (3)  Node.js Global全域物件
date: 2022-07-11 13:18:04
categories: Node.js
tags: 
- Node.js
description: '了解node.js裡的全域物件'
---

## Global 全域物件

在js中有 window 這個全域物件，我們可以將變數賦予到window上存取，我們稱為全域變數。

![window](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071103.png?alt=media&token=e0e1c0f6-8781-4730-b61b-7361b9e60446)

在 node.js中也有 Global 全域物件，我們將 global console出來會發現global內也有許多預設的功能。

![global](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071105.png?alt=media&token=8fe2bec8-2284-4917-a8a5-487630b0eb4e)

## 在global上新增變數

和window一樣，我們也可將變數賦予到 global 上

``` js
global.a = 1;
console.log(a);
```

![a賦予到 global](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071106.png?alt=media&token=9c5107fe-7d60-4bdc-aa03-701075ff6d83)


## global的變數作用域

![變數作用域](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071107.png?alt=media&token=4129e4f2-53df-4ec2-a84b-8a77b3080717)

在每隻js裡宣告的變數，只會在那隻js裡有效，無法在global內被存取。如果想存取到global上，要寫 `global.a = 1` 的方式。這和在winddow能直接繼承用var宣告的變數不同。




