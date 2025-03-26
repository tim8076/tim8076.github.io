---
title: React-router (4) NotFound 頁面與 useNavigate
date: 2024-09-15 11:35:14
categories: React-router
tags: React-router
description: "使用 useNavigate 建立 NotFound 元件"
---

## 建立 NotFound 元件

```js
// NotFound.js
export default function NotFound() {
  return <div>這是不存在頁面</div>;
}
```

## 引入元件

在 App.js 中引入，當上方路由都不匹配時，會導向 NotFound 元件

```js
import NotFound from "./pages/NotFound";
function App() {
  return (
    <div className="App">
      <Navbar />
      <div className="container mt-3">
        <Routes>
          <Route path="/" element={<Home />}></Route>
          <Route path="/about" element={<About />}></Route>
          <Route path="*" element={<NotFound />}></Route>
        </Routes>
      </div>
    </div>
  );
}
```

## navigate 元件

如果希望使用者到錯誤頁面後，自動導回首頁，可使用 useNavigate 方法

```js
// 在2秒鐘後，導回首頁
import { useNavigate } from "react-router-dom";
export default function NotFound() {
  const navigate = useNavigate();

  useEffect(() => {
    setTimeout(() => {
      navigate("/");
    }, 2000);
  }, [navigate]);

  return <div>這是不存在頁面</div>;
}
```

navigate 也可帶入數字，代表回到上一頁或前往下一頁

```js
// 點擊後回到上一頁
<button
  type="button"
  onClick={() => {
    navigate(-1);
  }}
>
  回到上一頁
</button>
```

## 選用參數

useNavigate() 可以帶上選用參數，這邊也補充給大家～

1. replace: boolean，其值為 true 或 false。通常呼叫 navigate 會推送一個新的 entry 到 history stack，所以使用者可以按下前一頁回去，如果填入 replace: true 目前的 entry 在 history stack 內會被取代成新的。例如：當用戶點擊『購買』按鈕但需要先登入時，在登入後跳轉到結帳畫面，若使用 replace: true，當他們再次點擊回到前一頁時，不會再次看到登入頁面。

2. state: 可為任意值，可用 state 在跳轉路由時傳遞資料，例如：navigate('/login', { state: { id: 1, } })，在 Login 元件就可以透過以下方式把傳遞值取出

```js
const location = useLocation();
console.log(location.state.id) // 1
```