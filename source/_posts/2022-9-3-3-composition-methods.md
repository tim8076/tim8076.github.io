---
title: Composition api (三) Methods
date: 2022-09-03 15:44:50
categories: Vue
tags: Composition api
description: '在Composition api中定義方法'
---

## 如何定義方法

![](https://cdn-images-1.medium.com/max/1100/1*DG0Xtfl9EOVnfo3atdVUqg.png)

在composition api裡，如果要定義方法，直接在setup裡用function或箭頭函式來定義即可，記得這些方法也要用return匯出。

## 不須匯出的資料

另外如果有資料不需要匯出到畫面，可以不用 ref 來定義，也不需要 return 出來。

``` js
const app = createApp({
  setup() {
    const num = ref(1);
    let countAdd = 0;

    const add = (n) => {
      num.value += n;
      countAdd +=1;
    }

    const getCount = () => {
      console.log(countAdd);
    }

    return {
      num,
      add,
      getCount,
    }
  },
});
```

如上 countAdd 不須匯出到畫面，所以直接宣告變數即可。



