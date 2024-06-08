---
title: Firebase 資料庫 (3) 取得 網路應用程式
date: 2024-04-23 21:13:06
categories: Firebase
tags: Firebase 
description: 'Firebase 資料庫環境設定'
---

首先請點一下左上「專案總覽」返回專案首頁

![](https://cdn-images-1.medium.com/max/1000/1*yS9r1FTI0PTSFJvDDkRwNg.png)


選擇網頁應用程式 </>符號，來將 firebase 新增到網頁應用程式
註冊完畢後底下就會立刻出現 Firebase 的 SDK，分別是 npm 與 script，這邊請選擇 script 標籤，接著複製下「firebaseConfig」的部分。

``` js
const app = firebase.initializeApp({
  apiKey: '<your-api-key>',
  authDomain: '<your-auth-domain>',
  databaseURL: '<your-database-url>',
  projectId: '<your-cloud-firestore-project>',
  storageBucket: '<your-storage-bucket>',
  messagingSenderId: '<your-sender-id>',
  appId: '<your-app-id>'
});
```

由於 Firebase 後來更新有兩個版本，本課程主要是以 Firebase v8 作為主要授課內容，但是官方 Firebase 所提供的是 Firebase 9，因此底下提供Firebase v8 的 CDN 以及準備好的 CodePen 給大家方便後續課程練習

Firebase V8：[https://codepen.io/hsiangfeng/pen/eYVwKqQ]()

這邊提供 [Firebase 文件網址](https://firebase.google.com/docs/database/web/start?authuser=1&hl=zh-tw)，官方文件的閱讀方式主要也有區分 V8 V9，只需要點一下上方分類標籤就可以切換語法囉。

可以開一個html檔，在 head 標籤引入 script，來看database 是否能讀取了

``` html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="https://www.gstatic.com/firebasejs/8.9.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.9.1/firebase-database.js"></script>
  <script>
    const config = {
      apiKey: '<your-api-key>',
      authDomain: '<your-auth-domain>',
      databaseURL: '<your-database-url>',
      projectId: '<your-cloud-firestore-project>',
      storageBucket: '<your-storage-bucket>',
      messagingSenderId: '<your-sender-id>',
      appId: '<your-app-id>'
    };
    firebase.initializeApp(config);
    const database = firebase.database();
  </script>
</head>
```







