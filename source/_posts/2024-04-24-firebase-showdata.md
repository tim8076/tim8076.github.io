---
title: Firebase 資料庫 (5) 顯示資料
date: 2024-04-24 14:07:39
categories: Firebase
tags: Firebase 
description: '使用 once 、on 顯示資料到網路上'
---

## once 讀取資料(一次性)

假設今天在firebase裡我們有一筆資料，想寫到網頁上

![](https://cdn-images-1.medium.com/max/1000/1*ClytmEDLd8qAgWmoFffsUg.png)

![](https://cdn-images-1.medium.com/max/1000/1*vhHkCBqqdSCorEUf8nQCVg.png)

可以先用 ref指向資料的位置

![](https://cdn-images-1.medium.com/max/1000/1*gOomVoRZLg80TYhauZmLpA.png)

再利用.once的語法，這個語法可以一次性地讀出資料，並第一個參數指定'value'代表我要取值，在function裡的 snapshot參數就是值，如果要轉換成js可以處理的陣列或物件的話，要再加上.val()。


## on 讀取資料(隨時監聽)

``` js
  const nameRef = firebase.database().ref('myName');
  nameRef.set('mark');
  nameRef.on('value', function(snapshot) {
    document.querySelector('#title').textContent = snapshot.val();
  })
```

on和once一樣可以讀取firebase資料庫的資料，唯一的不同是once只會在載入時讀取一次，on則會即時監聽資料庫的更新。

![](https://cdn-images-1.medium.com/max/1000/1*7vpxCj3XgRpN9-sFNz7FfA.png)

當資料庫的myName更新為 mark12

https://cdn-images-1.medium.com/max/1000/1*_Ni9VnokoGqCEwyhJnULhQ.png

網頁也會即時更新，適合做聊天室等功能。