---
title: JS 核心篇 (3) JS 的執行環境
date: 2024-04-17 11:35:24
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 的執行環境'
---

## 執行環境

![](https://cdn-images-1.medium.com/max/1000/1*__mmZCynRMxNwsHfGStYYg.png)

當我們宣告一個函式時，作用域就已經被確定，但此時還沒有變數產生。
當函式被執行，變數才產生，並產生一個`執行環境`，當函式反覆被執行，會產生多個`執行環境`。
`執行環境`會有限作用域的功能，並且有自己的this。

## 全域環境

除了函式有執行環境，全域也有全域執行環境。全域環境是在網頁一開啟或後端nodeJS一開啟就建立了。全域執行環境產生後會:
- 瀏覽器: 產生 window 變數，還有一個 this(等於 window)。
- nodeJS: 產生 global 變數， 還有一個 this(等於 global)。

## 執行堆疊

![](https://cdn-images-1.medium.com/max/1000/1*MN5_XRqtujvxGd8odbvZ7g.png)

當多個函式被執行時，依照執行的順序，執行環境會往上堆疊。

全域環境 =>  dosomething 環境 => sayHi 環境

當函式跑完後則依序離開

sayHi 環境離開 => dosomething 環境離開 => 回到全域執行環境






