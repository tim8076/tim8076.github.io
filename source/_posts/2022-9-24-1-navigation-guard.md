---
title: vue-router (9) 導航守衛
date: 2022-09-24 11:18:21
categories: Vue
tags: vue-router
description: '使用導航守衛'
---

vue-router 提供了路由的導航守衛，讓我們可以在變更路由的前後 去自動調用它們。

分別提供了 「全域」、「路由」、「元件內」三種不同的導航守衛供使用。

## beforeEach (全域)

我們可以註冊全域的導航守衛 `router.beforeEach`，這樣當「每一個」路由要進入之前，都會先經過這裡：

``` js
const router = createRouter({ ... })

router.beforeEach((to, from) => {
  // ...
  // explicitly return false to cancel the navigation
  return false
}
```

每個導航守衛的函式都接收三個參數:

- to: 即將進入的路由。
- from: 從何處進入的路由。

我們可以在這個 callback 函式裡面執行任何動作，例如身份驗證等等。

``` js
router.beforeEach(async (to, from) => {
  // canUserAccess() returns `true` or `false`
  const canAccess = await canUserAccess(to)
  if (!canAccess) return '/login'
})
```

## afterEach (全域)

和 beforeEach 相反，afterEach會在路由跳轉後觸發，適合用來搭配網頁分析等功能。

``` js
router.afterEach((to, from) => {
  sendToAnalytics(to.fullPath)
})
```

## beforeEnter(路由)

和 beforeEach 不同，beforeEnter是註冊在 route 路由表的物件內，可以依照每個路由的不同需求來決定是否註冊。

``` js
const routes = [
  {
    path: '/users/:id',
    component: UserDetails,
    beforeEnter: (to, from) => {
      // reject the navigation
      return false
    },
  },
]
```

### 元件內的 hooks

我們也可以在元件內部定義 導航守衛，共可分為三種

- beforeRouteEnter
- beforeRouteUpdate
- beforeRouteLeave

``` js
const UserDetails = {
  template: `...`,
  beforeRouteEnter(to, from) {

  },
  beforeRouteUpdate(to, from) {

  },
  beforeRouteLeave(to, from) {

  },
```

### beforeRouteEnter

在 beforeRouteEnter 中無法取得 this，因為元件的實體還沒被建立。但可以在 next中取得 this。

``` js
beforeRouteEnter (to, from, next) {
  next(vm => {
    // access to component public instance via `vm`
  })
}
```

### beforeRouteUpdate

在 beforeRouteUpdate 和 beforeRouteLeave 裡可以直接取用 this。

``` js
beforeRouteUpdate (to, from) {
  // just use `this`
  this.name = to.params.name
}
```

### beforeRouteLeave

 beforeRouteLeave 常用來防止使用者在未儲存資料時就離開此頁面。
 
``` js
beforeRouteLeave (to, from) {
  const answer = window.confirm('Do you really want to leave? you have unsaved changes!')
  if (!answer) return false
}
```






