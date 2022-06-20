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

通常我們會有一個 all.scss ，裡面放其他要載入的SCSS檔。

這個檔案就會有一堆 @import，編譯出來的CSS檔案就會依照@import的前後排列來依序產生CSS碼。

1. @import最前面的檔案裏面一定都會先放全域變數、mixin、function等，這樣後面的檔案 才吃的到變數的設定。

2. 再來是 reset、base等全站共用的樣式。

3. layout可以網頁版型的共通設計，如表頭、表尾。

4. 再來就index首頁、page內頁，再來就看你的單元數量視情況來切割。

引入參考順序

``` scss
// variables
@import './abstract/functions';
@import './abstract/variables';
@import './abstract/media-query';

// base classes
@import './base/reset';
@import './base/base';
@import './base/typography';

// utils
@import './utils/utils';

//layout
@import './layout/grid';

//pages
@import './pages/index';

//components
@import './components/button';
```













