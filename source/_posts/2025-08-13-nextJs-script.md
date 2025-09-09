---
title: NextJs (18) Script 元件
date: 2025-08-13 11:47:36
categories: NextJs
tags: NextJs
description: "Next 中使用 Script 元件"
---

`<Script>` 是 Next.js 提供的 React 組件，用於載入與最佳化第三方 script

## 使用示例

1. 在 root layout 中載入全站共用 script

```js
import Script from 'next/script'

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        {children}
        <Script src="https://example.com/script.js" />
      </body>
    </html>
  )
}
```
載入並執行於任何路由初次造訪時，只會執行一次

2. 在 layout 中載入多頁面共用 script

```js
import Script from 'next/script'

export default function DashboardLayout({ children }) {
  return (
    <>
      <section>{children}</section>
      <Script src="https://example.com/script.js" />
    </>
  )
}
```
此 script 在 dashboard 子路由或其頁面被造訪時載入，且只會載入一次。

## 屬性 (Props) 說明

必填屬性

- src：必須提供，指向外部或內部腳本檔的路徑或 URL。如使用 inline script，則可省略。


可選屬性：

- strategy：腳本載入策略，影響何時與如何載入腳本。
 - 可選值如下：
 - beforeInteractive：在任何 Next.js 程式碼與頁面 hydration 前載入，適合載入關鍵腳本（如 bot 偵測、Cookie 管理等）。這類腳本會被放入 `<head>`，不會阻塞 hydration。
 - afterInteractive（預設）：在部分或全部 hydration 完成後載入腳本，適用於希望盡快載入但不影響首屏的腳本。
 - lazyOnload：在瀏覽器閒置時間才載入，適合非即時需求或降低初始載入負擔的情境。
 - onLoad：腳本載入完成後執行的 callback。
 - onReady：腳本每次掛載時執行。
 - onError：腳本載入失敗時執行的 callback。
 
注意：這些事件處理器需放在 Client Component 中，並使用 "use client" 宣告。
其他 HTML 屬性（如 nonce, data-* 等）將自動轉發到最終的 <script> 元素。