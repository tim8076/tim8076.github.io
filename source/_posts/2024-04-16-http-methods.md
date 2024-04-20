---
title: HTTP Networking(7) http methods
date: 2024-04-16 11:14:10
categories: HTTP Networking
tags: HTTP Networking系列
description: 'http-methods 介紹'
---

## http methods

HTTP methods 是用來告訴伺服器，現在我們想對資料庫進行哪種操作，包含了 GET, POST, PUT, or DELETE 等方法。
這些方法會對應到 CRUD 四種不同的動作。

- Create: POST 方法
- Read: GET 方法
- Update: PUT 方法
- Delete: DELETE 方法

就像使用者操作社群平台貼文一樣，他們會 新增、修改、刪除、讀取貼文，而那正是 CRUD 對資料庫做的事。

## Status code

![](https://cdn-images-1.medium.com/max/1000/1*lceTqptlcG5bO41b1KHZyg.png)

- Errors: 當client端向server發出 http request 出錯時，會出現 error。
          例如: url 錯誤、網路斷線。
- Status code: 當http request成功送到伺服器，但伺服器端有錯誤時，會在 response 中用 status code 回應。
               例如: 沒有權限取得資料，伺服器掛掉。
               
以下是常見的 Status code

1. 200: OK 一切正常
2. 201: Created. 資源成功建立，通常用在 POST request
3. 301: Moved permanently. 請求的資源已經移到別處，例如網址更改。
4. 400: Bad request. 前端http request 發生錯誤
5. 401: Unauthorized. 請求權限不足，例如少了 api key。
6. 404: Not found. 請求的資源不存在
7. 500: Internal server error. 伺服器錯誤。

## GET methods

http get 方法可從 server 取回特定資料的 copy，並不是真的將資料從 server 拿出，而僅是該資料當下狀態的 copy 而已。
通常認為 get 是安全的，因為並不會更改或刪除資料庫裡的資料。

以下為使用 fetch() api ，送出 get request

``` js
await fetch(url, {
  method: 'GET',
  mode: 'cors',
  headers: {
    'sec-ch-ua-platform': 'macOS'
  }
})
```

fetch() api，第二個參數可傳入物件，以下為物件可能的值。

- method: The HTTP method of the request, like GET.
- headers: The headers to send.
- mode: Used for security, we'll talk about this in future courses.
- body: The body of the request. Often encoded as JSON.

## POST methods

post 方法會傳資料給 sever，通常會在資料庫中新增一筆新的資料。
在 fetch() api中，會將資料放在body後傳送給後端。

``` js
await fetch(url, {
  method: 'POST',
  mode: 'cors',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(data)
})
```

## PUT methods

送出 PUT 方法後，有兩種情況
1. 若後端已經有此筆資料，就更新該筆資料
2. 若後端沒有這筆資料，建立該筆資料

POST 和 PUT 的差別是，POST只建立資料， PUT 則是更新或建立資料。
另一個差異是，PUT 對後端是沒有重複影響的，當我送第一次PUT給後端時，後端更新該筆資料，當我送同樣的PUT到後端時，沒有影響。
POST 則是你送幾次請求，就在後端建立幾個新的資料。

``` js
await fetch(url, {
   method: 'PUT',
   mode: 'cors',
   headers: {
   'Content-Type': 'application/json'
   },
   body: JSON.stringify(data)
})
```

## PATCH method

Patch 和 put 不同的是， put 是更新整筆資料， Patch 則是更新部分資料。
Patch 沒有 PUT 那麼常用，很多後端 server 選擇使用 put 即使你只要更新部分資料。

## DELETE method

DELETE 方法用來刪除指定的資料

``` js
const url = 'https://api.boot.dev/v1/courses_rest_api/learn-http/locations/52fdfc07-2182-454f-963f-5f0f9a621d72'

await fetch(url, {
  method: 'DELETE',
  mode: 'cors'
})
```





