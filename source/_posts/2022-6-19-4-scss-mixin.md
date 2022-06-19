---
title: (5) SCSS練功坊-mixin
date: 2022-06-19 16:39:30
categories: scss
tags: 
- scss
description: '使用 mixin 管理重複的樣式'
---

## 使用 mixin 管理重複的樣式

當我們有一段樣式，會被重複用到，裡頭樣式數值又會有不同時，可以用mixin做管理。
撰寫mixin方法

``` 
@mixin + mixin名稱(參數) { }
```

![circle](https://miro.medium.com/max/1266/1*M5IXbD8WVeMwgzfadFHNrQ.png)


上圖中， circle 裡可以帶入 $size，$bg-color等不同參數，如此在不同地方，我們可以依照不同需求，傳入不同參數，做出不同的圓形。

引入 mixin時，用 @include + mixin名稱

![編譯後結果](https://miro.medium.com/max/1140/1*Yn5snpWqUCxsEJ1eA646zQ.png)



