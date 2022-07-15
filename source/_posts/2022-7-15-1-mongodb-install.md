---
title: MongoDB (一) 安裝MongoDB與基礎指令
date: 2022-07-15 11:04:59
tags: MongoDB
description: '安裝MongoDB，並介紹基礎指令'
---

## MongoDB是什麼?

MongoDB 是一個開源的「NoSQL ( 非關聯性 ) 文件資料庫」，具有以下優點:
- 不須先創立數據表格，且數據格式自由
MySQL 須創建表格讓 MySQL 抓取數據，而 MongoDB 不需事先創建表格，也能將數據直接寫入並彈性添加欄位，且欄位的格式較自由，例如:欄位使用數字或是字符串皆可。
- 可以處理json結構
MongoDB 將資料儲存為文件（類似 JSON 物件），以 field-value 為結構成對儲存，value 可以包含值、文件、陣列、文件陣列，讀取欄位內的數值。

## 安裝MongoDB

到[此網站](https://www.mongodb.com/docs/manual/administration/install-community/) 安裝mongoDB

![](https://miro.medium.com/max/1400/1*FCigXxB4Kis3PZ85fq2xiw.png)

到[此網站](https://www.mongodb.com/docs/mongodb-shell/install/) 安裝 mongosh(連線到mongoDB會用到的工具)

![](https://miro.medium.com/max/1400/1*pLlEilk0USrVukdgBbCKug.png)

安裝好後，打開終端機輸入 mongosh，會顯示目前安裝的mongoDB版本。

![](https://miro.medium.com/max/1400/1*_2EgvYu5TghFeA6_a7R2hw.png)

## 基礎指令

`show dbs `: 顯示目前有的資料庫

![](https://miro.medium.com/max/604/1*ZY3KbCmUBn6qjpZSbP1UYw.png)

`use 資料庫名稱`: 新增資料庫

![](https://miro.medium.com/max/640/1*8sW3YtdIxNhjE7ItSA-mCQ.png)

`show collections` : 顯示資料庫裡的collections

`db.dropDatabase()` : 刪除目前資料庫

![](https://miro.medium.com/max/840/1*bwoP97w5Dk7fMWbJBF8PUA.png)

`cls` : 清除終端機指令

`exit` : 離開mongosh，回到終端機




