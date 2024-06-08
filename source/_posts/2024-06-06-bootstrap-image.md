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
