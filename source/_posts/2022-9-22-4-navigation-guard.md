---
title:  vue-router (7) 導航守衛
date: 2022-09-22 15:32:00
categories: Vue
tags: vue-router
description: '使用 vue 導航守衛'
---

## 什麼是導航守衛 ?

導航守衛和vue的生命週期有點像，它提供我們在切換路由時，有不同的hook可以去做事的機會，流程如下:

1. Navigation triggered. (路由切換時觸發)
2. Call beforeRouteLeave guards in deactivated components.(離開原本的元件觸發)
3. Call global beforeEach guards. (準備進入新元件時觸發，是全域的hook，可以針對每一個路由設定一樣的規則)
4. Call beforeRouteUpdate guards in reused components. (在進入相同模組時觸發，例如: ?id =1 切換到 ?id=2 ，參數換但模組沒換)
5. Call beforeEnter in route configs.(針對特定route，設定特定規則)
6. Resolve async route components.
7. Call beforeRouteEnter in activated components. (第一次進入模組時觸發)
8. Call global beforeResolve guards.
9. Navigation is confirmed.
10. Call global afterEach hooks.
11. DOM updates triggered.
12. Call callbacks passed to next in beforeRouteEnter guards with instantiated instances.

## beforeEach (全域的route 守衛)

![](https://miro.medium.com/max/1100/1*79o4cb4bXqRjUTkh7eyvPQ.png)

beforeEach在準備進入新元件時觸發，是全域的hook，可以針對每一個路由設定一樣的規則。beforeEach提供兩個參數，to 和 form

- to: 即將前往的路由

- from: 目前正要離開的路由

並且可以return 一些值:

- return false: 取消導頁行為，並切回from的路由。

- return 路由位置: 導頁到新的路由位置，可傳入的路由位置方式

beforeEach 也可搭配async await