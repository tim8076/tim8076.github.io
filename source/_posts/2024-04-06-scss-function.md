---
title: (14) SCSS練功坊-function
date: 2024-04-06 13:52:43
categories: scss
tags: 
- scss
description: '使用 function 計算數值'
---

## 使用 function 來產生

當在 scss 想計算較複雜的數值時，可以使用 funtion

``` scss
@function light-comp($color) {
  $complement: complement($color);
  $light-complement: lighten($complement, 30%);
  @return $light-complement;
}
```

如上 我們在 自己建立的 light-comp function 中，傳入一個變數，
透過兩個內建的函式，來調整原本的顏色。

- complement(): 回傳相對色
- lighten(): 調亮顏色

最後將調整完的 $light-complement 透過 @return 回傳。



