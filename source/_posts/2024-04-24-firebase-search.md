---
title: Firebase 資料庫 (8) 資料搜尋區間與限制筆數
date: 2024-04-24 20:28:45
categories: Firebase
tags: Firebase 
description: '使用 startAt、endAt 搜尋資料區間'
---

## 搜尋資料區間

firebase 除了可以用 orderByChild 來排序資料以外，也可以加入搜尋區間的規則。

1. startAt ('值') : 在 值 以上
2. endAt('值') : 在 值 以下
3. equalTo('值'): 剛好等於值

![選出體重介於3500–4500的資料](https://cdn-images-1.medium.com/max/1000/1*SsUfAk9iWKLr4Zb24CGq8g.png)

![篩選出體重剛好是4000的資料。](https://cdn-images-1.medium.com/max/1000/1*TMRdOAbyz2DKZuSlI_iXYA.png)

## 限制筆數

假設今天想限制取出來資料的比數，可以用以下語法:

1. limitToFirst(筆數): 從資料前面取出指定筆數資料。
2. limitToLast(筆數): 從資料後面取出指定筆數資料。

今天有資料如下:

![](https://cdn-images-1.medium.com/max/1000/1*mCkSpixtI88Y91sLDxWz8Q.png)

![](https://cdn-images-1.medium.com/max/1000/1*3u4-FI6oVQCH1Q0WzWFn2A.png)

上面的例子會先篩選出weight大於3500的資料，在用 limitToFirst(1) 限制資料筆數為1筆，撈出結果如下。

![](https://cdn-images-1.medium.com/max/1000/1*xBf4MxCzrr94xIUmLilFvQ.png)

