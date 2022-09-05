---
title: Composition api (七) 使用 provide
date: 2022-09-03 16:40:06
categories: Vue
tags: Composition api
description: '用provide 傳遞資料'
---

## provide跨層級傳遞資料

要使用provide跟inject功能，可以先從vue解構出來

![](https://cdn-images-1.medium.com/max/1100/1*M-d8Q0BsFZoDwmORzDjHOQ.png)

![](https://cdn-images-1.medium.com/max/1100/1*CrhDwdhLPvCVH4ZeSDt1Vw.png)

在外層元件使用provide函式來傳遞資料，上圖將person這個物件傳出

``` js 
provide() // 第一個參數為provide名稱、第二個是provide要傳遞的值
```

![](https://cdn-images-1.medium.com/max/1100/1*D9mEqCpC_QNOZbPMZ7iPQg.png)

在內層元件使用 inject()來接收外層provide 傳來的資料，接受的名稱要和外層一致。
