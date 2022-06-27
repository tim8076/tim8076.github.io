---
title: (1) Js進階 requestAnimationFrame
date: 2022-06-27 16:05:47
categories: Javascript
tags: 
- Js進階
description: '利用requestAnimationFrame製作動畫'
---

## 製作動畫

在以前用Js中做動畫，可能會用 setInterval()或setTimeOut()，而現在有了更好用的API `requestAnimationFrame`。

## requestAnimationFrame

requestAnimationFrame是依照瀏覽器更新的頻率(通常是 1 /60 秒)來更新畫面。

``` js
let boxLeft = 0;

function main(currentTime) {
  boxLeft += 0.1;
  console.log(currentTime);
  box.style.setProperty('--left', boxLeft);
  window.requestAnimationFrame(main);
}

window.requestAnimationFrame(main);
```

requestAnimationFrame在約1/60秒後呼叫傳給它的callback函式(main)，
並且將timestamp當做參數傳給這個callback函式。
 
為了讓 requestAnimationFrame 能持續執行，我們在callback函式再執行一次 requestAnimationFrame。

如果把 timestamp console.log 出來，會發現timesatmp是以每6豪秒持續累加。

![timestamp](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022062701.png?alt=media&token=c961a215-9334-4ef0-a5e9-dd9408fb16a3)

[範例](https://codepen.io/tim-chou/pen/eYMOVGR)

## 控制更新頻率

每6毫秒更新一次函式可能太快了，假設我們希望每秒更新一次畫面就好，可如下設定

### 紀錄上次更新時間

``` js
let lastRenderTime = 0;

function main(currentTime) {
  window.requestAnimationFrame(main);
  const secondSinceLastRender = (currentTime - lastRenderTime) / 1000; // 將milisecond 轉成 second
  lastRenderTime = currentTime;
  console.log(currentTime);
}
```
可以先設一個變數用來記錄上次更新畫面的時間(lastRenderTime)，然後在函式中用currentTime減掉lastRenderTime，就可以得到從上次更新到這次過了多久時間(毫秒)，可以將時間除 1000 轉換成過了幾秒。

![second](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022062702.png?alt=media&token=6ebc37f7-3bc4-4e9b-a951-4533190544ef)

可以發現每次更新的間隔時間約是 6 毫秒。

### 設定更新門檻

``` js
const SPEED = 2; // 每秒更新次數

function main(currentTime) {
  window.requestAnimationFrame(main);
  const secondSinceLastRender = (currentTime - lastRenderTime) / 1000; // 將milisecond 轉成 second
  if (secondSinceLastRender < 1 / SPEED) return;
  lastRenderTime = currentTime;
  console.log('render');
}
window.requestAnimationFrame(main);
```
先設定SPEED變數代表每秒更新次數，在main函式裡增加判斷

``` js
if (secondSinceLastRender < 1 / SPEED) return;
```
用 1 除以 SPEED 可以得到每零點幾秒才能更新，上例是0.5秒更新1次，也就是每秒更新2次。
當 secondSinceLastRender 小於更新頻律，就將函式 return 不執行。

以上就完成控制更新頻律的方法了。









