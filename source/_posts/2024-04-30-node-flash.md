---
title:  Express框架(16) 後端傳送提示訊息
date: 2024-04-30 14:37:06
categories: Node.js
tags: 
- Node.js
- Express
description: '使用 connect-flash 傳送提示訊息'
---

## 情形

有時候會從後端傳送暫存的提示訊息給前端，比如前端姓名欄位沒填，傳送請填寫姓名的資訊給前端。此時可用 `connect-flash` 套件。

## 安裝套件

```
npm install --save connect-flash
```

## 使用方式

因為 connect-flash 是將資料存在 session，所以express要先載入 cookieParser 跟 session

``` js
const flash = require('connect-flash');
const session = require('express-session');
const cookieParser = require('cookie-parser');

app.use(cookieParser);
app.use(session({
  secret: 'keyboard cat', 
  resave: false,
  saveUninitialized: true
}));
app.use(flash());
```

因為有設定 flash 這個 middleware，所有路由都可以使用 req.flash() 功能。

``` js
// 將資料存入 flash
app.get('/flash', function(req, res){
  // Set a flash message by passing the key, followed by the value, to req.flash().
  req.flash('info', 'Flash is back!')
  res.redirect('/');
});

// 將 flash 的資料渲染到頁面上
app.get('/', function(req, res){
  // Get an array of flash messages by passing the key to req.flash()
  res.render('index', { messages: req.flash('info') });
});
```
