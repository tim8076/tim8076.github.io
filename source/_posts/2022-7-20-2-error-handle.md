---
title: Express框架(12) 錯誤處理範例
date: 2022-07-20 15:10:33
categories: Node.js
tags: 
- Node.js
- Express
description: '規劃錯誤處理的方法'
---

## 前言

在node.js裡遇到錯誤時我們可能會直接丟出錯誤

``` js
throw new Error('testing async errors');
```
在這章節會介紹如何統整不同錯誤的api在一個資料夾，方便管理。

## 新增errors資料夾

```
- errrors
  - index.js
  - custom-api.js
  - bad-request.js
  - not-found.js
- middleware
  - error-handler
```

首先在根目錄建立errors資料夾，底下會有處裡不同錯誤的js檔，以下分別說明

## custom-api

``` js
class CustomAPIError extends Error {
  constructor(message) {
    super(message)
  }
}
module.exports = CustomAPIError
```

建立 custom-api.js 檔，裡面我們會 extend 一個 CustomAPIError 的 class ，再將 CustomAPIError 匯出。

## 建立不同錯誤的js

當我們建立好 CustomAPIError 後，可以新增不同錯誤的js檔，以下以 Badrequest 錯誤為例:

``` js
const { StatusCodes } = require('http-status-codes');
const CustomAPIError = require('./custom-api');

class BadRequestError extends CustomAPIError {
  constructor(message) {
    super(message);
    this.statusCode = StatusCodes.BAD_REQUEST;
  }
}

module.exports = BadRequestError;
```

Badrequest 一樣會extend CustomAPIError ，statusCode的部分則會用'http-status-codes'這個套件帶入錯誤代碼。


## index.js

當不同錯誤的js檔建立好了，可以再新增 index.js統一匯出，這樣之後要使用不同錯誤方法時，可以統一由index這邊匯入。

``` js
const CustomAPIError = require('./custom-api')
const UnauthenticatedError = require('./unauthenticated')
const NotFoundError = require('./not-found')
const BadRequestError = require('./bad-request')

module.exports = {
  CustomAPIError,
  UnauthenticatedError,
  NotFoundError,
  BadRequestError,
}
```

## 使用方法

要使用錯誤方法時，可以先將要用的方法從index.js匯入使用，再將錯誤拋出。

``` js
const { BadRequestError, UnauthenticatedError } = require('../errors');
throw new BadRequestError('Please provide email and password');
```

## error middleware

當錯誤拋出後，會進到 error-handler 的 middleware 處理

``` js
const { CustomAPIError } = require('../errors')
const { StatusCodes } = require('http-status-codes')
const errorHandlerMiddleware = (err, req, res, next) => {
  let customError = {
    statusCode: err.statusCode || StatusCodes.INTERNAL_SERVER_ERROR,`
    message: err.message || 'Something went wrong try again later'
  }
  return res.status(customError.statusCode).json({ msg: customError.message });
}

module.exports = errorHandlerMiddleware
```

errorHandlerMiddleware 函式接收的 err 參數如果是我們自行丟出的會有 statusCode 和 message，我們就回傳customError的資訊。若不是則回傳預設的  StatusCodes.INTERNAL_SERVER_ERROR 。












