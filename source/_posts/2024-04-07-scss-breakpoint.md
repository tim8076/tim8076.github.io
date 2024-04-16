---
title: (14) SCSS練功坊-製作自己的 grid system
date: 2024-04-07 15:09:36
categories: scss
tags: 
- scss
description: '製作自己的 grid system 格線系統'
---

## 製作 grid system

像 bootstrap、tailwind 等css框架，都會有 grid system 來快速排版。
本篇會介紹 如何在 scss 裡製作屬於自己的格線系統

### container

在格線系統中， container 是一個將內容置中的容器。
會使用 `margin: 0 auto`，讓容器置中。

``` scss
// _grid.scss

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  box-sizing: border-box;
}
```

在container 內層會有 .row，用 flex 讓裡面的 col 能水平排列

``` scss
.row {
  display: flex;
  flex-flow: row wrap;
}
```

再來是 col 的製作，預設會有 12 個欄位
利用 col-2、col-5 的方式決定每個col 佔 12欄裡的幾欄。

``` scss
$grid-columns: 12; // 12欄

$breakpoints: (
  "xs": 0,
  "sm": 480px,
  "md": 720px,
  "lg": 960px,
  "xl": 1200px,
);

// 先跑每個斷點的迴圈
@each $brek, $value in $breakpoints {
  // include mq 的 mixin
  @include mq($brek) {
    // 從 1 跑到 12
    @for $i from 1 through $grid-columns {
      .col-#{$brek}-#{$i} {
        box-sizing: border-box;
        flex-grow: 0;
        // 每欄 col 的寬度
        width: math.div($i * 100%, $grid-columns);
      }
    }
  }
}
```

### 製作 gap

在每個col如果想要有間隔時，我們可以製作每欄的 gap
首先先設定 一個 gap 的 陣列，來決定 gap的寬度。

``` scss
$grid-gaps: (
  '0': 0,
  '1': 10px,
  '2': 20px,
  '3': 30px,
);
```
再來製作 gap 

``` scss
// grid gaps
@each $key, $val in $grid-gaps {
  
  // 在 row欄上加上 gap-3、gap-0 等 class來決定gap寬度
  // 每個 row 底下的 col 會有 padding來撐開寬度。
  .gap-#{$key} > *{
    padding: $val;
  }

  // 用負的margin來移除，最左欄和最右欄的 padding，讓col能貼齊row。
  .gap-#{$key} {
    margin-left: -$val;
    margin-right: -$val;
  }
}
```