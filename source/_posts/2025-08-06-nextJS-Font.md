---
title: NextJs (15) 字型優化
date: 2025-08-06 15:24:27
categories: NextJs
tags: NextJs
description: "Next 字型優化"
---

Next.js 提供的 next/font 功能，能讓你在使用 Google Fonts 或自訂字體時，享有以下優點：

✅ 字體自託管（Self-hosted）：不透過 Google API，避免外部請求、提升隱私。
✅ 更快載入：字體在建置（build）階段就打包進網站，載入更快。
✅ 避免版面跳動（Layout Shift）：自動預留空間，防止字體載入時文字閃爍。
✅ 懶載入 + swap 模式：可讀性佳，不會一開始出現空白。

## 使用 Google Fonts

使用 next/font/google 可以很方便地引入 Google 提供的免費字體，字體會自動轉成可用於本機的格式並載入。

```js
import { Inter } from 'next/font/google'

const inter = Inter({
  subsets: ['latin'],
  display: 'swap',
})
export default function RootLayout({ children }) {
  return (
    <html lang="zh-Hant" className={inter.className}>
      <body>{children}</body>
    </html>
  )
}
```

可設定參數：
- subsets: 字體子集（例如：latin、latin-ext、cyrillic 等）
- weight: 指定權重（粗細），非 variable 字體必填
- display: 字體顯示方式，建議使用 'swap'

## 使用本地字體（Local Fonts）

透過 next/font/local 可載入你自己準備的 .woff2、.ttf 等字體檔案，並享有與 Google Fonts 相同的優化功能。

```js
import localFont from 'next/font/local'
 
const myFont = localFont({
  src: './my-font.woff2',
})
 
export default function RootLayout({ children }) {
  return (
    <html lang="en" className={myFont.className}>
      <body>{children}</body>
    </html>
  )
}
```

