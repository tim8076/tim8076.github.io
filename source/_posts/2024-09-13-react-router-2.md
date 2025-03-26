---
title: React-router (2) 巢狀路由與 Outlet
date: 2024-09-13 16:26:41
categories: React-router
tags: React-router
description: "React-router 巢狀路由與 Outlet"
---

## 建立巢狀路由

1. 在需要使用巢狀路由的元件內，引入 Outlet 元件

```js
import { Outlet } from "react-router-dom";
export default function AlbumLayout() {
  return (
    <div className="row">
      <div className="col-4">左側選單列表</div>
      <div className="col-8">
        <Outlet />
      </div>
    </div>
  );
}
```

2. Route 元件內帶入子層的 Route 元件，子層的 Route 元件再指定前往的路由。

```js
import AlbumIndex from "./pages/AlbumIndex";

function App() {
  return (
    <div className="App">
      <Navbar />
      <div className="container mt-3">
        <Routes>
          <Route path="/" element={<Home />}></Route>
          <Route path="/about" element={<About />}></Route>
          <Route path="/album" element={<AlbumLayout />}>
            <Route index element={<AlbumIndex />}></Route>
            <Route path="/user" element={<AlbumUser />}></Route>
          </Route>
        </Routes>
      </div>
    </div>
  );
}
```

子路由前往路徑若為渲染的第一頁，可用 index 取代 path

```jsx
<Route index element={<AlbumIndex />}></Route> //  /album
<Route path="/user" element={<AlbumIndex />}></Route> //  /album/user
```

## 傳入資料到 Outlet 給子層

將資料傳入 Outlet 給子層路由用

1. 在 Outlet 用 context 將資料傳入

```jsx
<div className="col-8">
  <Outlet context={list} />
</div>
```

2. 子層接收資料

子層用 useOutletContext 接收資料

```jsx
import { useOutletContext } from "react-router-dom";
export default function AlbumIndex() {
  const list = useOutletContext();
  return <div>這是相簿首頁</div>;
}
```
