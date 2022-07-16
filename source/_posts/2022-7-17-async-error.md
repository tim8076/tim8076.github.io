---
title: Express框架(10) async-errors 套件
date: 2022-07-16 14:11:10
categories: Node.js
tags: 
- Node.js
- Express
description: '使用async-errors 套件處理promise'
---

## async-errors 套件

以往在使用async await 語法時，時常會用try catch處理非同步事件

``` js
try {

} catch (err) {

}
```

在express專案裡可以載入 async-errors 套件來取代try catch

``` 
npm install express-async-errors --save
```

## 使用方法

首先在 app.js 裡載入套件

``` js
require('express-async-errors');
```

然後當有錯誤發生時，在router函式裡可以直接丟出Error錯誤

``` js
const getAllProductsStatic = async (req, res) => {
  throw new Error('testing async errors');
  res.status(200).json({ msg: 'Product testing route'});
}
```

在app.js的最後則可用一個處理錯誤的middleware來承接錯誤

``` js
app.use(async (err, req, res, next) => {
  console.log(err)
  return res.status(500).json({ msg: 'Something went wrong, please try again' })
});
```