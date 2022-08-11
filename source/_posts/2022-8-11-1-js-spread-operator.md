---
title: ES6 展開與其餘參數
date: 2022-08-11 14:25:48
tags: 
- ES6
description: '在 ES6 中，新增了一個 "..." 的關鍵字，可做為展開或其餘運算符使用'
---

## 展開

以往合併兩個陣列時，我們會用 concat 語法，如下圖:

![](https://miro.medium.com/max/1020/1*AmR_SWLbqPwMJ6ilqnxCog.png)

在ES6 我們可以用 …groupA展開的語法，意思是將groupA陣列裡的值分別取出，再塞進新的陣列裡。

![](https://miro.medium.com/max/948/1*fVRSfV9FF115WgstFpASxg.png)

## 陣列淺複製

![](https://miro.medium.com/max/1210/1*NjmJV3JkhsaK3OlYF5ZZDw.png)

因為陣列是傳參考的特性，所以上圖中，groupA跟groupB裡面都會有 ‘阿明’

![](https://miro.medium.com/max/1176/1*feuXrhf1hU4vLv5zYE6TfA.png)

如果用...展開的方式，將groupA裡的值一個一個取出，再放進一個新的陣列裡，此時 groupA 跟 groupB 是兩個不同的陣列，groupA不會有 '阿明'

## 類陣列轉為陣列

![](https://miro.medium.com/max/1130/1*nccwenEmifGe5qlT5aSaxQ.png)

由於類陣列 nodelist不是陣列，無法使用陣列方法，所以利用展開的方式，將類陣列 nodelist 裡的值取出後，放入新陣列中。如此newDoms就是一個新的陣列，可以使用陣列的方法。

## 物件的合併

![](https://miro.medium.com/max/1022/1*UZtmGDckziMEOj8HIjUWTw.png)

![](https://miro.medium.com/max/436/1*Oyz0bvL-lb70I2xfb_AjsQ.png)

利用展開語法 ，將兩個物件放入一個新的物件合併，personTwo會複寫與personOne重複的屬性，多的則加入。

## 其餘參數

我們可以用 其餘參數來取得不確定數量的參數。如果函式的最後一個命名參數以 ... 開頭，它會被視為一個陣列，並將所有參數存入陣列中。

![](https://miro.medium.com/max/1056/1*QrBRIz50E_WVBnaszhnX7Q.png)



