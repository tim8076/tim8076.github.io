---
title: Express框架(7) EJS Layout
date: 2022-07-13 11:09:55
categories: Node.js
tags: 
- Node.js
- Express
description: '使用ejs layout'
---

## 設定樣板

我們可以新增一個 layout.ejs 作為樣板頁面使用，layout裡加入 `<%- body %>` 語法，會將其他ejs檔內容匯入。

![](https://miro.medium.com/max/1400/1*HCMrT2xXSlDbGgThg-E0FA.png)

在其他ejs上，只須加上一行 `<% layout('樣板檔案名稱') %>`，就可將樣板帶入。

![](https://miro.medium.com/max/930/1*uI6xlmXBCNH-7o0Ro_NxFg.png)


## 路由導入參數

![](https://miro.medium.com/max/1320/1*n9MNv2VOt634BqoBPeFmTw.png)

在res.render裡面第一個參數是指定ejs樣板，第二個參數則可帶入一個物件，裡頭是要選染的變數資料。

![](https://miro.medium.com/max/1400/1*MEchuM--HhsuN16kiVua_g.png)

``` ejs
<%= 變數名稱 %>  // 將參數當作純字串渲染
<%- 變數名稱 %>  // 將參數當作html渲染
```

## 流程判斷

在ejs裡，也可加入if else的判斷，假設我有一個show的變數

![](https://miro.medium.com/max/1090/1*g2OO40_Q_po6b1qZW3PEGw.png)

在ejs裡一樣可以用 <% %>在裏頭寫邏輯判斷

![](https://miro.medium.com/max/908/1*SJVRG_Rem5uq7Aihpgb_Mw.png)

假設show是true則渲染內容，false則不渲染。

## 列表渲染

ejs也可以渲染陣列，假設有一個course陣列如下:

![](https://miro.medium.com/max/1108/1*eqFjWH00H2lzsN12qE2sTw.png)

在ejs裡一樣可以用 for 語法去渲染陣列出來

![](https://miro.medium.com/max/1152/1*TWV9_MNkwNTjiJcBaz2Q4Q.png)



