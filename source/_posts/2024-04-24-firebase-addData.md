---
title: Firebase 資料庫 (6) 新增、刪除資料
date: 2024-04-24 14:58:48
categories: Firebase
tags: Firebase 
description: '使用 push、remove 新增、刪除資料'
---

## push 新增資料

firebase中新增資料可以用 push 語法

![](https://cdn-images-1.medium.com/max/1000/1*Lj_oiCxolhEon7gyO2jouw.png)

上面例子中，先選取todos的資料位置後，再用push語法新增一筆物件進去

![](https://cdn-images-1.medium.com/max/1000/1*r-Q7UQ1tFWHEqkE0Bw8Epw.png)

新增完後，在todos裡的每個物件都會有一個隨機id，作為區分資料用。

## child 指定路徑

在firebase裡指定路徑除了用 `.ref('路徑')`以外，也可以用 `.child()`

![](https://cdn-images-1.medium.com/max/1000/1*3brTEjA3oACFFsOxQJf6XQ.png)

上面代表先指定到ref()根目錄，在指定到根目錄下一層的todos資料。

## remove、child - 移除資料

![](https://cdn-images-1.medium.com/max/1000/1*gDRzebZUUhnE8ghhLlEvbw.png)

移除資料可以用remove()，上面例子中先指定todos裡的 -MpeDcD0TbFwIjQajj -資料，再用remove()做刪除。
