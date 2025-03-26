---
title: NextJs (6) Layout
date: 2024-09-26 14:45:59
categories: NextJs
tags: NextJs
description: "建立 Layout 共用版型"
---

## 建立 Layout 共同模板

![](../images/nextJs/next-12.png)

如果要建立 Header、Footer 這種通用版型時，next.js 預設就有提供 layout 檔案

位置在 app 資料夾內

![](../images/nextJs/next-13.png)

在 layout 內，可以像這樣加入 header、footer

```js
return (
  <html lang="en">
    <body>
      <header>
        <p>header</p>
      </header>
      {children}
      <footer>
        <p>footer</p>
      </footer>
    </body>
  </html>
);
```

6

## 指定頁面 Layout

個別頁面也能設定自己的 layout

![](../images/nextJs/next-14.png)
![](../images/nextJs/next-15.png)
