---
title: (1) Node.js 安裝
date: 2022-07-10 20:36:40
categories: Node.js
tags: 
- Node.js
description: '安裝流程介紹'
---

## 什麼是 NodeJs

![v8引擎](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/20220710.png?alt=media&token=094bcae5-8d76-462f-95e1-8ad790ab0fcd)

Node.js是一個基於V8 JavaScript引擎的JavaScript執行環境，透過V8引擎將JavaScript程式碼編譯成機器語言讓電腦運作。除了nodeJS以外，像Chrome瀏覽器也使用了 V8 引擎來執行JavaScript。

## 安裝 nodeJs

安裝nodeJs我們會先下載 [nvm](https://github.com/coreybutler/nvm-windows/releases/tag/1.1.7)(nodeJs版本管理工具)，
選擇這個檔案下載
![setup](https://cdn-images-1.medium.com/max/1100/1*MMtq_QXGr8WOb0PZBG38Gg.png)

```
nvm -v  // 查看安裝版本
```

## nvm 指令

nvm 可用的指令有這些: 

- nvm list : 查看已安裝的版本
- nvm list availabel : 查看可安裝的NodeJs版本
- nvm install 版本號 :  安裝指定版本的NodeJs
- nvm use 版本號 : 指定NodeJs版本

輸入 nvm list available 確認可用的nodeJs版本 (選擇LTS穩定版)

![可用版本](https://cdn-images-1.medium.com/max/1100/1*M3IU0v3oSFGFJ4tN31Awrw.png)

輸入 nvm install 版本號  下載nodeJs

![nvm install](https://cdn-images-1.medium.com/max/1100/1*f1MaLlOhzZk_xukIsqFfrA.png)

安裝好後，可輸入 `node -v` 確認安裝的nodeJs版本。

因為下載nodeJs時，會順便下載npm，輸入npm -v 來確認版本。

![npm -v](https://cdn-images-1.medium.com/max/1100/1*RkuPmVE75hwZt_PIwmX8SA.png)
