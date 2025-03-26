---
title: NextJs (11)部屬 Next 專案
date: 2025-03-21 16:22:21
categories: NextJs
tags: NextJs
description: "Next部屬"
---

## 部署
純 Node.js 環境輸出

1️⃣ 先設定 next.config.js

```js
module.exports = {
  output: "standalone",
};
```
2️⃣ 重新編譯

```js
next build
```
這會生成 .next/standalone/ 目錄，內含 獨立的 Node.js 伺服器。

3️⃣ 用 node 直接運行

進入 .next 資料夾

```js
node ./standalone/server.js
```