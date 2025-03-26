---
title: JS 基礎篇 (9) DOM Node 的建立、刪除與修改
date: 2022-08-07 16:33:55
categories: JS 基礎篇
tags: JS 基礎篇
description: '介紹 DOM Node 的操作方法'
---

## 新增節點

### createElement

``` js
document.createElement('element');
```

![](https://miro.medium.com/max/922/1*YbdC8phChHpaXIwadplUhg.png)

透過 document.createElement() 可以建立一個新的元素，在建立新的 div 元素 newDiv 後，這時候我們在瀏覽器上還看不到它，直到透過 appendChild()、insertBefore() 或 replaceChild() 等方法將新元素加入至指定的位置之後才會顯示。

### createDocumentFragment

``` js
document.createDocumentFragment()
```

createDocumentFragment() 是一種沒有父層節點的「最小化文件物件」。 可以把它看作是一個輕量化的 Document，用如同標準文件一般的方式來保存「片段的文件結構」。

![](https://miro.medium.com/max/1354/1*IhyIKgVykoa64qi5s2Q4wQ.png)

## 插入節點

接下來要介紹的幾個方法，說明要如何將剛剛建立好的 DOM 節點，置入到我們所指定的位置。

### appendChild

``` js
NODE.appendChild(childNode)
```

透過 appendChild 方法，可以將指定的 childNode 節點，加入到 Node 父容器節點的末端：

![](https://miro.medium.com/max/1400/1*Duv1uiJyztP5av1hgMhwoA.png)


### append

``` js
NODE.append(childNode || String)
```

和appendChild 一樣將節點加入父層末段，但除了節點以外，也能加入字串。

## 刪除節點

```  js
const div = document.querySelector('div');
div.remove()  // 刪除節點
```

``` js
const div = document.querySelector('div');
const child = document.querySelector('.child');
div.removeChild(child) // 刪除子元素
```

## 操作元素的屬性

### 取得屬性內容

使用 getAttribute 可以回傳一個元素上的指定屬性值，如果指定的屬性不存在，則會回傳 null。

```js
element.getAttribute("屬性名稱");
```

```html
<div id="hi"></div> 
```
``` js
const div = document.querySelector('div');
div.getAttribute('id') //hi
div.getAttribute('src') //null
div.id // hi
```


### 設定屬性內容

可以使用 setAttribute 替指定元素設定屬性值，若該屬性存在則會替換值，語法如下：

```js
element.setAttribute("屬性名稱", "屬性值");
```

``` html
<div></div> 
```
``` js
const div = document.querySelector('div');
div.setAttribute('id', 'hi'); // 將id屬性設為 hi
```

### 移除屬性
``` html
<div title="aa" id="bob"></div> 
```
``` js
const div = document.querySelector('div');
div.removeAttribute('title'); // 將titile屬性移除
```

### data屬性操作

``` html
<div data-test="this is a test" data-num="123"></div>
```

``` js
div.dataset.test // this is a test
div.dataset.num // 123
```

## 操作元素的class

``` html
<div></div>
```

``` js
const div = document.querySelector('div');
div.classList.add('new-class'); // 新增class
div.classList.remove('new-class'); // 移除class
div.classList.toggle('new-class'); // 有class則移除class，沒有則加入該class
```

## 直接操作元素的css

``` html
<div></div>
```

``` js
const div = document.querySelector('div');
div.style.color = 'red';
div.style.backgroundColor = 'black';
```

## 節點(node)與元素(element)的區分

基本上 html 裡的節點包含所有的html標籤、換行、文字，而元素只包含的html標籤。
當我們在js裡用不同的選取dom方法時，依照方法不同會回傳 HTML Collection 或 Nodelist。

- HTML Collection: 當元素增減時，會自動更新。
- Nodelist: 依照選取方法不同，有的會自動更新，有的不會。

這邊推薦使用會回傳 Nodelist 的選取方法，如 querySelectorAll。因為元素如果會自動更新，出錯時很難維護。

[影片教學](https://www.youtube.com/watch?v=rhvec8cXLlo&ab_channel=WebDevSimplified)

## 取得與新增文字

新增文字有兩種方法 textContent 、 innerText，原先的所有內容都會被清空（包含 HTML 標籤），新的內容將被瀏覽器解析成「純文字」，不會保留 HTML 標籤的特性。

``` js
div.innerText = 'Hello World';
div.textContent = 'Hello World';
```


兩個方法都能加入文字，但innerText只顯示會出現螢幕上的文字，textContent則顯示全部文字。

``` html
<div>
  <span>Hello<span>
  <span style="display:none">Tim<span>
</div>
```
``` js
console.log(div.textContent); // Hello Tim
console.log(div.innerText); // Hello
```

- 取得文字

透過 textContent 可以取得 DOM 元素內的 「純文字內容」，HTML 會被忽略（請注意「純文字內容」有包含換行以及空格）

```html
<div class="targetClass">
  <p>取得這個 p 標籤的純文字</p>
</div>
```

```js
const targetClass = document.querySelector(".targetClass p");
console.log(targetClass.textContent); // 取得這個 p 標籤的純文字
```


## 取得與新增 html

透過 innerHTML 可以取得 DOM 元素內的「HTML 內容」

```html
<div class="targetClass">
  <!--  註解、換行、空白也包含在內  -->
  <p>HTML 標籤的內容也被選取</p>
</div>
```

```js
const targetClass = document.querySelector(".targetClass");
console.log(targetClass.innerHTML);
```

innerHTML 可以在元素內加入 html 結構，並清除元素原有內容。

``` js
div.innerHTML = '<span>Hello<span>'
```










