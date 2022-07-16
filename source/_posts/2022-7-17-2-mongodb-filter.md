---
title: MongoDB (三) 進階搜尋
date: 2022-07-16 20:14:57
tags: MongoDB
description: '進階搜尋modgodb物件'
---

## 進階搜尋

使用進階搜尋，在find({ })裡的物件的值要再使用物件指定

``` 
$eq: 搜尋相等的值
```

![搜尋name等於arod的資料](https://miro.medium.com/max/762/1*z5MdNdvkq8vgc0e2YSaP1g.png)

```
$in: 搜尋多筆資料
```

![搜尋name為 Tom跟Lisa的資料](https://miro.medium.com/max/963/1*kBWhGNWTVIlDcXn3sms-Uw.png)

```
$nin: 搜尋多筆不等於的資料
```

![回傳name不等於 Tom跟Lisa的資料](https://miro.medium.com/max/963/1*6V7wGbsl4V5OqWhKdQ-K9Q.png)

```
$ne: 搜尋不等於值的所有結果
```

![回傳name不等於john的結果](https://miro.medium.com/max/855/1*AHLxw1weSOF3PnMcaqI7uw.png)

```
$gt: 回傳大於的值
```

![回傳age> 13的值](https://miro.medium.com/max/766/1*Ew8Ue57MPOcuQxSGD3rRbg.png)

```
$gte: 回傳大於等於的值
```
![](https://miro.medium.com/max/756/1*Ivi-dmvotfSyyWd7EveN3g.png)

```
$lt: 回傳小於的值
```
![](https://miro.medium.com/max/769/1*mnWWPxKd6nSCiOiRbieExw.png)

```
$lte: 回傳小於等於的值
```

![](https://miro.medium.com/max/824/1*0HjXji2L2aFrS4IBvwmeKw.png)

```
$exits: 回傳欄位存在的值，true是存在，false是不存在
```

![回傳有age欄位的值](https://miro.medium.com/max/875/1*KAN637IjOrmlSVPrBlEMsg.png)

```
$not: 回傳不符合條件的資料
```

![回傳 age不是小於等於40的資料](https://miro.medium.com/max/963/1*2k8b8OlsJcrAZrHudnosBg.png)

## 多重尋找

![尋找 age >=15且 <=40 且 name為sara的資料](https://miro.medium.com/max/963/1*VvL-74sVwh2oo8hz4JZZtA.png)

```
$and: 尋找條件都符合的資料
```

![尋找 age =19且 name為sara的資料](https://miro.medium.com/max/963/1*rteWbRZYyhxGxvg8NZb5UA.png)

```
$or: 尋找條件之一符合的資料
```

![回傳age≤40 或 name為john的資料](https://miro.medium.com/max/963/1*AozlkrEyLbEUhTafgXYNGw.png)

```
$expr : 後方可放入表達式，欄位名稱要加上 $
```

![回傳 $debt > $balance的資料](https://miro.medium.com/max/963/1*-nFA_bUG5XsbTkx7GOXYTA.png)

## 深層尋找

如果資料裡還有物件，屬於巢狀結構的話，使用.的方式尋找

![回傳 address裡street的值為 978 st的值](https://miro.medium.com/max/963/1*bZSPltOMgAxaj5xEnnSqKw.png)

```
$findOne: 回傳找到的第一筆資料
```

![回傳age>10的第一筆資料](https://miro.medium.com/max/803/1*v1g2nEa4VAjP4GQQVKqd2w.png)

```
$countDocument: 計算資料筆數
```

![回傳age≤40的筆數](https://miro.medium.com/max/963/1*52BUktA6BLIWuFDebslMkw.png)
