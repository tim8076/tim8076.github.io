---
title: 透過 DOM API 查找節點
date: 2022-08-09 16:17:30
categories: Javascript
description: '介紹如何在 dom 中選取你要的元素'
---

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








