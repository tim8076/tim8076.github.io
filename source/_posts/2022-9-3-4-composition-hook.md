---
title: Composition api (四) 使用Options API 的方法
date: 2022-09-03 15:53:05
categories: Vue
tags: Composition api
description: '在Composition api中使用Options API 的方法'
---

## 使用生命週期

官方文件中有說明 Composition API 中的生命週期有哪些：

![](https://cdn-images-1.medium.com/max/1100/1*K0LpszKEUHPCxfdPGEEWuA.png)

基本上 beforeCreate跟created兩個hook已經被整合到setup裡，所以我們在setup裡定義的資料就等於在 created裡定義。

要使用生命週期函式，首先將生命週期的函式從vue裡解構出來。

![](https://cdn-images-1.medium.com/max/1100/1*UTEoiSULVLsBWDfKrfMJDg.png)

在生命週期hook裡帶入一個function來撰寫程式。

![](https://cdn-images-1.medium.com/max/1100/1*chxC3xO_Q8mETcQMgqFbvA.png)

## 使用 computed

![](https://cdn-images-1.medium.com/max/1100/1*tGf-ehBAk1y5xIvggUw_KQ.png)

首先從vue解構 computed 出來。

![](https://cdn-images-1.medium.com/max/1100/1*Cy_fKTUjUH-5tYtAqR0uBA.png)

使用方法和option api 類似，一樣需要將處理完的資料回傳出來，如上圖newValue 是 計算完的資料。

![](https://cdn-images-1.medium.com/max/1100/1*fmGf5y5yBMMr6vNk-6_hjw.png)

computed一樣可使用 get 和 set 的形式，這邊改為傳入一個物件，裡頭有get跟set 函式。

