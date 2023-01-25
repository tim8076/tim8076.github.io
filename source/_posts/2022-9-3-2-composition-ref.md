---
title: Composition api (二) reactive 與 ref
date: 2022-09-03 15:23:51
categories: Vue
tags: Composition api
description: '使用reactive與 ref 定義資料'
---

## reactive定義資料

![](https://cdn-images-1.medium.com/max/1100/1*SdlSgQtLZc3-11s1o_pXxQ.png)

在vue3裡要定義雙向綁定的資料，可以用reactive方法，reactive基本上就是一個proxy物件，帶入的參數一定要是物件。

要修改物件的值，可以用 person.name 的方式來修改。

![](https://cdn-images-1.medium.com/max/1100/1*NOBpSjy6lqEqoayTvw4GTg.png)

使用reative時盡量使用const宣告，如果像上圖使用let宣告後，再去賦予person成一個新的物件時，就會失去雙向綁定的功能。

## ref 定義資料

![](https://cdn-images-1.medium.com/max/1100/1*A_cirZ994ZMmm6N3jrtrhg.png)

我們也可以用ref來定義雙向綁定的資料，如上圖我們定義了num = 1這個資料。

``` js
num.value  // 用.value 來讀取或修改 ref 的值。
```

除了定義純值以外，也可定義物件

![](https://cdn-images-1.medium.com/max/1100/1*fUnxj_qNyfwHIb8wSWfjHw.png)

上圖定義了person 為一個物件，要調整或讀取物件的值時

``` js
物件.value.name  // 先用.value 讀取到物件，再用.name 讀取到物件的屬性
```

![](https://cdn-images-1.medium.com/max/1100/1*MRGXPNfkIAtWOoL-ISIZZA.png)

和reactive不同，我們可以用.value = 新物件 的方式，來將原本的物件替換掉，也依然保有雙向綁定的功能。

## reactive與 ref 如何選擇

![](https://cdn-images-1.medium.com/max/1100/1*rb-oWwlZ-Q8IWAJgPniDCA.png)

用reactive建構的資料本身就是proxy物件，本身會有一個Handler來監控target也就是資料，當target有變動時，Handler就會介入來進行畫面的渲染

![](https://cdn-images-1.medium.com/max/1100/1*GDB2jgjjgJb1PvmuSxWZqg.png)

用ref定義的資料是一個 RefImpl物件，這個物件包含

``` js
rawValue: 原始值
value: 給外層存取的值
```

物件裡一樣有一個handler函式，當value被修改或讀取時，handler會介入來渲染畫面，並寫一份新的值回rawValue裡，好處是value不一定是proxy物件，一樣可用純值來存取。

## 實戰中的選擇

實戰中ref是比較好用且不會出錯的方法，使用 ref 定義的資料用.value來存取資料，不會有被物件覆蓋而失去雙向綁定的問題。