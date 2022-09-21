---
title: 2022-9-21-3-vue-router-matching
date: 2022-09-21 15:22:15
categories: Vue
tags: vue-router
description: 'vue-router 路由比對'
---

除了使用靜態路由 `/about` 或動態路由 `/users/:userId` 以外，vue-router 也提供了其他路由比對方式。

## 正規表達式

透過正規表達式來比對路由

``` js
const routes = [
  // /:orderId -> matches only numbers
  { path: '/:orderId(\\d+)' },
  // /:productName -> matches anything else
  { path: '/:productName' },
]
```

這樣只有 /25 會符合 /:orderId ， 非數字的路由則符合 `/:productName`。

## 重複的路由

當路由表裡有多個區段，都要對應同個元件時。例如 / 、 /user 、 /user/id。

可用 * (允許 0 個區段或多個) ， 或 + (允許一個以上的區段)

``` js
const routes = [
  // /:chapters -> matches /one, /one/two, /one/two/three, etc
  { path: '/:chapters+' },
  // /:chapters -> matches /, /one, /one/two, /one/two/three, etc
  { path: '/:chapters*' },
]
```

## 選擇性參數

當想要一個路由不管有沒有參數，都對應到同個元件時，可以用 ? 符號。

``` js
const routes = [
  // will match /users and /users/posva
  { path: '/users/:userId?' },
  // will match /users and /users/42
  { path: '/users/:userId(\\d+)?' },
]
```

