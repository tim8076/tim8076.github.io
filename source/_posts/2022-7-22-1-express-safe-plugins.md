---
title:  Express框架(13) 安全處理套件
date: 2022-07-22 15:19:11
categories: Node.js
tags: 
- Node.js
- Express
description: '介紹處理安全問題的套件'
---

這篇介紹幾個常用的 安全性套件如下

```
npm install helmet --save   // helmet藉由設定多個http-header來保護app
npm install cors --save     // cors允許跨域的網路請求
npm install xss-clean --save  // 防止xss攻擊
npm install express-rate-limit  // 防止太頻繁的請求
```

![載入套件](https://cdn-images-1.medium.com/max/1320/1*iiglV8mBgWLo9fmYK2f2kQ.png)

![使用套件](https://cdn-images-1.medium.com/max/1320/1*PXV7BHiBXv1zxakGrrVfSg.png)

