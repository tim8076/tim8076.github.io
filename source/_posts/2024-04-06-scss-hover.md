---
title: (13) SCSS練功坊-hover時產生樣式
date: 2024-04-06 12:08:45
categories: scss
tags: 
- scss
description: '使用 父層選擇器產生樣式'
---

## 產生 hover 樣式

在 scss 裡，可以用 & 來指向父層，產生 hover 時的樣式。

``` scss

.text-primary {
  color: black;

  &:hover {
    color: white;
  }
}
```

如上在 hover 時，color會變白色。
