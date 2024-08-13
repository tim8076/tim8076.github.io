---
title: (0-1) CSS基礎篇 自行hosting google font
date: 2022-06-20 11:21:54
tags: 
- CSS基礎篇
categories: CSS
description: '自行託管 google font'
---

## 為什麼要自行hosting google font

以前當我們在使用 google font時，大多會用 cdn 的方式來載入字型。但自行hosting google font
，有以下好處:

- 加快網路載入速度: 自行hosting，不必像 CDN 一樣向 server申請字型資源，可以讓網頁載入速度更快。

- 降低網頁跑版問題: 使用cdn載入字型，可能因為載入字型的時間，導致網頁暫時跑版。自行hosting可避免此問題。

## 自行hosting 方法

1. 來到 [google font 官網](https://fonts.google.com/)

2. 選擇你想使用的字型，點選下載

![](https://cdn-images-1.medium.com/max/1000/1*b7lVRh_6Qnp4Vbg4iLS3Qg.png)

3. 解壓縮下載好的字型，

![](https://cdn-images-1.medium.com/max/1000/1*WNvYUqKLJrCKJ8j29jQ9MA.png)

4. 來到 [fontsquirrel](https://www.fontsquirrel.com/tools/webfont-generator)，點選上傳檔案，將字型檔案壓縮。

![](https://cdn-images-1.medium.com/max/1000/1*vzsTfF4EZmNV6cwQDeHueQ.png)

5. 下載壓縮好的字型到網頁專案資料夾

![](https://cdn-images-1.medium.com/max/1000/1*4JlORBm4mAKD7LIwc6_Nvw.png)

6. 在 scss 檔案裡用 @font-face 載入字型，@font-face 裡的 src 指向你存放字型檔案的位置。

``` scss
@font-face {
  font-family: 'Roboto';
  font-weight: 900;
  src: url('../../font/squeez/roboto-black-webfont.woff2') format('woff2'),
       url('../../font/squeez/roboto-black-webfont.woff') format('woff')
}

body {
  font-family: 'Roboto', sans-serif;
  font-weight: 900;
}
```




