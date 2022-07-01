---
title: Ajax解說系列(2) XMLHttpRequest
date: 2022-07-01 13:58:11
categories: Javascript
tags: 
- Javascript
- Ajax
description: '利用 XMLHttpRequest 發送網路請求到後端'
---

## 前言

XMLHttpRequest (XHR) 是 JavaScript 著名的 古老 API，能透過它操作 HTTP 請求，進行網路作業，
擷取資料的同時，卻不需進行頁面重載 (page reload)，以下介紹使用方法

## 建立物件

我們可以透過new 一個 XMLHttpRequest 物件 ，來向伺服器發送請求，這個XMLHttpRequest 物件包含許多屬性可使用。

![xml](https://miro.medium.com/max/714/1*e4T8bl0a1-yLF-6ty31wSA.png)
![](https://miro.medium.com/max/1155/1*32TavTHF8TJWAcE5XIOyGw.png)

其中 readyState 的狀態分為幾種，分別代表發出請求的不同階段

- 1 代表你用了 open 但還沒有把資料傳過去
- 2 偵測到你用 send
- 3 資料loading 中 ，可能資料太大
- 4 你撈到資料了，數據完全接收了

## 設定請求

使用 open() 方法，設定請求，
請求方法 除了 GET 與 POST，還能使用 PUT、DELETE、HEAD、OPTIONS

``` js
xhr.open('請求方法', '請求資源網址', true | false)
```

其中第三個參數代表: 

true 代表非同步，不等資料回傳，程式碼就會繼續跑。
false 代表同步，資料回傳，程式碼才繼續跑。

## 發送請求

使用 send() 方法，發送請求。

![send](https://miro.medium.com/max/1155/1*DvrAzDHjq31_kdppxvivyQ.png)

## 監聽事件

當使用非同步時，要監聽onload事件，確認資料撈回後，再進行處理。

![on-load](https://miro.medium.com/max/1155/1*-UC5WKjY-A5ClIMLUM3PbQ.png)


## POST 方法

和 get取得資料不同，利用 post 方法，傳送資料到伺服器，可以做帳號驗證、登入等功能。

![post](https://miro.medium.com/max/1155/1*4ip7E7cbry2cIWUcO1Ufvg.png)

1. open方法，選用post
2. setRequestHeader，指定傳送資料的格式
- json : application/json
- 傳統表單: application/x-www-form-urlencoded

3. send 傳送要核對的資料 ，利用 & 連接多筆資料

4. 監聽 onload事件，處理回傳後資料

![onload](https://miro.medium.com/max/1086/1*RSI2A1RPc5obLx5K_sYEyQ.png)