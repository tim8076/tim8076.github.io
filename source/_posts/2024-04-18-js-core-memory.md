---
title: JS 核心篇 (6) JS 記憶體存放
date: 2024-04-18 13:17:24
categories: JS 核心篇
tags: JS 核心篇
description: "介紹 JS 的記憶體存放"
---

## 記憶體存放

![](https://cdn-images-1.medium.com/max/1000/1*MN5_XRqtujvxGd8odbvZ7g.png)

之前章節說過每個函式在執行時，會產生執行環境，在執行環境中會創造屬於他的記憶體空間。當函式執行完後，也會將記憶體空間釋放。
但記憶體的釋放也有條件:

- 當這個物件不被任何物件參考時，會被時為可回收的記憶體垃圾。

範例:

```js
function getData() {
  let demoData = [];
  for (let i = 0; i < 1000; i++) {
    demoData.push(randomText(5000));
  }
}
getData();
```

上面函式執行完後， demoData 因不被參考，而釋出記憶體空間。

```js
function fn() {
  const demoData = [];
  setTimeout(() => {
    demoData;
  }, 10000);
}
fn();
```

上面函式因為 demoData 有被參考，記憶體不會釋放。
