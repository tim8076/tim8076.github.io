---
title: CSS font-family 教學
date: 2024-04-04 11:20:54
tags: 
- CSS基礎篇
categories: CSS
description: '使用 system-ui 字型'
---

## system-ui 字型的好處

一般建立網頁時，常用 google font 的 CDN 來載入字型，但會讓網頁速度變慢。
使用電腦、手機內建的 system-ui 可以避免這個問題。

``` css
body {
   font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
```

- `-apple-system, BlinkMacSystemFont` : Apple 系統字型。
- `Segoe UI`: Window 系統字型。
- `Roboto`: Unix 系統字型。
 
當這樣設定時，系統會從最前面的 system-ui 字型開始套用，如果找不到，就往後尋找直到最後的 sans-serif 為止。

``` css
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 900;
}
```

使用 system-ui 的另一個好處是，從 100-900的字體粗細都有。不像 google-font 還要下載指定的字體粗細。




