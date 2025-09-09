---
title: NextJs (14) 圖片優化
date: 2025-08-06 15:07:52
categories: NextJs
tags: NextJs
description: "Next 圖片優化"
---

Next.js 的 `<Image>` 元件是對原生 `<img>` 的加強，提供以下功能：

- 尺寸自動優化：依裝置需求自動提供合適尺寸的圖片，並轉成 WebP 或 AVIF 等效能更高的格式。
- 視覺穩定性：依照圖片原始寬高建立 DOM 位置，避免載入時 layout shifting。
- 漸進載入與模糊預覽：圖片進入 viewport 才載入，可選擇使用 placeholder="blur" 顯示低解析模糊預覽，再進行完全載入。
- 高彈性資源處理：不論本地或遠端圖片，都可以按需即時調整尺寸。

## 本地圖片（Local）

若將圖片放在 public/ 資料夾中，直接用 / 引用就好：

```jsx
import Image from 'next/image'
 
export default function Page() {
  return (
    <Image
      src="/profile.png"
      alt="Picture of the author"
      width={500}
      height={500}
    />
  )
}
```

如果透過 import 匯入圖片，Next.js 會自動捕捉其寬高並加上低解析並模糊佔位（blurDataURL）及 placeholder="blur" 支援

```js
import Image from 'next/image'
import ProfileImage from './profile.png'
export default function Page() {
  return (
    <Image
      src={ProfileImage}
      alt="Picture of the author"
      // width={500} automatically provided
      // height={500} automatically provided
      // blurDataURL="data:..." automatically provided
      // placeholder="blur" // Optional blur-up while loading
    />
  )
}
```

## 遠端圖片

使用遠端 URL 或 API 傳入的圖片時，必須手動指定 width 和 height props

```js
<Image
  src="https://example.com/avatar.png"
  alt="使用者大頭照"
  width={200}
  height={200}
/>
```

如果不確定寬高，可以設定 fill 為 true 來填滿父層容器

```js
<Image src="/profile.png" fill={true} />
```
此外，你需要在 next.config.js 中設定允許的遠端來源，確保安全與效能

```js
// next.config.ts
import type { NextConfig } from 'next'
const config: NextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 's3.amazonaws.com',
        port: '',
        pathname: '/my-bucket/**',
        search: '',
      },
    ],
  },
}
export default config
```




