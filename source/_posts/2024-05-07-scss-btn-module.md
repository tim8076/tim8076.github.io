---
title: (15) SCSS練功坊-元件模組化技巧
date: 2024-05-07 14:05:00
categories: scss
tags: 
- scss
description: '元件模組化技巧'
---

## 元件模組化技巧

本篇講解 scss 元件如何模組化過程，以 button 元件為例:

``` scss
// 首先可以設定 .btn 的基礎樣式
.btn {
  display: inline-block;
  // 當元素是inline-block時 vertical-align:middle 可以使其垂直對齊。
  vertical-align: middle; 
  padding: 0.375rem 0.75rem;
  text-align: center;
  text-decoration: none;
  font-size: 1rem;
  line-height: 1.5;
  user-select: none;
  color: #000;
  border-radius: 0.375rem;
  background-color: transparent;
  border: 1px solid transparent;
}

// 設定顏色按鈕模組
.btn-primary {
  color: #fff;
  background-color: #007bff;
  border-color: #007bff;
}

// 增加大小按鈕模組
.btn-lg {
  padding: 0.5rem 1rem;
  font-size: 1.25rem;
  line-height: 1.5;
  border-radius: 0.3rem;
}
```
