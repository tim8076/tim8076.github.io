---
title: React-router (3) 動態路由
date: 2024-09-14 14:16:23
categories: React-router
tags: React-router
description: "React-router 動態路由 設定"
---

## 動態路由設定

1. 在 path 上用 : 設定動態路由

```jsx
<Route path="/album" element={<AlbumLayout />}>
  <Route index element={<AlbumIndex />}></Route>
  <Route path=":id" element={<AlbumPhoto />}></Route>
</Route>
```

2. 在元件內用 useParams 取出動態路由值

```js
import { useParams } from "react-router-dom";

export default function AlbumPhoto() {
  const { id } = useParams();
}
```

## 取得路由參數

```
http://localhost:3000/album/search?query=building
```

上面網址中 ? 後面的 query 就是網址參數，以下說明 React-router 如何取得網址參數

1. 元件內將方法 `useSearchParams` 引入

```js
import { useSearchParams } from "react-router-dom";
```

2. 在元件內使用方法

```js
export default function AlbumSearch() {
  const [searchParams, setsearchParams] = useSearchParams();
}
```

- searchParams.get('參數名稱'): 取得參數的值
- setsearchParams: 將值寫入參數

```js
// 帶入物件，key為參數名稱，value 為參數值
setsearchParams({
  query: e.target.value,
});
```
