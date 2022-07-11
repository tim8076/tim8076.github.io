---
title: (6) Node.js 內建模組
date: 2022-07-11 14:37:26
categories: Node.js
tags: 
- Node.js
description: '介紹其他Node.js內建模組'
---

## OS模組(operating system模組)

os 提供了一些基本的系统操作函数，首先載入模組

``` js
const os = require('os');
```

![os](https://miro.medium.com/max/942/1*N07WqfVXhpTjXTv7Tc1TSA.png)

![os](https://miro.medium.com/max/982/1*VhskxuDYl8iPxJWp8vrKcA.png)

上圖中顯示 userInfo和 uptime

![os](https://miro.medium.com/max/954/1*gUiWv1LYXUv5DWUh3zdlvg.png)

![os](https://miro.medium.com/max/786/1*HDXgZT45S93ydYeiIPVnIA.png)

上圖顯示，使用者系統名稱如windows和相關記憶體資料。

## Path模組

再講 path模組前，先介紹兩個功能 

``` js
__dirname : 回傳檔案目錄位置
__filename : 回傳檔案目錄位置(包含檔名)
```
![__dirname，__filename](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022071114.png?alt=media&token=e85ea62f-4e45-47fe-8746-55740d27bc8f)

nodeJs裡有一個 path 模組，可用來取得檔案與目錄路徑，詳細也可瀏覽 [Node.js PATH API文件](https://nodejs.org/api/path.html)

- 抓目錄路徑： path.dirname(‘/xx/yy/zz.js’) 回傳 /xx/yy
- 路徑合併：path.join(__dirname,'/xx') 回傳 前後路徑合併
- 抓檔名： path.basename('/xx/yy/zz.js') 回傳 zz.js
- 抓副檔名： path.extname('/xx/yy/zz.js') 回傳 js
- 分析路徑： path.parse('/xx/yy/zz.js') 回傳 上述綜合物件

### 絕對路徑: path.resolve()

path.resolve()方法用於將path-segments序列解析為絕對路徑。它通過處理從右到左的路徑順序來工作，在每個路徑之前添加，直到創建絕對路徑為止。

![path](https://miro.medium.com/max/1400/1*RzS_lXFO03QUo1fP5D5xkA.png)

![path](https://miro.medium.com/max/1400/1*2Yq7Z3y8Dh5AGiDVMvvBWA.png)






