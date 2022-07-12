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