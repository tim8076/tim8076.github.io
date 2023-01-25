---
title: Composition api (五) 使用props
date: 2022-09-03 16:08:19
categories: Vue
tags: Composition api
description: '在setup裡使用props'
---

## 在setup裡使用props

![](https://cdn-images-1.medium.com/max/1100/1*41Q9b6dQDvcuaPINKG44EQ.png)

![](https://cdn-images-1.medium.com/max/1100/1*yzRMFpYrCTmCX_NEffri2w.png)

今天有一個card元件如上，我們想在外層傳入person這個物件到card元件裡

![](https://cdn-images-1.medium.com/max/1100/1*MiGnt4S1V8WIaWdVs1THLg.png)

在card元件裡，可以用props來接收外層傳入的prop，在setup裡會將props當作參數傳入，這個參數是包含所有props的物件，要讀取個別prop可以用物件解構的方式。

``` js
const { name } = props // 取出name的個別prop值
```

但要注意解構出來的值只有第一層有雙向綁定

![](https://cdn-images-1.medium.com/max/1100/1*SqY8TLQGR4uaz0_zN1MIEw.png)

如果解構第二次的值是沒有雙向綁定的特性，如上圖的name。
要解決這個問題，可以用ref來取出第一次解構的值。

![用ref定義item.name](https://cdn-images-1.medium.com/max/1100/1*zhypvjFf0rrWnlQu808-Qg.png)