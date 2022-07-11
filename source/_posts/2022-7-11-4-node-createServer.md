---
title: (5) Node.js 內建模組 createServer
date: 2022-07-11 14:10:59
categories: Node.js
tags: 
- Node.js
description: 'createServer內建模組'
---

## 內建模組 createServer

在 node.js 中有許多內建模組，其中 createServer 可以用來開啟個web伺服器。

![createServer](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071110.png?alt=media&token=7ce0ed04-70e6-405b-99c2-fab0e7782e73)

上圖中，我們用`require('http')`，將http模組引入。引入後，用http模組的createServer功能開啟伺服器。並在createServer()裡帶入一個函式，並傳入兩個參數 request， response。

- request: 代表前端發出的請求的詳細資訊
- response: 代表伺服器要回傳的資料

![req, res](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071111.png?alt=media&token=db5e0f66-5d26-473d-a617-3ab8cd50d137)

我們用 response.writeHead()撰寫表頭資料，response.write()寫回傳的內容，response.end()代表結束。最後用listen()來監聽port。




