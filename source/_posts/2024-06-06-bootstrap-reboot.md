---
title: Bootstrap (6) reboot 基礎樣式
date: 2024-06-06 15:13:54
categories: Bootstrap
tags:
  - Bootstrap
description: "Bootstrap 使用的基礎樣式"
---

## Reboot

bootstrap 是使用 normalize css 為基底來寫全站樣式，會給網站預設樣式， Normalize 並未將所有 HTML 標籤的預設樣式清除，像是文字標籤下方都保有留白，<ol>、<ul> 留有編號和圓點樣式。

- 使用 rems 取代 ems
- 取消元素 margin-top
- 文字設定相關設定，盡量使用 inherit。

- 針對 HTML 標籤自定義樣式

Bootstrap 已經有寫入以下樣式，不用另外撰寫
修改盒模型計算方式

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
img {
  vertical-align: middle;
}
```

### body 設定

以下是 bootstrap 對 body 的基本設定，可用變數的部分放在 `_root.scss`

```css
// ._reboot.scss
body {
  margin: 0;
  font-family: var(--bs-body-font-family);
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #dee216;
  background-color: var(--bs-body-bg);
}
```

### 頁面設定

1. border-box: 設定 _, _::before, \*::after 全部元素為 border-box。
2. body 上設定 文字大小 1rem。
3. 背景色彩預設為 #fff 白色。

### 字體設定

使用 system ui 字體，讓字體在每個裝置都能很好呈現。

```scss
$font-family-sans-serif:
  // Cross-platform generic font family (default user interface font)
  system-ui,
  // Safari for macOS and iOS (San Francisco)
  -apple-system, // Windows
  "Segoe UI",
  // Android
  Roboto, // older macOS and iOS
  "Helvetica Neue",
  // Linux
  "Noto Sans", "Liberation Sans", // Basic web fallback
  Arial,
  // Sans serif fallback
  sans-serif, // Emoji fonts
  "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji" !default;
```

### 標題

`<h1>~<h6>` 標題取消 margin-top，並加上 `margin-bottom: .5rem`，`line-height: 1.2;`

### 段落

`<p></p>` 段落取消 margin-top，並加上 `margin-bottom: 1rem`

### 連結 Links

`<a href="#">This is an example link</a>` 連結預設有下底線，和藍色文字顏色。

### 列表 Lists

`<ul>, <ol>, and <dl>` 列表取消 margin-top，並加上`margin-bottom: 1rem`。
並且在 `<ul>, <ol>` 加上左邊的 padding-left。

### cursor-pointer

若要在元素上加入 cursor-pointer，加上 `role="button" `即可。

`<span role="button" tabindex="0">Non-button element button</span>`
