---
title: React-router (5) React 專案中的 import 手法
date: 2024-09-17 15:10:26
categories: React-router
tags: React-router
description: "React 專案中的 import 手法"
---

## import 統整

```js
//App.js
import AlbumLayout from "./pages/AlbumLayout";
import AlbumIndex from "./pages/AlbumIndex";
import AlbumPhoto from "./pages/AlbumPhoto";
import AlbumSearch from "./pages/AlbumSearch";
import NotFound from "./pages/NotFound";
```

原本我們會在 App.js 元件中 import 個別元件進來，如果要簡化可以這樣做

在 pages 資料夾底下新增 index.js，統一引入各元件

```js
import Home from "./Home";
import About from "./About";
export { Home, About };
```

在 App.js 再引入即可

```js
// App.js
import { Home, About } from "./pages/index";
```
