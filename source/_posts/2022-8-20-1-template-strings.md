---
title: ES6 樣板字面值
date: 2022-08-20 15:57:02
tags: 
- ES6
description: '使用 ES6 樣板字面值'
---

## ES6 樣板字面值

![](https://miro.medium.com/max/1400/1*5YA_01lRWRrI6JmEpZ_nKw.png)

在以前，當我們需要在JS中加入字串和變數時，需要用 ' ' 來相加，有時不太方便。在ES6以後，我們有了新的組字串方法，樣板字面值。

在ES6以後，我們有了新的組字串方法，樣板字面值

1. 使用 ` `將字串包住
2. 樣板字面值包含由錢字元及花括號所構成（${expression}）的佔位符號。
3. ${ }內 可以加入變數，或是表達式。

所以上圖我們可以修改為:

![](https://miro.medium.com/max/1266/1*a29DtXuoV377hfJWerohaQ.png)

${} 也可插入函式，如下圖插入了立即函示:

![](https://miro.medium.com/max/1400/1*nNF7L_S13WZmghpY0M9_fA.png)

## 巢狀結構

樣板字面值內，還可以插入另一組樣板字面值。

![](https://miro.medium.com/max/1400/1*XYoDm5T10uE29wpd_ZPNDg.png)

也可直接在${ }內做函式運算

![](https://miro.medium.com/max/1400/1*RxYStv56lZ9Rs8OqQWWjUA.png)



