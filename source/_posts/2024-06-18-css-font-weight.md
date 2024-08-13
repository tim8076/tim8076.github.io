---
title: (0-3) CSS基礎篇 文字粗細 (Font weight)
date: 2022-06-20 11:23:54
tags: 
- CSS基礎篇
categories: CSS
description: 'CSS 文字粗細 (Font weight)設定'
---

## Font weight

在 CSS 中，設定文字粗細的方法主要是使用 font-weight 屬性。這個屬性允許你設定文字的粗細程度，有幾種常見的使用方式：

使用關鍵字：可以使用預設的關鍵字來設定文字粗細，如 normal 和 bold。
使用數值：可以使用數值來設定更細緻的粗細程度，範圍從 100 到 900，數值越大，文字越粗。

``` css
.bold-text {
    font-weight: bold;
}
.thin-text {
    font-weight: 100;
}
```

關鍵字與數值之間的對應關係如下：

| 關鍵字        | 數值 |
|---------------|------|
| `thin`        | 100  |
| `extra-light` | 200  |
| `light`       | 300  |
| `normal`      | 400  |
| `medium`      | 500  |
| `semi-bold`   | 600  |
| `bold`        | 700  |
| `extra-bold`  | 800  |
| `black`       | 900  |