---
title: Express框架(1) 開啟web伺服器
date: 2022-07-11 16:13:59
categories: Node.js
tags: 
- Node.js
- Express
description: '用express開啟伺服器'
---

## 什麼是Express?

Express 這個套件主要幫忙解決許多node.js http server 所需要的基本服務，讓開發http service 變得更為容易，不需要像之前需要透過層層模組（module）才有辦法開始編寫自己的程式。

這個套件是由TJ Holowaychuk 製作而成的套件，裡面包含基本的路由處理(route)，http 資料處理（GET/POST/PUT），另外還與樣板套件（js html template engine）搭配，同時也可以處理許多複雜化的問題。

## 安裝express

在新專案裡 輸入 npm init 建立 package.json檔後，輸入

``` 
npm install express --save   // 安裝express 套件
```

## 建立web伺服器

![app.js](https://miro.medium.com/max/1400/1*-a7Jvq3IudAqXHKVJYVXKQ.png)

在js檔裡，先把express require()進來，並將express賦予到app變數上。

app.get: 第一個參數是路由，看前端是訪問哪個網址，第二個function則帶入req, res參數。

app.listen: 監聽個別的port。

## 404頁面設計

![404頁面](https://miro.medium.com/max/1236/1*WcOY6fVxz7hTrTSOot1xyQ.png)

使用app.all('*')來設計404頁面，不論使用者是發出 get 、post 、put 、delete請求，都會觸發app.all。並且使用 * 做為路由，代表不管使用者前往哪個路由都會觸發這個function。

