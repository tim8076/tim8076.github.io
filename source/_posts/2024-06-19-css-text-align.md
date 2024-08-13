---
title: (0-9) CSS基礎篇 文字對齊 (text-align)
date: 2024-06-19 10:57:32
tags: 
- CSS基礎篇
categories: CSS
description: 'CSS 文字對齊設定'
---

## text-align 說明

text-align 用於設定文字的水平對齊方式。

- left: 將文本對齊到容器的左邊緣（默認對齊方式）。
- right: 將文本對齊到容器的右邊緣。
- center: 將文本居中對齊。
- justify: 將文本對齊到容器的兩邊緣（即左右對齊），使每一行的文字間距相等。
- start: 根據文本的書寫方向，將文本對齊到開始邊緣（對左到右的文本為左對齊，對右到左的文本為右對齊）。
- end: 根據文本的書寫方向，將文本對齊到結束邊緣（對左到右的文本為右對齊，對右到左的文本為左對齊）。
- inherit: 繼承父元素的 text-align 屬性值。

## text-align last

text-align-last 可以設定最後一行的文字對齊。利用 text-align-last 搭配 justify ，可以將單行文字左右對齊。

``` css
.text {
  padding: 1rem;
  background-color: #ccc;
  margin: 60px 0;
  text-align-last: justify;
}
```

[範例](https://codepen.io/jskrtivy-the-animator/pen/gOJvorz)

