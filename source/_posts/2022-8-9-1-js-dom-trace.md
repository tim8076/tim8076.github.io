---
title: JS 基礎篇 (8) 透過 DOM API 查找節點
date: 2024-04-24 10:00:00
categories: JS 基礎篇
tags: JS 基礎篇
description: '解釋 JS DOM API'
---

## Bom 與 Dom 是什麼

前端開發者在網頁上的操作方法，都是由瀏覽器所提供的，Js本身並沒有提供網頁操作方法。
這些操作方法由 「BOM」與 「Dom」所擁有:

![](https://miro.medium.com/v2/resize:fit:828/format:webp/0*A6XZonNYmKAnSJy3)

### BOM(Browser Object Model 瀏覽器物件模型):

BOM 的核心其實是 window 物件。而 window 物件提供的屬性主要為 document、location、navigator、screen、history 以及 frames。

在瀏覽器裡的 window 物件扮演著兩種角色：

- ECMAScript 標準裡的「全域物件」 (Global Object)
- JavaScript 用來與瀏覽器溝通的窗口

window 提供了許多屬性和方法，用於操作瀏覽器視窗和其中載入的文件。以下是 window 物件的一些常見屬性和方法：

- window.document: 表示目前視窗中載入的文件，可以通過它來訪問和操作文件的內容、結構和樣式。
- window.location: 用於獲取或設置目前視窗的URL。
- window.alert(): 顯示一個警告框，包含指定的訊息和一個“確定”按鈕。

### DOM (Document Object Model 文本物件模型):

dom 是將html以樹狀的結構來表示的模型，最根部是document，往下則是 html 標籤節點，再往下則是文本節點和屬性節點。
dom api 就是定義能操作 html 架構、樣式的方法。 





## getElementById

選取特定id的元素

``` html
<div id="bob"></div>
```

``` js
const bob = document.getElementById('bob');
```

## getElementByClassName

選取所有包含指定class的元素

``` html
<div class="card"></div>
```

``` js
const bob = document. getElementByClassName('card');
```

## querySelector

querySelector 使用 css 選擇器來選取一個元素。

``` html
<div class="card"></div>
```
``` js
const bob = document. querySelector('.card');
```

## querySelectorAll

querySelectorAll 使用 css 選擇器來選取多個元素，會回傳一個collection(不是陣列)

``` html
<div class="card"></div>
<div class="card"></div>
```
``` js
const bob = document.querySelectorAll('.card');
```

## Node.children

Node.children 會回傳所有Node 節點的子節點，會回傳一個collection。

``` html
<div class="container "> 
  <div class="card"></div>
  <div class="card"></div>
</div>
```

``` js
const container = document.querySelector('.container');
const cards = container.children;
```

## Node.parentElement

透過 Node.parentElement 可以用來取得父元素，回傳值只會是一個元素節點 (Element node)

``` html
<div> 
  <div class="card"></div>
</div>
```

``` js
const card = document.querySelector('.card');
const parent = card.parentElement;
```

## Node.closest

Node.closest 會一路往上找，取得符合條件的父元素。

![](https://cdn-images-1.medium.com/max/1200/1*-En99lg7L95i7glPXF-PYA.png)

![](https://cdn-images-1.medium.com/max/1200/1*QkZmAc54hcar7Iy-yVlOTw.png)

## Node.previousSibling

透過 Node.previousSibling 可以取得同層之間的「前一個」節點，如果 node 已經是第一個節點，則回傳 null。

``` html
  <div></div>
  <div class="card"></div>
```

``` js
const cardOne = document.querySelector('.card');
const cardTwo = document.previousSibling;
```

## Node.nextSibling

與 Node.previousSibling 類似，透過 Node.nextSibling 可以取得同層之間的「下一個」節點，如果 node 已經是最後一個節點，則回傳 null。

``` html
  <div class="card"></div>
  <div></div>
```

``` js
const cardOne = document.querySelector('.card');
const cardTwo = document.nextSibling;
```








