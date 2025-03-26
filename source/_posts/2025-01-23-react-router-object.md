---
title: React-router (7) Plain Object Router
date: 2025-01-23 13:26:31
categories: React-router
tags: React-router
description: "Plain Object Router 用法說明"
---

## 路由配置

在 React Router 中，也可以使用 plain object（純物件）來代表路由的配置。
預計渲染路由，main.js 中的 RouterProvider 會渲染整個 App 元件，App 元件內的 outlet 才會渲染其他內容。
![](../images/react/react-19.png)

1. main.js 引入 RouterProvider, createHashRouter，並建立路由表 routes 陣列，陣列內的物件會代上 path 跟對應的元件，並用 createHashRouter 將路由陣列代入來建立路由表

```jsx
// main.js
import { Home, About } from "./pages/index";
import { RouterProvider, createHashRouter } from "react-router-dom";
const routes = [
  {
    path: '/',
    element: <App />,
    children: [
      {
        index: true,
        element: <Home />
      },
      {
        path: '/about',
        element: <About />
      }
    ],
  },
]
const router = createHashRouter(routes)
createRoot(document.getElementById('root')).render(
  <StrictMode>
    <RouterProvider router={router}/>
  </StrictMode>,
```

2. App.jsx 中用 outlet 的方式帶入路由表中 children 的頁面。

```jsx
// App.jsx
import { Outlet } from "react-router-dom";

function App() {
  return (
  <div className="App">
    <Navbar />
    <div className="container mt-3">
      <Outlet />
    </div>
  </div>
);
```

## 專案結構優化

將路由表直接寫在 main.jsx 會不好管理，所以在根目錄新開一個 routes 資料夾，底下新增 index.jsx 檔案來管理路由

```
- routes
  - index.jsx
```

在 index.jsx 裡建立路由表並匯出

```jsx
import { Home, About } from "../pages/index";
import NotFound from "../pages/NotFound";
import { createHashRouter } from "react-router-dom";
import App from '../App.jsx';

const routes = [
  {
    path: '/',
    element: <App />,
    children: [
      {
        index: true,
        element: <Home />
      },
      {
        path: 'about',
        element: <About />
      },
      {
        path: '*',
        element: <NotFound />
      }
    ],
  },
]

const router = createHashRouter(routes);
export default router;
```

在 main.jsx 匯入 router

```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import router from './routes';
import { RouterProvider } from 'react-router-dom';

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <RouterProvider router={router}/>
  </StrictMode>,
)
```
