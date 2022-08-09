---
title: DOM Node 的建立、刪除與修改
date: 2022-08-07 16:33:55
categories: Javascript
description: '介紹常用的 dom 新增與刪除方式'
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

``` html
<div id="hi"></div> 
```
``` js
const div = document.querySelector('div');
div.getAttribute('id') //hi
div.id // hi
```

### 設定屬性內容
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

## 新增文字

新增文字有兩種方法 textContent 、 innerText

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


## 新增 html
innerHTML 可以在元素內加入 html 結構，並清除元素原有內容。

``` js
div.innerHTML = '<span>Hello<span>'
```










