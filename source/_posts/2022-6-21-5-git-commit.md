---
title: (2) Git 練功坊-紀錄修改與提交
date: 2022-06-21 15:52:38
categories: Git
tags: 
- Git
description: '提交修改紀錄'
---

## 新增資料並加入索引

上一章節已經將專案的數據庫建立好了，那我們先在專案內新增一些資料，我先建立一個 「sample.txt」的文字檔案，並在裡面打一些內容。

此時我們可以將新增的資料加入索引，加入索引的檔案之後才能被commit 提交，方法如下:

- git add .   將所有更新的檔案加入索引。
- git add 檔案名稱  將特定檔案加入索引。

## 查詢檔案狀況

```
git status  // 查詢目前檔案狀況
```

![git status](https://miro.medium.com/max/1268/1*0-Hunc2dByNVE3AeTQPTyQ.png)

上圖中綠色是已加入索引，紅色是未加入。

若要取消加入索引，可用

```
git reset HEAD : 取消已加入索引的全部檔案，此時檔案會呈現未追蹤狀態。
git reset HEAD 檔案名稱: 取消已加入索引的單個檔案，呈現未追蹤狀態。
```

## 提交檔案

若確認檔案都加入索引後，可以將索引內的檔案提交到數據庫

```
git commit -m "更新內容"
```

我們使用 git commit 將本次的更新提交到數據庫，-m 可以輸入更新的內容重點。
通常我們會在專案開發完某個功能後，做一次commit。例如完成首頁輪播功能，或切完首頁版型等等，方便之後做版本切換。

![commit](https://miro.medium.com/max/1400/1*rM-6FClWTQvcFPXmYmq8JQ.png)







