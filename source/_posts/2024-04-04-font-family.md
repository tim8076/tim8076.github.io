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
 
當這樣設定時，系統會從最前面的 system-ui 字型開始套用，如果找不到，就往後尋找直到最後的 sans-serif 為止。通常撰寫字型的時候會在最後將通用字型（像是：sans-serif 無襯線字體）寫上，確保各個裝置都能正確瀏覽。

``` css
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 900;
}
```

使用 system-ui 的另一個好處是，從 100-900的字體粗細都有。不像 google-font 還要下載指定的字體粗細。

## Google Fonts 線上外部字型載入

選擇想要載入的字型，以 [Castoro](https://fonts.google.com/specimen/Castoro) 為例。

1. 進入 Google Fonts 官網，搜尋 Castoro
2. 點擊右上角的「Get font」
3. 會跳轉到這個畫面，接著點擊「Get embed code」

![](https://imgur.com/OnsYucx.png)

然後下方會提供兩種方式載入（擇一使用）

使用 `<link>` 方式：
將程式碼貼到 HTML <head> 內
範例：

``` html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Castoro:ital@0;1&display=swap" rel="stylesheet">
  <link href="style.css"> <!-- 自定義的 CSS 檔 -->
</head>
```

使用 @import 方式：
在 CSS 最上方加入

``` css
@import url('https://fonts.googleapis.com/css2?family=Castoro:ital@0;1&display=swap');
```





