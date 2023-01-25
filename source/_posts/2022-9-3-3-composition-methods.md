---
title: Composition api (三) Methods
date: 2022-09-03 15:44:50
categories: Vue
tags: Composition api
description: '在Composition api中定義方法'
---

## 如何定義方法

![](https://cdn-images-1.medium.com/max/1100/1*DG0Xtfl9EOVnfo3atdVUqg.png)

在composition api裡，如果要定義方法，直接在setup裡用function或箭頭函式來定義即可，記得這些方法也要用return匯出。
另外如果有資料不需要匯出到畫面，可以不用ref來定義。

