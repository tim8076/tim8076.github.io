---
title: (4) Node.js require、module exports 模組設計
date: 2022-07-11 13:44:03
categories: Node.js
tags: 
- Node.js
description: '在node.js裡拆分模組'
---

## 匯入匯出

在node.js如果想讀取或匯出不同js檔案的資料，可用:

``` js
module.exports = data;  // 匯出資料
const data = require('./data');  // 匯入資料
```

![匯入匯出](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071108.png?alt=media&token=d3064ea4-4ab5-43a0-b915-1a5a5d20a434)

如上圖，我們在 data.js裡用module.exports匯出資料，並在 app.js裡用 require 匯入。

## 匯出整筆物件

若有多筆資料要同時匯出，也可將資料放到物件裡同時匯出:

![匯出物件](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071109.png?alt=media&token=d4e53e3c-1b7a-4ec8-b8ed-8e095399cd7d)


 
