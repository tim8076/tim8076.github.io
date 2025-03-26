---
title: json-server (1) 介紹資料庫設計
date: 2024-11-27 16:24:53
categories: json-server
tags: json-server
description: '介紹 json-server 資料庫設計'
---

## 基礎說明

json-server 是一個輕量級工具，可以快速建立一個基於 JSON 資料的 RESTful API，常用於開發階段進行前端測試，模擬後端 API 提供資料。以下是如何使用 json-server 與相關功能的介紹：

## 安裝

```
npm install json-server
```

##  建立 JSON 資料檔案

創建一個 JSON 檔案（例如：db.json），作為模擬數據的資料庫。例如：

``` json
{
  "users": [
    {
      "id": 1,
      "name": "偉杰"
    },
    {
      "id": 2,
      "name": "Mary"
    }
  ],
  "posts": [
    { "id": 1, "title": "json server", "userId": 1},
    { "id": 2, "title": "json server-2", "userId": 1},
    { "id": 3, "title": "json server-3", "userId": 2}
  ],
  "comments": [
    { "id": 1, "text": "a comment about post 1", "postId": 1, "userId": 1 }
  ]
}
```

json 檔案建立後，啟動伺服器

```
json-server --watch db.json
```

## 取得資料

啟動後，json-server 自動生成以下 RESTful API：

- GET /posts：獲取所有文章。
- GET /posts/1：獲取 ID 為 1 的文章。

### 取得單一資料的關聯資料

- GET /posts/1/comments

上面路徑能取得文章 1 中的所有 comments 資料。

- GET /posts/1/comments?_expand=user

上面路徑能在 comments 資料中帶入 user 資料。

### expand 關聯資料

```json
{
  "posts": [
    { "id": 1, "title": "Post 1", "authorId": 1 },
    { "id": 2, "title": "Post 2", "authorId": 2 }
  ],
  "authors": [
    { "id": 1, "name": "Author 1" },
    { "id": 2, "name": "Author 2" }
  ]
}
```

使用 /posts?_expand=author，可以在 posts 資料中，用 author 來尋找外層 authors 資料表，並將author 資料帶入，得到如下資料:

```json
[
  {
    "id": 1,
    "title": "Post 1",
    "authorId": 1,
    "author": {
      "id": 1,
      "name": "Author 1"
    }
  },
  {
    "id": 2,
    "title": "Post 2",
    "authorId": 2,
    "author": {
      "id": 2,
      "name": "Author 2"
    }
  }
]
```

## 新增資料

- POST /posts：新增一篇文章

body 帶入

```json
{
  "body": "新增文章1",
  "userId": 2
}
```

- POST /posts/1/comments: 在 文章1中新增一筆留言

```json
{
  "body": "新增留言1",
  "userId": 2
}
```

## 篩選功能

JSON-SERVER 也提供篩選功能，以下資料為例:

```json
{
  "products": [
    {
      "name": "A產品",
      "price":500,
      "language":{
        "zh-tw":"A產品",
        "en-us":"A product"
      },
      "id": 1
    },
    {
      "name": "B產品",
      "price":100,
      "language":{
        "zh-tw":"B產品",
        "en-us":"B product"
      },
      "id": 2
    },
    {
      "name": "C產品",
      "price":900,
      "language":{
        "zh-tw":"C產品",
        "en-us":"C product"
      },
      "id": 3
    }
  ],
}
```

透過在路由加上參數的方式可以篩選出對應資料

```js
// 篩選 name 屬性為 A產品的商品
http://localhost:3000/products?name=A產品
```

多個篩選條件可以用 & 連接

```js
// 篩選 name 屬性為 A產品，且 price 為500的資料
http://localhost:3000/products?name=A產品&price=500

// 篩選 id 屬性為 1 或 2 的資料
http://localhost:3000/products?id=1&id=2
```

物件深層的資料也可以篩選，用點記號指定

```js
// 篩選 language 物件裡，en-us屬性值為 A product 的產品
http://localhost:3000/products?language.en-us=A product
```

若不確定屬性名稱，也可以用 q 用來執行全文搜尋，會在 JSON 資料中所有的屬性中進行模糊比對。

```js
//。篩選出 關鍵字帶有A產品的資料
http://localhost:3000/products?q=A產品
```

## 分頁功能

在使用 json-server 時，內建了分頁功能，可以通過 _page 和 _limit 兩個參數實現分頁效果。

- _page:
  - 指定顯示的頁碼。
  - 預設值為 1。

- _limit：
  - 指定每頁顯示的資料筆數。
  - 預設值為 10。

```js
// 回串第二頁的資料，每頁5筆
http://localhost:3000/resource?_page=2&_limit=5
```

## 排序功能

在 json-server 中，可以使用 _sort 和 _order 參數對資料進行排序。這些參數提供了基於指定屬性的升序或降序排列資料的功能。

- _sort：
  - 指定用於排序的屬性名稱。
  - 支援單一屬性或多個屬性（用逗號分隔）。

- _order：
  - 指定排序方式。
  - 可選值：
  - asc：升序排列（小到大或字母順序），為預設值。
  - desc：降序排列（大到小或字母逆序）。

```js
將 price 屬性照降序排列方式排序
http://localhost:3000/products?_sort=price&_order=desc
```