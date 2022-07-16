---
title: MongoDB (二) 新增與尋找
date: 2022-07-16 10:21:01
tags: MongoDB
description: '新增資料到MongoDB'
---

## 新增單筆資料

![](https://miro.medium.com/max/1400/1*gVW--Mwzkr8MGyRqEAiJqQ.png)

``` js
insertOne() // 新增單筆資料
```

使用insertOne()語法，在users這個collection裡面新增一筆資料(document)，資料以物件形式加入。

## 新增多筆資料

![](https://miro.medium.com/max/1400/1*iifEjaw0vesRmNJuc55dJA.png)

``` js
insertMany([])  // 加入多筆資料，每筆資料為物件格式。
```

## 尋找資料

1. 尋找所有資料
![](https://miro.medium.com/max/1400/1*u24PrSDc2Y_O9za1Sd5cVg.png)

使用 find()，將collection 裡的所有資料(document)列出，可以看到在mongoDB裡，每一筆資料的格式可以不同，也能在物件裡再放物件格式。

2. .find({ 搜尋條件 })， 尋找指定資料

![](https://miro.medium.com/max/1400/1*1y28loJEsDtZ7HFlUP8VDw.png)

3. find({ 搜尋條件 }, { 需要欄位}): 尋找指定資料，並只回傳需要的欄位，1 代表要回傳的欄位, 0代表不要回傳的欄位

![只回傳 name 跟 age的欄位](https://miro.medium.com/max/1400/1*rd21DIRvfdpCTdqRS-l0Dw.png)

![回傳age以外的欄位](https://miro.medium.com/max/1400/1*__9L7fjSlJVkfnh569nIdw.png)

## 篩選資料

1. 限制搜尋筆數: .limit(筆數)

![](https://miro.medium.com/max/1400/1*fslx_qLREPu8Do0OA-iOSw.png)

2. 資料排序: sort( {}):

物件key值為要排序的屬性， value為 1(降冪) 或 -1 (升冪)

![](https://miro.medium.com/max/1400/1*GDXlcgddlVyMXtV_YSXm3A.png)

3. 多條件排序

![](https://miro.medium.com/max/1400/1*6l6JUe1cSsM3b1DxQi1mGQ.png)

sort()裡可放多屬性，會依照屬性順序做排序，如上圖會先將age做排序，若age一樣再用name做排序。

4. 跳過項目 .skip(跳過數量)

![掠過第一筆資料](https://miro.medium.com/max/1400/1*0G0NEDl6BejHTCqxO5DK7Q.png)


