---
title:  (10) CSS 基礎篇 margin-padding
date: 2024-06-25 09:48:11
categories: CSS
tags: 
- CSS基礎篇
description: '了解  margin 和 padding 的使用方式'
---

## 基礎介紹

- margin: 控制物件的外部距離
- padding: 控制物件的內部距離

可以接受的值如 `px、%、em、rem、vw、vh`

設定方法可分為一到四個值

``` css
/* 四個值 分別設定 */
margin: 上 右 下 左

/* 三個值 */
margin: 上 [左右] 下

/* 兩個值 */
margin: [上下] [左右]

/* 一個值 */
margin: [上右下左]
```

## margin 用法

margin 用來設定物件與周圍物件的距離

``` css
.box {
  width: 100px;
  height: 100px;
  margin: 10px;
}
```

如上 .box 的寬高為 100px，又向外推了 10px 的 margin 空間，總共佔 110px 的空間。

### 用 auto 水平居中

可以用 `margin: 0 auto`，來做水平居中，auto 的用途是將父層剩餘的空間分配給具有這個值的位置。

``` css
.box {
  width: 100px;
  margin: 0px 0px 0px auto; // 物件靠右
}
.box2 {
  width: 100px;
  margin: 0px auto; // 物件水平置中
}
.box3 {
  width: 100px;
  margin: 0px auto 0px 0px; // 物件靠左
}
```

### 使用百分比單位

當 margin 使用 % 為單位時，是以父層的 content-box 為百分之百。所以設定 margin-left: 10% ，表示為父層 width寬度的 10%。

## padding 用法

padding 是用來設定物件 border 到資料之間的留白空間，稱為「內距」。
當設定 padding 後，padding 的空間會添加到元素的寬高之外，border 以內，padding 空間會顯示背景色彩。




