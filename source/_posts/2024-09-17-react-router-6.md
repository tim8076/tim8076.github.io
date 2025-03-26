---
title: React-router (6) Browser Router 與 Hash Router
date: 2024-09-17 15:31:03
categories: React-router
tags: React-router
description: "Browser Router 與 Hash Router"
---

## 差異說明

在 React Router 中，BrowserRouter 和 HashRouter 都是用來處理應用中的路由的，但它們的工作原理和用途略有不同：

## BrowserRouter

- 使用 HTML5 History API: BrowserRouter 依賴 HTML5 的 history.pushState 和 history.replaceState，因此 URL 是標準的、乾淨的路徑（例如 /about、/contact）。

- 無 Hash（#）符號: 在 URL 中不會有 # 符號，因為它是基於瀏覽器的歷史記錄 API 來管理路由。

- 服務器配置需求: 因為它依賴瀏覽器的歷史 API，所以如果直接進行 URL 跳轉（例如直接訪問 /about），服務器需要適當配置以確保所有請求都指向你的應用程序的入口點（如 index.html）。如果未配置，可能會出現 404 錯誤。

```
路由範例
https://example.com/about
```

## HashRouter

- 使用 URL Hash: HashRouter 使用 URL 中的哈希（#）來模擬不同的路徑。當 URL 變化時，實際上只是 # 後面的部分變化，這部分不會發送到服務器，瀏覽器不會刷新頁面。

- 不依賴伺服器配置: 由於 HashRouter 依賴 URL 中的哈希部分，瀏覽器不會發送新的請求到服務器，這意味著你不需要服務器進行特殊配置。這使得 HashRouter 更加便於部署在一些靜態文件伺服器或不支援路由設置的環境中。

- 有 Hash（#）符號: URL 中會包含 #，並將其後面的部分作為路由的一部分。
  使用場景: 當你無法或不想配置服務器來處理 HTML5 History API，或者你的應用程序是部署在靜態服務器上時，HashRouter 是更簡便的選擇。

在 create react app 中改用 HashRouter

```js
// index.js
import { HashRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <HashRouter>
      <App />
    </HashRouter>
  </React.StrictMode>
);
```
