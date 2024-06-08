---
title: vue-router (1) 安裝與簡介
date: 2022-09-21 10:53:24
categories: Vue
tags: vue-router
description: 'vue-router 安裝與簡介'
---

## 簡介

![](https://miro.medium.com/max/1100/1*FJPvYSYzevc9PXIdx_io6g.png)

Vue Router 是 Vue.js 官方提供的前端路由管理器，是由前端所模擬的路由器，像是我們切換不同頁面時，網址都停留在index.html，但藉由切換 /#/user 的不同路由，可以切換不同的元件來呈現。

## 安裝

如果是用 Vue CLI 建立專案，可選取 Router 選項來安裝。

如果是已經建立好的專案，但在專案建置時並未安裝過，可以用npm來安裝

```
npm install vue-router@4
```

## 使用 vue-router

``` html 
<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!-- use the router-link component for navigation. -->
    <!-- specify the link by passing the `to` prop. -->
    <!-- `<router-link>` will render an `<a>` tag with the correct `href` attribute -->
    <router-link to="/">Go to Home</router-link>
    <router-link to="/about">Go to About</router-link>
  </p>
  <!-- route outlet -->
  <!-- component matched by the route will render here -->
  <router-view></router-view>
</div>
```

在 html 上使用 router-link，作為換頁的連結，router-link 在經過編譯後會變成 `<a> 標籤`。

符合當前路由的元件 則由 router-view 來顯示。

``` js
// 1. 定義路由的元件，可以從其他檔案匯入。如果是SPA的話，則會是一個.VUE檔
const Home = { template: '<div>Home</div>' }
const About = { template: '<div>About</div>' }

// 2. 定義路由表，每個路由會對應一個元件。
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
]

// 3. 建立路由實體，並將路由表加入。
const router = VueRouter.createRouter({
  // 網址路徑模式: 使用網址hash的形式
  history: VueRouter.createWebHashHistory(),
  routes, // short for `routes: routes`
})

// 5. 將路由實體掛載到 vue 實體上。
const app = Vue.createApp({})
// Make sure to _use_ the router instance to make the
// whole app router-aware.
app.use(router)

app.mount('#app')

// Now the app has started!
```




