---
title: (4) Git 練功坊-遠端數據庫
date: 2022-06-21 17:05:13
categories: Git
tags:
  - Git
description: "新增 github 遠端數據庫"
---

## 遠端數據庫

之前介紹過如何再本地端提交更新，今天要教大家將本地端的更新提交到遠端數據庫(Github)。

## 註冊 Github

我們要先去 [GitHub](https://github.com/) 註冊會員。

![github](https://ithelp.ithome.com.tw/upload/images/20190908/20119923T2oDPSuQK3.png)

## 新建一個 repository

註冊好帳號後，可以在 github 上新建一個 repository 數據庫

![repository](https://miro.medium.com/max/1400/1*7xMLMI0zZ87X4s9Hi4EIHg.png)

這邊填寫數據庫名稱

![repo-name](https://miro.medium.com/max/1400/1*PdIfUXuiD4hS1HDjNyhU7w.png)

## 複製遠端數據庫到本地端

新開一個專案資料夾並移動進去

輸入:

```
git clone 遠端數據庫網址
```

輸入完後，會將遠端新增的 repository 複製到本地資料夾內。

![git-clone](https://miro.medium.com/max/1400/1*TRv6Lzld1DosUcNDlJWErQ.png)

## 推送資料到遠端數據庫

在本地端新增資料，並照上個章節的做法 commit 完以後，就可以將 commit 上傳到遠端資料夾內囉。

```
git push  // 將資料推到遠端
```

![上傳成功](https://miro.medium.com/max/1400/1*7mwBekzTKtNV_DHCBs_txg.png)

## 從遠端下載資料

若遠端資料庫的資料有更新，比如說其他同事有 push 新的資料上去，那我們有兩種方式將資料下載下來。

```
git pull  // 從遠端拉取資料下來，並直接合併
```

執行 git pull 會將遠端更新的資料下載下來，並且會直接合併。

```
git fetch  // 從遠端拉取資料下來，但不合併
```

執行 git fetch 也會從遠端下載資料下來，但不會直接合併，而是以新的 commit 呈現。
等確認這些新的 commit 內容 ok，可以再自行用 git merge 合併進專案。

```
語法
git merge origin/master
```

## 語法介紹

遠端儲存庫(Repository)操作

- 註冊遠端儲存庫：git remote add <遠端數據庫簡稱> 遠端儲存庫網址
- 更新資料到遠端 master 分支：git push -u origin master
- 觀看遠端數據庫列表：git remote
- 觀看遠端數據庫列表(包含 rul)：git remote -v
- 下載遠端數據庫：git clone <url>
- -u 是指他預設會推到哪個遠端數據庫服務
- origin 可以改它的遠端數據庫名稱，例如 git push -u github master
