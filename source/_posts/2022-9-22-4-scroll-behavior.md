---
title:  vue-router (8) 滾動行為
date: 2022-09-22 15:32:00
categories: Vue
tags: vue-router
description: 'vue-router 滾動行為'
---

## 滾動行為 

我們可以在換頁時設定滾動行為，例如換頁時頁面置頂，或者回到上一頁原本滾動的位置。

建立 router 時，可以設定 `scrollBehavior` 的函式，函式有 to 、from 、savedPosition 三個參數。

以下為設定的範例:

- 換頁時永遠置頂

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    // always scroll to top
    return { top: 0 }
  },
})
```

- 有上下頁位置紀錄時，回到那個位置，否則置頂。

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    if (savedPosition) {
      return savedPosition
    } else {
      return { top: 0 }
    }
  },
})
```

- 指定頁面滾動

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    if (to.fullPath.match('newPage')) {
      return {
        top: 0
      }
    }
    return {}
  },
})
```

- 依照指定元素位置設定

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    // always scroll 10px above the element #main
    return {
      // could also be
      // el: document.getElementById('main'),
      el: '#main',
      top: -10,
    }
  },
})
```

- 指定滾動到某個 錨點

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    if (to.hash) {
      return {
        el: to.hash,
      }
    }
  },
})
```

- 設定[滾動行為](https://developer.mozilla.org/en-US/docs/Web/API/Window/scroll)

``` js
const router = createRouter({
  scrollBehavior(to, from, savedPosition) {
    if (to.hash) {
      return {
        el: to.hash,
        behavior: 'smooth',
      }
    }
  }
})
```





