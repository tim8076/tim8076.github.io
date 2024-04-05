---
title: (10) SCSS練功坊-Math
date: 2024-04-05 21:56:50
categories: scss
tags: 
- scss
description: '使用 math 計算'
---

## 使用 Math

在 scss 裡可以使用內建的 math 函式來計算。
用 `@use 'sass:math';` 來將 math 函式載入。

``` scss
@use 'sass:math';

@debug math.div(10, 3); // 除法 10 / 3 => 3.3333 

@debug math.$pi;  // 圓周率 3.1415926536

@debug math.floor(2.6); // 四捨五入，無條件去小數點 => 2

@debug math.max(1px, 20px, 15px, 12px); // 取最大值 => 20px
```
