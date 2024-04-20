---
title: HTTP Networking(5) Http Headers
date: 2024-04-14 13:59:55
categories: HTTP Networking
tags: HTTP Networking系列
description: '介紹 Http Headers'
---

## 什麼是 http headers

http headers 可以讓 client 或 server 在每次 request 或 response 時附帶額外的資訊。
例如在網站登入時，常作為使用者的身分驗證使用。
http headers是由一對一對的 key value pair，組成，由冒號(:)隔開

常見的如:

- Content-Type: application/json => 傳輸資料的格式
- User-Agent:  Mozilla/5.0  => 用戶端的裝置
- Date: Wed, 21 Oct 2015 07:28:00 GMT => 傳輸資料的日期

## 使用瀏覽器工具

在瀏覽器的開發者工具中，可以找到 network 標籤，裡面記錄了整個網頁的網路活動，包括瀏覽器發出的 request 和收到的 response，還有整個資源請求所需的時間。

![](https://storage.googleapis.com/qvault-webapp-dynamic-assets/course_assets/STKdceG.png)

  