---
title: (0-5) CSS基礎篇 文字裝飾 (Text decoration)
date: 2022-06-20 11:25:54
tags: 
- CSS基礎篇
categories: CSS
description: 'CSS 文字裝飾 (Text decoration) 設定'
---

## text decoration 規則

 text decoration 用於設定文字的裝飾效果，可以設定的值如下:

- none：無任何裝飾。
- underline：下底線。
- overline：上底線。
- line-through：中線、刪除線。
- inherit：繼承父元素的 text-decoration 屬性。

##  text decoration 組成

 text decoration 實際上由五個屬性組成:

 - text-decoration-thickness: 線段尺寸
 - text-decoration-style: 線段樣式
 - text-decoration-color: 線段色彩
 - text-decoration-line: 線段位置
 - text-underline-offset: 線段偏移距離

 實際上可以如此使用:

 ``` css
  text-decoration-thickness: 1px;
  text-decoration-style: dotted;
  text-decoration-color: red;
  text-decoration-line: underline;
 ``` 

 或是縮寫:

 ``` css
  text-decoration: 1px dotted red underline;
 ```

 text-underline-offset 基本上是設定底線與文字的距離，只針對底線(underline)有效果。
 設定正數值可以增加底線與文字距離。
 設定負數值則使底線往文字上方移動。

 

