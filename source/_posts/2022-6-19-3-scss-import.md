---
title: (4) SCSS練功坊-import
date: 2022-06-19 15:14:55
categories: scss
tags: 
- scss
description: '模組化你的scss檔案'
---

## 模組化管理
以往寫css時，所有的code都寫在同一份css檔案裡，當code越來越多，就越難維護與管理你的css。
在scss裡，我們可以將檔案進行模組化管理，方法如下:

我們會有一個主要的scss檔案，在這個 scss 檔裡我們會import其他模組的scss檔進來，只有這個主要的scss檔案最後會被編譯成css。

![all.scss](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022061901.png?alt=media&token=baae5c4a-b4de-4b55-a04f-9681653bf7d1)

至於其他被引入的scss，我們會在檔案名稱前加上 「 _ 」 ，如「_reset.scss」， 加了 _ 的檔案就不會被編譯成 css。

![module](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022061902.png?alt=media&token=61fab007-d152-47c8-ae03-ce4a073e3391)

## 引入順序

引入檔案時順序是有影響的，先引入的檔案內容才能被之後的檔案讀取。所以如果有變數、function等這些所有檔案都須用到的模組，要先載入，之後的scss檔才讀取的到這些變數與funciton。









