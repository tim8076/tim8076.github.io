---
title: Composition api (七) 使用 refs
date: 2022-09-03 16:30:42
categories: Vue
tags: Composition api
description: '用ref取得dom元素'
---

## 用ref取得dom元素

![](https://cdn-images-1.medium.com/max/1100/1*PAyK_UJg0U6WrVlYG5YNFw.png)

如上圖 app裡有兩個元素，都綁上ref的值，一個是card、一個是button

![](https://cdn-images-1.medium.com/max/1100/1*j5Gm06npbpzaAoK07i3OTw.png)

在setup裡用 btn = ref(null)的方式來取得dom元素，要記得變數名稱要和dom上綁的ref名稱一致。

![](https://cdn-images-1.medium.com/max/1100/1*ylqmdRjzY8z0Wj_Q1z3X3A.png)

在onMounted這個生命週期裡，就可以順利取得dom元素

![](https://cdn-images-1.medium.com/max/1100/1*pMN45Uvr0HyDoroahjRmNA.png)


