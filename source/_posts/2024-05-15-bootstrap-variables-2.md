---
title: Bootstrap (2) SCSS 客製化-變數更改
date: 2024-05-15 12:39:26
categories: Bootstrap
tags:
  - Bootstrap
description: "更改SCSS以客製化 Bootstrap"
---

## Variable defaults

在 bootstrap 裡的每個 variable 都有加上 !default 標籤，讓我們在自己的 scss 檔案裡能覆蓋這些樣式

```scss
// Required
@import "../node_modules/bootstrap/scss/functions";

// 客製化樣式要在 functions 之後，variables之前
$body-bg: #000;
$body-color: #111;

// Required
@import "../node_modules/bootstrap/scss/variables";
@import "../node_modules/bootstrap/scss/variables-dark";
@import "../node_modules/bootstrap/scss/maps";
@import "../node_modules/bootstrap/scss/mixins";
@import "../node_modules/bootstrap/scss/root";
```

## 網站主色更改

在 bootstrap 資料夾裡 可以找到 \_\_variable.scss 檔案，在裏頭可以修改變數來客製化

\_\_variable.scss 檔案從上到下的順序為 色系 > Options(預設樣式)> Spacing(間隔)> Body > link (連結) > breakpoints(斷點 ˇ)

在 \_\_variable.scss 檔案 找到$theme-colors 來更改顏色

```scss
$theme-colors: (
  "primary": #ffdf65,
  "secondary": $secondary,
  "success": $success,
) !default;
```

要新增色系直接加在 $theme-colors 裡面即可

```scss
$theme-colors: (
  "primary": #ffdf65,
  "secondary": $secondary,
  "success": $success,
  "success2": #ddff666,
) !default;
```

## options 預設樣式更改

在變數的 Options 區域可以更改全站設定

```scss
$enable-caret: true !default;
$enable-rounded: true !default; // 是否啟用元素的圓角
$enable-shadows: false !default; // 是否啟用元素的陰影
$enable-gradients: false !default; // 是否啟用元素的漸變背景
$enable-transitions: true !default; // 是否啟用 CSS 過渡效果
$enable-reduced-motion: true !default;
```

## Spacing 更改間距

在變數的 spacer 區域可以更改距離設定

```scss
$spacer: 1rem !default;
$spacers: (
  0: 0,
  1: $spacer * 0.25,
  2: $spacer * 0.5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
) !default;
```

更改後跟距離有關係的 class 都會吃到效果，如 p-3 、mb-2 等

## body 更改全站樣式

body 區域可以更改全站預設樣式

```scss
$body-text-align: null !default;
$body-color: $gray-900 !default; // 全站文字顏色
$body-bg: $white !default; // 全站背景顏色

$body-secondary-color: rgba($body-color, 0.75) !default;
$body-secondary-bg: $gray-200 !default;

$body-tertiary-color: rgba($body-color, 0.5) !default;
$body-tertiary-bg: $gray-100 !default;

$body-emphasis-color: $black !default;
```

## 文字大小設定

文字的通用樣式預設無法響應式變化

需要更改 responsive 屬性，修改方式可參考 Bootstrap - Utilities API

```scss
$utilities: map-merge(
  $utilities,
  (
    "font-size": map-merge(
        map-get($utilities, "font-size"),
        (
          responsive: true,
        )
      ),
  )
);
```

然後在 關掉 RFS 功能

```scss
$enable-rfs: false !default;
```

```scss
$font-sizes: (
  1: $h1-font-size,
  2: $h2-font-size,
  3: $h3-font-size,
  4: $h4-font-size,
  5: $h5-font-size,
  6: $h6-font-size,
) !default;
```

## 其餘文字設定

- `<h1>~<h6>` 標籤：`$headings-margin-bottom`
- `<p>`：`$paragraph-margin-bottom`
- 內文:
  - 字重：`$font-weight-base`
  - 行高：`$line-height-base`
- 標題:
  - 字重：`$headings-font-weight`
  - 行高：`$headings-line-height`

## link 更改連結樣式

```scss
$link-color: $primary !default; //更改a連結顏色
$link-decoration: underline !default; // 更改a連結下底線
$link-shade-percentage: 20% !default;
$link-hover-color: shift-color($link-color, $link-shade-percentage) !default;
$link-hover-decoration: null !default;

$stretched-link-pseudo-element: after !default;
$stretched-link-z-index: 1 !default;
```

## 修改元件樣式

### Button

- 字重：`$btn-font-weight`
- 間距：`$btn-padding-y`、`$btn-padding-x` (調整為手機版尺寸，桌機再另外用通用類別調整)
- 圓角：`$btn-border-radius`
- disabled
  - `$btn-disabled-opacity`

### 表單

- input:
  - padding: `$input-btn-padding-y`、`$input-btn-padding-x`
  - 字重：`$input-font-weight`
  - 提示字顏色：`$input-placeholder-color`
  - 背景色：`$input-bg`
  - 圓角：`$input-border-radius`
