---
title: (6) Git 練功坊-建立分支
date: 2022-06-23 11:08:59
categories: Git
tags: 
- Git
description: '建立不同分支'
---

## 什麼是分支？

分支是為了將修改記錄的整體流程分開儲存，讓分開的分支不受其他分支的影響，所以在同一個數據庫裡可以同時進行多個不同的修改。

當我們輸入完 git init 後，並完成第一次提交後(commit)會自動產生一個 main 分支，在建立其他分支前，所有紀錄都存在main分支上。

## 建立分支

要建立一個新的分支，可以用

```
git branch 分支名稱
```

![branch](https://miro.medium.com/max/1206/1*MM7zD5dXszOgNHn_UcqtOg.png)


要查詢目前有的分支可以輸入

```
git branch
```

![brach](https://miro.medium.com/max/1134/1*8p-_J_x4kqDFcnO15JBRLQ.png)


此時用git branch 去查詢，可以發現多了 feature1 分支，但目前所在分支還是master。


## 切換分支

假設目前有 master 分支和 feature1分支，我現在在master分支上，想切換到 feature1分支，可用:

```
git checkout 分支名稱
```

![checkout](https://miro.medium.com/max/1218/1*Gzf7OBa_JANOziPgnxYaVQ.png)


## HEAD標籤

HEAD是目前所在位置的指標，會跟隨在最新的commit上面，如下圖:

![head](https://miro.medium.com/max/680/1*vBHV9Vo4Ws2O4a_AfGPdig.png)


在git裡的每個commit都有自己的代碼，我們可以用 git log 查詢所有 commit 紀錄。

![commit](https://miro.medium.com/max/1272/1*fcmwOhm5NG9_XpjeoFhPxw.png)

如果想看前一版本commit紀錄裡做了哪些事，可以透過指令將HEAD移動到該commit版本上，看完後再移動回最新的commit上。

``` 
git checkout commit前四碼
```

![checkout](https://miro.medium.com/max/676/1*ItxAAKHhndN-_oToicuXnw.png)

分支的切換其實也就是將HEAD移動到不同分支標籤上而已。

## 分支移動

是 Git 中用來**移動分支指向某個提交（commit）**的指令。

```
git branch -f <分支名稱> <提交位置>
```

- -f 或 --force：強制操作，不管這個分支目前在哪裡指向，都會移到新的位置。
- <分支名稱>：要移動的分支名稱。
- <提交位置>：可以是 commit hash、HEAD、HEAD~1 等。









