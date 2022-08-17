---
title: canvas (1) 繪製基本圖案
date: 2022-08-13 13:51:12
tags: canvas
description: '介紹如何使用canvas繪製基本圖形'
---

## 基礎設定

canvas是原生的 html 標籤，可以用js來操控，繪製各種動畫或圖案。以下介紹基礎設定

``` html
<canvas id="canvas"></canvas> 
```

``` js
// 選取canvas元素
const canvas = document.querySelector('#canvas');
// 設定 context 是 2d or 3d
const ctx = canvas.getContext('2d');

// 預設畫布大小是螢幕大小
canvas.height = window.innerHeight;
canvas.width = window.innerWidth;
```

## 繪製線條

基礎設定好後，可以嘗試來繪製線條。

- moveTo(x, y): 設定起始點的座標
- lineTo(x, y): 下一個點的座標
- stroke(): 依據座標繪製線條

``` js
// 開始繪製
ctx.beginPath();
//我們用moveTo(x,y)來指定線的起點座標
ctx.moveTo(50, 50);
//之後使用lineTo(x,y)來指定與前一個座標相連的點
ctx.lineTo(100, 50);
ctx.stroke();
```

繪製後會出現水平的線條

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022081301.png?alt=media&token=52fcd54d-c0cf-4f9e-a37a-e72bb56efbae)

## 三角形

三角形一樣用lineTo指定點的座標，連回原點即可。

``` js
ctx.beginPath();
ctx.moveTo(50, 50);
ctx.lineTo(100, 50);
ctx.lineTo(50, 100);
ctx.lineTo(50, 50);
ctx.stroke();
```

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022081302.png?alt=media&token=ff4ed4e8-ddcc-445d-819c-662750f8947a)

或者在最後用 closePath()可以自動連回原點。

``` js
ctx.beginPath();
ctx.moveTo(50, 50);
ctx.lineTo(100, 50);
ctx.lineTo(50, 100);
ctx.closePath();
ctx.stroke();
```

## 設定顏色與線條寬度

``` js
  // 設定線條寬度
  ctx.lineWidth = 5;
  // 設定線條顏色
  ctx.strokeStyle = '#000';
  // 設定填滿顏色
  ctx.fillStyle = 'red';
  ctx.beginPath();
  ctx.moveTo(50, 50);
  ctx.lineTo(100, 50);
  ctx.lineTo(50, 100);
  ctx.closePath();
  ctx.stroke();
  // 填滿顏色
  ctx.fill();
```

經過設定顏色後的三角形

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022081303.png?alt=media&token=14978bab-5f29-449e-8703-abb9fa462ff6)

## 正方形

正方形一樣可用lineTo指定座標的方式繪製，但canvas有內建繪製正方形的函式。

```
ctx.rect(x,y, w, h) // x,y一樣是座標，w和h是四邊形的寬和高*/
```

``` js
  ctx.lineWidth = 5;
  ctx.strokeStyle = '#000';
  ctx.fillStyle = 'red';
  ctx.rect(50, 50, 100, 100);
  ctx.stroke();
  ctx.fill();
```

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022081304.png?alt=media&token=f59d83c6-8374-4fcc-99ba-85636a4596b3)

## 圓形

圓形的繪製使用 arc() 函式 來完成

``` js
arc(x, y, r, s, e)
// x: x座標
// y: y座標
// r: 圓的半徑
// s: 起點的角度
// e: 終點的角度
```

![s和e角度說明](https://ithelp.ithome.com.tw/upload/images/20180724/2010693504414fOrmj.jpg)

``` js
  ctx.lineWidth = 5;
  ctx.strokeStyle = '#000';
  ctx.fillStyle = 'red';
  ctx.arc(100, 100, 25, 0, Math.PI * 2);
  ctx.stroke();
  ctx.fill();
```

因為 Math.PI 代表 180度，所以從 0度 到 Math.PI * 2 就可以畫出 360度的圓形了。

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022081305.png?alt=media&token=056b1188-e696-4fa9-b3ff-ca9c93fb0997)

若要繪製半圓則改變起始的角度即可

``` js
  ctx.lineWidth = 5;
  ctx.strokeStyle = '#000';
  ctx.fillStyle = 'red';
  ctx.arc(100, 100, 25, Math.PI / 2, Math.PI * 1.5);
  ctx.stroke();
  ctx.fill();
```

















