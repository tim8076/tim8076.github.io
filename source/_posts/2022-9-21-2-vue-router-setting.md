---
title: vue-router (2) 動態路由
date: 2022-09-21 14:36:04
categories: Vue
tags: vue-router
description: 'vue-router 動態路由'
---

## 動態路由

vue-router也提供動態路由功能，透過 URL 的動態路徑來讓不同的 URL 路徑都能指向同一個 Vue 元件實體。

假設有一個 User 的元件，必須依照 userId 不同，來渲染不同內容，可以這樣做:

``` js
const User = {
  template: '<div>User</div>',
}

// these are passed to `createRouter`
const routes = [
  // dynamic segments start with a colon
  { path: '/users/:id', component: User },
]
```

現在，/users/johnny 和 /users/jolyne 都會指向同一個元件。 

路由上的參數會以 `:` 的方式呈現。在每個 user 元件內，則可使用 `this.$route.params` 來取得參數的值。

``` js
const User = {
  template: '<div>User {{ $route.params.id }}</div>',
}
```

若有路由有多個參數，則分別在 $route.params 以不同的key來讀取。

```
/users/:username/posts/:postId   路由

{ username: 'eduardo', postId: '123' }  $route.params
```

## 參數改變時的回應

當使用者從 /users/johnny 轉到 /users/jolyne 頁面時， User 元件會被重複使用，因為兩個路由指向的是同一個元件。但這也代表 User 的生命週期並不會被重複觸發。

要在參數改變時做出回應時，可以用 watch 來監聽 `$route.params`。

``` js
const User = {
  template: '...',
  created() {
    this.$watch(
      () => this.$route.params,
      (toParams, previousParams) => {
        // react to route changes...
      }
    )
  },
}
```

或使用 `beforeRouteUpdate()` 路由守衛的函式。

``` js
const User = {
  template: '...',
  async beforeRouteUpdate(to, from) {
    // react to route changes...
    this.userData = await fetchUser(to.params.id)
  },
}
```









