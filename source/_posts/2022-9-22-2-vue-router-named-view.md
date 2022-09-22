---
title: vue-router (6) 命名視圖
date: 2022-09-22 13:48:47
categories: Vue
tags: vue-router
description: '在一個元件呈現多個視圖'
---

## 命名視圖

當今天在一個元件內想呈現多個 `<router-view>` 時，比如說同時有 `sidebar view` 和 `main view`，可以使用命名視圖的方式。

每一個不同的 router-view 會有一個 name 的值，沒有 name 的值則預設為 default。

``` js
<router-view class="view left-sidebar" name="LeftSidebar"></router-view>
<router-view class="view main-content"></router-view>
<router-view class="view right-sidebar" name="RightSidebar"></router-view>
```

在路由表裡以 components 來將多個視圖對應元件。

``` js
const router = createRouter({
  history: createWebHashHistory(),
  routes: [
    {
      path: '/',
      components: {
        default: Home,
        // short for LeftSidebar: LeftSidebar
        LeftSidebar,
        // they match the `name` attribute on `<router-view>`
        RightSidebar,
      },
    },
  ],
})
```

## 巢狀命名視圖

我們也可以結合 巢狀路由與命名視圖來一起設計。

```
/settings/emails                                       /settings/profile
+-----------------------------------+                  +------------------------------+
| UserSettings                      |                  | UserSettings                 |
| +-----+-------------------------+ |                  | +-----+--------------------+ |
| | Nav | UserEmailsSubscriptions | |  +------------>  | | Nav | UserProfile        | |
| |     +-------------------------+ |                  | |     +--------------------+ |
| |     |                         | |                  | |     | UserProfilePreview | |
| +-----+-------------------------+ |                  | +-----+--------------------+ |
+-----------------------------------+                  +------------------------------+
```

- Nav 是一個普通的元件
- UserSettings 是父層的 view component
- UserEmailsSubscriptions, UserProfile, UserProfilePreview 是巢狀的元件

實際的 html 如下

``` html
<!-- UserSettings.vue -->
<div>
  <h1>User Settings</h1>
  <NavBar />
  <router-view />
  <router-view name="helper" />
</div>
```

最後可以在路由表裡來設計

``` js
{
  path: '/settings',
  // You could also have named views at the top
  component: UserSettings,
  children: [{
    path: 'emails',
    component: UserEmailsSubscriptions
  }, {
    path: 'profile',
    components: {
      default: UserProfile,
      helper: UserProfilePreview
    }
  }]
}
```

