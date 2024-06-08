---
title: vue (6) 條件判斷與列表渲染
date: 2024-05-03 15:27:30
categories: Vue
tags: vue
description: '使用 v-if 判斷資料，v-for 渲染列表'
---

## 條件判斷 v-if v-show

若要依據資料顯示或隱藏元素，vue 提供了 v-if v-show 兩種做法:

### v-show

綁定的值為 truthy 則顯示，falsy 則隱藏。用的是 display: none 的方式來隱藏元素。
``` html
<div v-show="isShow"></div>
```

### v-if

同樣控制元素出現與否，可搭配 v-else-if、v-else 來判斷

``` html
<div v-if="count === 0">A</div>
<div v-else-if="count < 5">B</div>
<div v-else>C</div>
```

如上依據條件來決定顯示 A 或 B 或 C。
若想一次判斷多個元素顯示與否，可在外層加上` <template> `包起來。

``` html
<template v-if="count === 0">
  <div>A</div>
  <div>B</div>
  <div>C</div>
</template>
```

### 使用 v-if 或 v-show

當判斷式結果經常更動時，推薦用 v-show，因為元素僅用 display 在切換，節省效能。
當判斷式的結果幾乎不變時，推薦用 v-if，因為 v-if 是將元素刪除後重新掛載，不適合用在經常切換狀態的情形。

## v-for 列表渲染

### 列表

v-for 指令會以 item in items 的語法進行。

``` js
<div id="app">
  <ul>
    <li v-for="(item, index) in foods">{{ index }} / {{ item }}</li>
  </ul>
</div>
<script>
  const { createApp } = Vue;
  const vm = createApp({
    data() {
      return {
        foods: [ 'ramen', 'hamburger', 'rice', 'meat' ]
      }
    }
  });
  vm.mount('#app');
</script>
```

上面列表會渲染出以下列表，其中 item 為陣列內容，index 則是索引

``` html
0 / ramen
1 / hamburger
2 / rice
3 / meet
```

### 數字範圍

除了陣列與物件外，也可以在數字範圍內跑回圈

``` js
<li v-for="page in 10">{{ item }}</li>
```

如上會印出 1 到 10 的數字

### v-for 與 template

如果希望一次渲染多個 dom ，可在外層加上` <template> `包起來。

``` js
<template v-for="item in links">
  <div>divider</div>
  <div>{{ item.age }}</div>
</template>
```

### v-for 的排序與過濾

若想在渲染列表時，進行排序或搜尋過濾時，v-for 本身雖沒有提供相關功能，但我們能將原始陣列先用 computed 篩選後，在去跑篩選後的陣列即可。

``` js
<div id="app">
  <ul>
    <li v-for="num in bigNum">{{ num }}</li>
  </ul>
</div>
<script>
  const { createApp } = Vue;
  const vm = createApp({
    data() {
      return {
        num: [300, 20, 60, 560, 666],
      }
    },
    computed: {
      bigNum() {
        return this.num.filter(num => num > 500);
      }
    }
  });
  vm.mount('#app');
</script>
```

### v-for 與 key

vue 是用 virtual dom 的方式更新畫面，virtual dom 是一個物件會記錄當前元件的狀態，當畫面有更新時，會去比較更新前後 virtual dom 的差異，並只更新有差異的資料。

換句話說當一個 dom 的資料沒有更新時，vue 會沿用這個 dom，可看以下例子:

![](https://cdn-images-1.medium.com/max/1000/1*L4PPCQaIrSqZt7XE1SzIkg.gif)

當 list 內資料順序更動時，div 結構沒有更動，只有文字資料做更新，input 則維持原來位置。

解決方法是在加上唯一值的 key，確保畫面重新渲染:

`<li v-for="item in bigNum" :key="item.id">{{ item.name }}</li>`





