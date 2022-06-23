---
title: (8) Git 練功坊-推送分支到遠端
date: 2022-06-23 14:55:16
categories: Git
tags: 
- Git
description: '推送分支到遠端數據庫'
---

## 推送分支上 github

本節會講解如何推送branch到github上。

首先我們先開一個新的分支，並用git checkout 分支，移動到該分支上。

![add branch](https://miro.medium.com/max/1400/1*gN684t4CgXrmbfitc8Ro2A.png)

再來新增一個commit 記錄到該分支

![commit](https://miro.medium.com/max/1400/1*9GKiKFBMWI50hjFgxLm7QA.png)

這時如果用git push指令想將本地端的commit推到github上，可能會出現下面錯誤。

![error](https://miro.medium.com/max/1400/1*050HdBhOzj3125XCFpOFzg.png)

原因是因為我們可能有許多遠端數據庫，有的是測試用的、有的是正式主機用的，git不知道你的分支要推到哪個數據庫。

所以可用 git remote 指令來查詢本地端有多少遠端數據庫。

![remote](https://miro.medium.com/max/1208/1*ZV4Dyk2Rq2l36mbNiGNxWA.png)

可以發現有一個 github 預設的 origin 數據庫。

要將分支推上github 的話 ，可使用指令:

```
git push 遠端數據庫名稱 分支名稱
```

![push](https://miro.medium.com/max/1268/1*avTlKgGgw8qFA08F88x_Pg.png)

## 更改遠端數據庫名稱

如果不想用github預設的origin數據庫名稱，可輸入: 

```
git remote rename 更改前名稱 更改後名稱
```

![rename](https://miro.medium.com/max/930/1*wNOekbkp-5Gsu3iiFVHGvQ.png)

在用 git remote來查詢， 會發現數據庫名稱從 origin 改成 github了。

![git-rename](https://miro.medium.com/max/1400/1*6DAh5wMtkOZ-ga1uvU__fw.png)




