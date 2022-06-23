---
title: (5) Git 練功坊-合併與衝突
date: 2022-06-23 10:51:11
categories: Git
tags: 
- Git
description: '合併修改記錄'
---

## 合併與衝突

上章節講過我們可以用 git pull 或 git fetch 來下載遠端更新的內容。
如果遠端數據庫和本地端數據庫的同一個地方都發生了修改的情況下（例：檔案中同一行的地方）。
這時，因為Git不能自動判斷要導入那一個修改內容於是就會發生錯誤。


``` html
    <div class="container">
<<<<<<< HEAD
      <div>我是 Cat</div>
=======
      <div>我是 Dog</div>
>>>>>>> dog
    </div>
```

此時發生衝突的地方必須手動修改，如上例，VScode會提醒你產生衝突的地方，此時再決定要留 cat 還是 dog。





