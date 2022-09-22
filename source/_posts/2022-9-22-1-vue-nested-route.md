---
title: vue-router (4) 巢狀路由
date: 2022-09-22 10:29:03
categories: Vue
tags: vue-router
description: 'vue-router 巢狀路由介紹'
---

## 巢狀路由

有些時候元件可能有多層的巢狀結構

```
/user/johnny/profile                  /user/johnny/posts
+------------------+                  +-----------------+
| User             |                  | User            |
| +--------------+ |                  | +-------------+ |
| | Profile      | |  +------------>  | | Posts       | |
| |              | |                  | |             | |
| +--------------+ |                  | +-------------+ |
+------------------+                  +-----------------+
```

此時可以在路由表以巢狀路由的方式設定，以上一章節的結構為例

``` html
<div id="app">
  <router-view></router-view>
</div>
```

``` js
const User = {
  template: `
    <div class="user">
      <h2>User {{ $route.params.id }}</h2>
      <router-view></router-view>
    </div>
  `,
}
```

我們在 User 元件內也可以設定 router-view，來顯示巢狀的元件。

``` js
const routes = [
  {
    path: '/user/:id',
    component: User,
    children: [
      {
        // UserProfile will be rendered inside User's <router-view>
        // when /user/:id/profile is matched
        path: 'profile',
        component: UserProfile,
      },
      {
        // UserPosts will be rendered inside User's <router-view>
        // when /user/:id/posts is matched
        path: 'posts',
        component: UserPosts,
      },
    ],
  },
]
```

我們以一個 children 的陣列來設定子層的路由，而子層路由的每個物件寫法就和外層是一樣的。

此時 '/user/1234' 並不會在 User的 router-view 內顯示任何子元件，因為沒有符合路由。如果想顯示元件，可以設定空字串。

``` js
const routes = [
  {
    path: '/user/:id',
    component: User,
    children: [
      // UserHome will be rendered inside User's <router-view>
      // when /user/:id is matched
      { path: '', component: UserHome },

      // ...other sub routes
    ],
  },
]
```






