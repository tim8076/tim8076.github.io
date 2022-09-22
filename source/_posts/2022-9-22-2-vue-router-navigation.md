---
title: vue-router (5) 路由轉址
date: 2022-09-22 11:22:06
categories: Vue
tags: vue-router
description: '在程式裡進行路由轉址'
---

## 路由轉址

在程式裡，可以使用 router.push(...) 來進行轉址。在 vue 的實體裡，可以透過 `this.$router.push()` 來執行。

``` js
// literal string path
router.push('/users/eduardo')

// object with path
router.push({ path: '/users/eduardo' })

// named route with params to let the router build the url
router.push({ name: 'user', params: { username: 'eduardo' } })

// with query, resulting in /register?plan=private
router.push({ path: '/register', query: { plan: 'private' } })

// with hash, resulting in /about#team
router.push({ path: '/about', hash: '#team' })
```

要注意，如果有 path，則 params 會被忽略。所以可以用 name + params 來搭配。


## Replace 用法

router.replace(...) 用法和 push 一樣，差別在 replace 不會新增新的路由歷史紀錄，相反的他是取代目前路由。

``` js
router.push({ path: '/home', replace: true })
// equivalent to
router.replace({ path: '/home' })
```

## 前往上一頁或下一頁

使用 router.go()，來前往上 / 下一頁

``` js
// go forward by one record, the same as router.forward()
router.go(1)

// go back by one record, the same as router.back()
router.go(-1)

// go forward by 3 records
router.go(3)

// fails silently if there aren't that many records
router.go(-100)
router.go(100)
```
