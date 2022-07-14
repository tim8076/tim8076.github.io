---
title: Express框架(3) 路由設計
date: 2022-07-11 16:49:43
categories: Node.js
tags: 
- Node.js
- Express
description: '設計應用程式路由'
---

## 設計路由(固定路徑)

![路由](https://miro.medium.com/max/1400/1*dZ1tIxswvDQ40zTICPcpUg.png)

我們可以設計像 '/user/edit-photo'、’/user/edit-profile’ 不同的路由，讓使用者來到user頁面後再去不同的頁面如edit-photo、edit-profile。


## 動態路由

![動態路由](https://miro.medium.com/max/1400/1*-X6TxEjNyQ0DPy5IMtVwaA.png)

有時候會在網址路徑後看到一串亂碼，那串亂碼就是專屬的序號內容，利用這個序號內容去資料庫撈出對應的資料。

## 取得動態路徑

![](https://miro.medium.com/max/1400/1*zxg6lOzZWL8c3ijWK-i7rw.png)

```
/route/:params  指定動態路由
req.params  取得動態路由
```

如上圖我指定動態路由是/:name，就可以用req.params.name將動態路由的值撈出來去資料庫做判斷。


![](https://miro.medium.com/max/1400/1*FSy3X_0YLDQWpzgGslbdPg.png)

路由裡也可以有多組params，如上圖我有 /:productID和 /:reviewID兩組params，req.params回傳後是一個物件，裡面是各個params的值。

![](https://miro.medium.com/max/990/1*DMxLXRpjJ1FHZjHqTcjrhg.png)

## query — 取得網址參數

![](https://miro.medium.com/max/1400/1*2igJn3maJXQnHbDaxlIjlA.png)

![](https://miro.medium.com/max/816/1*IBO0l0IXCUR2NpMfQ-ixYg.png)

```
req.query.參數名稱   取得參數的值
```

在網址中?後方代表的是query參數，在express中，可以用 req.query.參數名稱，來取得參數的值。

### query範例

![](https://miro.medium.com/max/1002/1*uLDTt5JDg1HpufIpz_J9AQ.png)

![](https://miro.medium.com/max/1400/1*si0clmAdnnJYOxd-dnBBOA.png)

上面範例中，先將 search跟 limit 從req.query解構出來後，再利用if判斷 search跟limit有沒有值，有的話就用search跟limit做資料過濾。

如果過濾完沒有值，就回傳空陣列，有值則回傳過濾後陣列。要注意 res回傳只能有一個，所以 前面判斷後的res要加上return。