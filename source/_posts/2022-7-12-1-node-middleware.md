---
title: (7) Node.js Middleware
date: 2022-07-12 16:10:32
categories: Node.js
tags: 
- Node.js
description: '介紹其他Middleware運作'
---

## Middleware 概念

Middleware 像水管一樣可以串聯在一起，所有的 Request 及 Response 都會層層經過這些水管。
用圖例可以很容易理解，如下圖：

![middleware](https://miro.medium.com/max/1200/0*6JyVusGg4jQkcBJw.png)


## App.use

在express中，使用app.use作為類似守門員的角色，app.use就像一層一層的水管，當程式符合條件，才會執行next()，進到下一個funciton。

![app.use](https://miro.medium.com/max/1400/1*ZG8cv5Yke-HB8ZdEx0oUoQ.png)

## 404路由設定

![404](https://miro.medium.com/max/1400/1*tdatSPLTGHYNUeRLNnEzNA.png)

當今天使用者輸入錯誤網址，應該要回傳404頁面。像上圖，當使用者輸入 /user ，那沒問題會進入user頁面。

但如果輸入錯誤，可以使用app.use，來回傳res.status(404)，並且send一個404提示頁面給使用者看。如果是程式有問題則可回傳res.status(500)。

## middleware 位置

middleware寫的位置也可不同，以下介紹不同的寫法:

### 寫在參數內

middleware也可以寫在路由函式的第二個參數，當使用者進入'/user'後，就會進入守門員 middleware，當通過next()後，才會跑最後的function。

![寫在第二個參數](https://miro.medium.com/max/1400/1*eIOZrfAsK9x2Ey328D1wxQ.png)

### 加入多個middleware

加入多個middleware，可以用陣列方式

![多個middleware](https://miro.medium.com/max/1400/1*9IjEP7363kE6HV1ZgHI8GA.png)

### 加入所有router

上圖中，我們是手動將logger加入路由中，但當今天路由很多時，無法一一加入，可以用app.use(middleware)，一次將middleware加入所有頁面。

![加入所有router](https://miro.medium.com/max/1400/1*-18WRu76rnoT2zAaDQyObw.png)

當有多個middleware要加入時，可以用陣列方式加入，陣列裡的順序會影響middleware的執行順序。

![加入多個](https://miro.medium.com/max/1328/1*QXP-U-OUPfYuBOMyqT9B8Q.png)

### 加入指定路徑的路由

![](https://miro.medium.com/max/948/1*tArClOuxGOqWKeursFf5NQ.png)

app.use()，第一個參數可加入指定路徑，如上圖只要路徑是/api開頭的都會被加上middleware，如 /api/about、/api/products

![](https://miro.medium.com/max/1216/1*H0R6d3NsPCX423vN5NZT3A.png)


## express內建 middleware

在express中，已經內建了許多 middleware，如之前學過的express.static()

![](https://miro.medium.com/max/908/1*eQ0DKpqLRQ2rIXcShoOwxg.png)

