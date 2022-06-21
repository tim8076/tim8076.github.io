---
title: (1) CSS 基礎篇-Position
date: 2022-06-21 11:16:36
categories: CSS
tags: 
- CSS基礎篇
description: '利用position屬性定位網站元素'
---

## Position 屬性介紹

在網頁中 position 的用途是設定「物件定位時所要的參考對像」，預設狀態下物件的位置是依據資料流來做排列，也就是跟隨資料做排列，如果對物件添加了不同的 position 之後，就能改變物件所參考的空間對像，進而改變物件的位置。

以下分別介紹各種position 屬性

## static 靜態定位

是元素的預設值，不會被特別定位」在頁面上特定位置，而是照著瀏覽器預設的配置自動排版在頁面上

## relative 相對定位

在一個設定為 position: relative 的元素內設定 top 、 right 、 bottom 和 left 屬性，會使其元素「相對地」調整其原本該出現的所在位置，而不管這些「相對定位」過的元素如何在頁面上移動位置或增加了多少空間，都不會影響到原本其他元素所在的位置。可以稱為【偏移顯示】

不過通常不會對position relative設定top 、 right 等位移，因為會讓元素脫離預設的排版，讓我們很難去設定周圍元素的樣式。

[參考影片](https://youtu.be/jx5jmI0UlXU?t=166)

## abosulute 絕對定位

會將元素從預設排版中抽離，就像不存在於html結構中一樣。
元素設定 Position abosulute 後會去尋找父層中，有定位的元素做定位，如最常用的 position:relative、或fixed、absolute；
若父層都沒有定位元素，就會跟瀏覽器做定位。

position absolute可以搭配top 、bottom 、right、left 來設定定位位置，如下面範例將元素定位在左上角。

``` css
.box {
  position: position;
  top: 0;
  left: 0;
}
```
### absolute搭配 width height技巧
width、height、margin: auto 跟top 、bottom等一起用，可以控制元素的大小與位置，[教學影片](https://www.youtube.com/watch?v=QGKO0PGzFXQ&t=16s)

![position](https://miro.medium.com/max/826/1*ThNCveqMOYrXF4nVoTBWkw.png)

![position](https://miro.medium.com/max/1400/1*PIKeD9RV4TGRvLhT3w5ylA.png)

## fixed 固定定位

固定定位（position: fixed）的元素會相對於瀏覽器視窗來定位，這意味著即便頁面捲動，它還是會固定在相同的位置。和 relative 一樣，我們會使用 top 、 right 、 bottom 和 left 屬性來定位。

固定定位元素不會保留它原本在頁面應有的空間，不會跟其他元素的配置互相干擾。

## sticky 黏著定位

結合了 position : relative，跟 position: fixed，當使用者沒滑動卷軸時，就跟relative元素一樣，當使用者滑動卷軸時，則跟position: fixed 會固定在視窗上。

[範例](https://codepen.io/tim-chou/pen/NWbvMQL)






