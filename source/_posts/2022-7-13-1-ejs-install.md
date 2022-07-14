---
title: Express框架(6) EJS樣板語言
date: 2022-07-13 10:57:54
categories: Node.js
tags: 
- Node.js
- Express
description: '介紹與安裝ejs樣板'
---

## EJS 介紹

EJS 的全名是「Embedded Javascript」，顧名思義就是內嵌式的樣板引擎，可以將邏輯與內容直接嵌入到 HTML 頁面上，也就是 EJS 可以讓我們利用 JavaScript 生成 HTML 頁面 。

## 替 Express 加入 EJS

首先要先來安裝 EJS 套件進入專案，這邊選用 [ejs-locals](https://www.npmjs.com/package/ejs-locals) 這個鄉民開發的套件，因為正版ejs有些功能較缺乏。

![](https://miro.medium.com/max/1400/1*gfvzeVND9wZ-5HET2qaaKg.png)

``` js
app.engine() // 指定我們要用的樣板引擎是ejs。
app.set('views', './views')  //設定views資料夾，存放所有ejs樣板檔案。
app.set('view engine', 'ejs') // 告訴express要用ejs樣板來跑。
```

## 新增 ejs 檔案

![](https://miro.medium.com/max/788/1*GVlx6DfG7W4l9SMN9UOcAg.png)

![](https://miro.medium.com/max/1400/1*q-nTWNurcyFK6D3LeObr6w.png)

在view資料夾下，新增不同頁面的 ejs檔案。

![](https://miro.medium.com/max/1400/1*RvhXzYdnc6cshoJ3NhS3Zg.png)

在app.get裡，可以用res.render()來指定要渲染的ejs檔案，這邊不用加副檔名.ejs，因為在app.set時已經指定渲染樣板為ejs。

