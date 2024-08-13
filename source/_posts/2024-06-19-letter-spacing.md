---
title: (0-10) CSS基礎篇 letter spacing
date: 2024-06-19 11:26:11
tags: 
- CSS基礎篇
categories: CSS
description: 'CSS letter spacing 設定'
---

## 基礎設定

letter spacing 用來設定每個字母間的距離。可以設定的值包括 px、em、rem、cm 等。

``` css
// 設定 2 個字元間距
p.increased-spacing {
  letter-spacing: 2em;
}
```

其他增加文字距離的屬性包括

- letter-spacing: 每個字母間的距離
- word-spacing: 每個單字間的距離
- white-space: 每個空白字元距離

## word-spacing 用法

word-spacing 用來處理每個單字間空白的距離，中文不太用得上，但在英文上就可以看出差異。
利用這點，可以將 inline-block 排版產生的 4~5px 的空白處理掉。

``` css
.list {
  word-spacing: -4px;
}
.list li {
  display: inline-block;
  padding: 5px 10px;
}