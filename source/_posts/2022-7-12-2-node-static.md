---
title: Express框架(5) 靜態檔案
date: 2022-07-12 21:49:50
categories: Node.js
tags: 
- Node.js
- Express
description: '設定靜態檔案'
---

## 設定靜態檔案

靜態檔案泛指瀏覽器在呈現完整畫面時所需要的資源檔案，指的是伺服器端不需要去改變的檔案。
常見有的.js、.css、.jpg、.png等

在express中如果要載入靜態檔案如圖片、css檔案等，要在程式碼前面先指定靜態檔路徑: 

``` js 
app.use(express.static('public'))
```

上面程式中，我們將靜態檔案設定在public資料夾裡，這樣之後的靜態檔路徑就會從public開始抓

![](https://miro.medium.com/max/1400/1*kn1VKZekT892LH8V5YZsvg.png)

如上圖會去找/public/images/logo.png
