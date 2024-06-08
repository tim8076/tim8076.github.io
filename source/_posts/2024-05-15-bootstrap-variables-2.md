---
title: Bootstrap (2) SCSS 客製化-變數更改
date: 2024-05-15 12:39:26
categories: Bootstrap
tags: 
- Bootstrap
description: '更改SCSS以客製化 Bootstrap'
---

## Variable defaults

在 bootstrap 裡的每個 variable 都有加上 !default 標籤，讓我們在自己的scss檔案裡能覆蓋這些樣式

``` scss
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

在 bootstrap 資料夾裡 可以找到 __variable.scss 檔案，在裏頭可以修改變數來客製化

__variable.scss 檔案從上到下的順序為 色系 > Options(預設樣式)> Spacing(間隔)> Body > link (連結) > breakpoints(斷點ˇ)


在 __variable.scss 檔案 找到$theme-colors來更改顏色
``` scss
$theme-colors: (
  "primary":    #ffdf65,
  "secondary":  $secondary,
  "success":    $success,
) !default;
```

要新增色系直接加在 $theme-colors 裡面即可

``` scss
$theme-colors: (
  "primary":    #ffdf65,
  "secondary":  $secondary,
  "success":    $success,
  "success2":   #ddff666,
) !default;
```

## options 預設樣式更改

在變數的 Options 區域可以更改全站設定

``` scss
$enable-caret:                true !default;
$enable-rounded:              true !default; // 是否啟用元素的圓角
$enable-shadows:              false !default; // 是否啟用元素的陰影
$enable-gradients:            false !default; // 是否啟用元素的漸變背景
$enable-transitions:          true !default; // 是否啟用 CSS 過渡效果
$enable-reduced-motion:       true !default;
```

## Spacing 更改間距

在變數的 spacer 區域可以更改距離設定

``` scss
$spacer: 1rem !default;
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
) !default;
```

更改後跟距離有關係的 class 都會吃到效果，如 p-3 、mb-2等

## body 更改全站樣式

body 區域可以更改全站預設樣式

``` scss
$body-text-align:           null !default;
$body-color:                $gray-900 !default; // 全站文字顏色
$body-bg:                   $white !default; // 全站背景顏色

$body-secondary-color:      rgba($body-color, .75) !default;
$body-secondary-bg:         $gray-200 !default;

$body-tertiary-color:       rgba($body-color, .5) !default;
$body-tertiary-bg:          $gray-100 !default;

$body-emphasis-color:       $black !default;
```

## link 更改連結樣式

``` scss
$link-color:                              $primary !default; //更改a連結顏色
$link-decoration:                         underline !default; // 更改a連結下底線
$link-shade-percentage:                   20% !default;
$link-hover-color:                        shift-color($link-color, $link-shade-percentage) !default;
$link-hover-decoration:                   null !default;

$stretched-link-pseudo-element:           after !default;
$stretched-link-z-index:                  1 !default;
```



