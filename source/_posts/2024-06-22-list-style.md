---
title: (8) CSS 基礎篇 List-style
date: 2024-06-22 10:59:30
categories: CSS
tags: 
- CSS基礎篇
description: '用 list-style 設定清單樣式'
---

## 基礎用法

可以使用 list-style 設定清單前方的圖示，可以接受 1-3 個值，語法如下:

``` css
list-style: circle outside url('gold-fish.png')
```

list-style 是簡寫寫法，是以下三個屬性簡寫

- list-style-type: 清單符號樣式
- list-style-position: 清單符號位置
- list-style-image: 清單符號圖片

## list-style-type

list-style-type 用來設定清單前置圖示，可以設定的值有

- none: 沒有符號
- disc: 實心圓形 (預設值)
- decimal: (1、2、3)
- cjk-ideographic: (一、二、三)
- decimal-leading-zero: (01, 02, 03)
- lower-alpha: (a, b, c)
- upper-alpha: (A, B, C)

其他還有很多值，可以參考 [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type#cjk-ideographic)

## 實際專案會用到的屬性

實際專案上會因設計需求清除清單符號，如下:

``` CSS
list-style: none; //簡寫寫法

list-style-type: none; //  單一屬性寫法
```



