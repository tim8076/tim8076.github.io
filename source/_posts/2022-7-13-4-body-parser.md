---
title: Express框架(8) body-parser
date: 2022-07-13 21:00:19
categories: Node.js
tags: 
- Node.js
- Express
description: '使用body-parser處理表單資料'
---

## body-parser 是什麼？

body-parser 是 Express 經常使用的中介軟體，用於解析請求的資料(body)，比如說：POST 一筆 JSON 格式的資料到我們的 Express App，這時可以透過 body-parser 快速解析這筆資料，以方便取用。下方的圖為 Express 的運作模型，可以看到 body-parser 會先進行資料的解析，才會把解析後的資料傳給其他相關的 middleware 使用。

![](https://miro.medium.com/max/1400/0*8sAI6T1cahPoR-e6.png)

## 使用 body-parser

在express4的版本已經內建body-parser的功能，所以直接使用即可:

``` js
const express = require('express');
const app = express();

app.use(express.json());  // 解析json格式
app.use(express.urlencoded({ extended: false })); // 解析表單資料
```

## 表單設計

![](https://miro.medium.com/max/1196/1*XUZu72p4jof3Tk6jZl6xOg.png)

在Form標籤上，action的路徑代標資料會傳到哪，method則選用post代表將資料送出到後端。

![](https://miro.medium.com/max/1156/1*xn-Ao4WJiGUQEVJh2uRRDw.png)

在app.js中，可以設計app.post去接收前端表單的資料，第一個參數'/searchList' 也就是前端表單的action路徑。

接收到的req.body會是一個 json格式，key值就是前端input所指定的name。

## Redirect 跳轉頁面設定

![](https://miro.medium.com/max/1240/1*Ky3EZaP8KjIveIpTp7b7eA.png)

當我們收到前端傳來的表單資料後，並將資料處理完後，就可以用

res.redirect(‘路由’)將網頁導回 指定頁面。