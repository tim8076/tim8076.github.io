---
title: (6) CSS基礎篇 盒模型
date: 2024-06-08 13:56:50
categories: CSS
tags: 
- CSS基礎篇
description: '介紹 css 盒模型尺寸計算'
---

## 盒模型介紹

![](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/box-model.png)

瀏覽器引擎在佈局文檔 (document) 時，會根據 CSS 的 Box Model 把每個元素視為長方形狀的 Box，這個 Box 是由內容 (content)、內距 (padding)、邊框 (border) 和外距 (margin) 所組成。

- 內容(content)：元素的實際內容，如文本、圖片等。內容區域的尺寸由width和height屬性定義。

- 內邊距(padding)：內容與邊框之間的空白區域。內邊距的尺寸可以通過padding屬性設置。

- 邊框(border)：圍繞內容和內邊距的邊框。邊框的寬度、樣式和顏色可以分別通過border-width、border-style和border-color屬性設置。

- 外邊距(margin)：元素與相鄰元素之間的空白區域。外邊距的尺寸可以通過margin屬性設置。

這四個部分組合起來形成一個元素在網頁中的總空間，占據的空間大小計算如下：

``` md
元素的總寬度 = 內容寬度 + 左右內邊距 + 左右邊框寬度 + 左右外邊距
元素的總高度 = 內容高度 + 上下內邊距 + 上下邊框寬度 + 上下外邊距
```

## 盒模型的兩種模式

### content box

``` css
html {
  box-sizing: content-box;
}
```

content-box 是網頁預設的尺寸計算方式

```
計算方式為: 內容(width,height) + padding + border
```

### border box

``` css
html {
  box-sizing: border-box;
}
```

在這種模型下，width和height包括內容、內邊距和邊框的尺寸，但不包括外邊距。可以通過設置box-sizing: border-box;來使用替代盒模型。

```
計算方式為: 內容(width,height) ，padding 和 border包含在內容裡。
```


