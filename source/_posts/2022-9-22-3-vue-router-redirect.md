---
title: vue-router (7) Redirect and Alias
date: 2022-09-22 14:26:27
categories: Vue
tags: vue-router
description: '使用 redirect 重新導向'
---

## Redirect

當想從 '/home' ，導向到 '/' 時:

``` js
const routes = [{ path: '/home', redirect: '/' }]
```

也可以使用命名路由

``` js
const routes = [{ path: '/home', redirect: { name: 'homepage' } }]
```

或使用 function 來進行動態的導向

``` js
const routes = [
  {
    // /search/screens -> /search?q=screens
    path: '/search/:searchText',
    redirect: to => {
      // the function receives the target route as the argument
      // we return a redirect path/location here.
      return { path: '/search', query: { q: to.params.searchText } }
    },
  },
  {
    path: '/search',
    // ...
  },
]
```

## Alias 路由別名

路由別名讓兩個不同路由，可以對應同一個元件。

'/' 和 '/home'，都會顯示同個元件。

``` js
const routes = [{ path: '/', component: Homepage, alias: '/home' }]
```


