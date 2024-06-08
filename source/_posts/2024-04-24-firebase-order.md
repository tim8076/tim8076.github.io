---
title: Firebase 資料庫 (7) 資料排序
date: 2024-04-24 16:40:08
categories: Firebase
tags: Firebase 
description: '使用 orderByChild 排序資料'
---

## 資料排序

在firebase中，如果想對資料作排序可以用 ` orderByChild() `語法搭配 ` forEch() `語法。

![](https://cdn-images-1.medium.com/max/1000/1*6KW8RQdpyEMZqUAljK-bLg.png)

![](https://cdn-images-1.medium.com/max/1000/1*Rvu0eLayL6Oq0YfUeKekTw.png)

我們有一筆people物件的資料，先讀取物件的路徑。

![](https://cdn-images-1.medium.com/max/1000/1*r5g4ZluzPf8uBaqFK9r3-w.png)

在peopleRef路徑後先用 orderByChild()，決定排序屬性是height身高、old年齡或weight體重，再用once去讀出資料。
在 once 的 function 裡用 forEach 去將排序後的資料一一讀出，這邊的 forEach 是 firebase 的語法，不是 js 裡的語法。

## orderByChild 排序規則

![](https://cdn-images-1.medium.com/max/1000/1*-bZo1rwFvWKNgZeDebYikA.png)

![](https://cdn-images-1.medium.com/max/1000/1*tBqWw0TWQzT99eKJOCNbKg.png)

假設今天 orderByChild 針對 height 屬性作排序，height 屬性的值有不同型別如 null、數字、字串 、物件等，排序規則如下:

```
null > false > true > 數字 > 字串 > 物件
```
排序結果如下:

![](https://cdn-images-1.medium.com/max/1000/1*tg-jW512rdPciOfT8rF1Yg.png)


