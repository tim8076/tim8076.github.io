---
title: Bootstrap (8) Image 圖片與大小控制
date: 2024-06-06 17:03:00
categories: Bootstrap
tags: 
- Bootstrap
description: '介紹Bootstrap中與圖片大小的相關設定'
---

[教學應片](https://youtu.be/_SSPsPmz9U0?list=PLqivELodHt3jq3oWBZfdhMu0GE7774HBW)

## 響應式圖片

在 img 加上 `.img-fluid`，會加上 `max-width: 100%;  height: auto;` 屬性，讓圖片自適應父層寬度。

``` html
<img src="..." class="img-fluid" alt="...">
```

## 邊框圖片

在 img 加上 `.img-thumbnail`，替圖片加上 1px border 。

``` html
<img src="..." class="img-thumbnail" alt="...">
```

## w-100

在 img 加上 `.w-100`， 會加上 `width: 100%;` 讓圖片填滿父層寬度

``` html
<img src="..." class="w-100" alt="...">
```

## 圖片區

``` html
<figure class="figure">
  <img src="..." class="figure-img img-fluid rounded" alt="...">
  <figcaption class="figure-caption">A caption for the above image.</figcaption>
</figure>
```

當想要加上圖片的說明文字時，可以在 img 下用 figcaption 包住 說明文字，外層則用 figure
