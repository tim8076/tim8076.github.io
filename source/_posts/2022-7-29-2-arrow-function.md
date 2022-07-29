---
title: ES6 箭頭函式
date: 2022-07-29 17:48:02
categories: Javascript
tags: 
- ES6
description: '使用箭頭函式取代傳統函式'
---

## 箭頭函式

箭頭函式(Arrow Functions)是ES6後提供的新的函式撰寫方法，箭頭函式省略 function ，並在小括號後 加上 => 
寫法如下: 

``` js
([param] [, param]) => {
   statements
}
```

## 縮寫

![](https://miro.medium.com/max/1186/1*ESxQlngtFWX4n1s2aenzaA.png)

另外如果程式碼只有一行 ，可將{ }省略，並且不用寫 return，因為 箭頭函式 預設就有return；

![](https://miro.medium.com/max/1170/1*9IF91hfHL3P8GkqFRKEEqg.png)

如果參數只有一個，小括號 ( )也可省略

![](https://miro.medium.com/max/1084/1*kDJRvdiX4f8BFUVfA7F7hg.png)

若沒有參數，小括號 () 不可省略

## 沒有 this

和傳統函式不同，箭頭函式沒有自己的this，所以它的this會沿用外層的this

![](https://miro.medium.com/max/1106/1*JQNWRCFVt4ScYCqNoFSHlw.png)

## 常見問題

### 無法回傳 物件實字

因為 物件的 { } 會被當作 箭頭函式結構的一部分，導致無法回傳物件。

![](https://miro.medium.com/max/778/1*mynKPfZszhSThbM3JLrYoQ.png)

解決方法是在 物件外 加上 ( ) 包住

![](https://miro.medium.com/max/862/1*jnDAY_EmMmMf9LFwbGRnrQ.png)

### 搭配判斷式時，不能直接接箭頭函式

![](https://miro.medium.com/max/730/1*OR1_s2JDhdFL2y60Da27tw.png)

解決方法依樣在外面加上 ( )

![](https://miro.medium.com/max/804/1*E_mYA5m_ncwWoXN--eIi8w.png)







