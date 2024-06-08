---
title: vue (7) vue 元件的生命週期
date: 2024-05-04 15:20:48
categories: Vue
tags: vue
description: '使用 vue 元件的生命週期'
---

## 生命週期

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*v0EMufIEqpt5XczaeS-psA.png)

Vue 的實體物件從建立、掛載、更新、銷毀的一連串過程稱為生命週期。在這個過程中，vue 提供了開發者在這些週期階段做對應處理的「鉤子函式」，介紹如下

- beforeCreated:
  Vue實體被建立，狀態和事件尚未初始化。
- created:
  Vue實體被建立，狀態和事件初始化完成(可使用 data、props、computed等屬性)
- beforeMounted:
  Vue實體尚未與模板(Dom節點)綁定，但模板已編譯完成
- mounted:
  Vue實體與模板(Dom節點)掛載完成
- beforeUpdated:
  狀態被更動，畫面更新前
- updated:
  狀態被更動，畫面也更新完成
- beforeUnmounted: 元件銷毀前，還能取得data資料
- unmounted: 元件已銷毀，還能取得data資料

使用方式為，在vue實體加入生命週期鉤子函式，這樣vue在進入不同週期時，會觸發對應函式:

``` js
<script>
  const { createApp } = Vue;
  const vm = createApp({
    data() {
      return {
        foods: [ 'ramen', 'hamburger', 'rice', 'meat' ]
      }
    },
    created() {
      console.log('created');
    },
    mounted() {
      console.log('mounted');
    },
    unmounted() {
      console.log('unmounted');
    },
  });
  vm.mount('#app');
</script>
```

## keep alive

如果希望元件在使用 v-if 進行切換時，能保有資料狀態時，可以在元件外層加上 keep alive，避免重新渲染。這在需要保留狀態（例如表單輸入、滾動位置等）的情況下非常有用。

``` html
  <keep-alive>
    <child v-if="isShowing"></child>
  </keep-alive>
```

使用 keep-alive; 時，有兩個額外的生命週期鉤子可供使用：
- activated: 當元件被激活時調用。
- deactivated: 當元件被停用時調用。

``` js
<template>
  <div>我是被快取的元件！</div>
</template>

<script>
export default {
  activated() {
    console.log('元件被激活');
  },
  deactivated() {
    console.log('元件被停用');
  }
};
</script>
```

### include 屬性

`<keep-alive>` 組件有兩個屬性：include 和 exclude，這些屬性用來控制哪些組件應該被緩存，哪些不應該被緩存。

include 屬性用來指定只有哪些組件應該被緩存。它可以是一個逗號分隔的字符串、正則表達式或一個陣列。

- 逗號分隔的字符串：列出應該被緩存的組件名稱。
- 正則表達式：匹配應該被緩存的組件名稱。
- 陣列：列出應該被緩存的組件名稱。

``` js
<keep-alive include="ComponentA,ComponentB">
  <component :is="currentComponent"></component>
</keep-alive>
```

### exclude 屬性

exclude 屬性用來指定哪些組件不應該被緩存。

``` js
<keep-alive exclude="ComponentC">
  <component :is="currentComponent"></component>
</keep-alive>
```


## 狀態更新與畫面的同步

假設想在 資料更新後立刻去對 dom 進行操作，會無法法成功。響應式資料更新後，Vue 會先同步更新相依數據，再以非同步的方式去更新 DOM。換句話說，vue 會等所有資料都更新完後，才一口氣更新 dom。

這樣的好處是可以節省效能，如果開發者短時間內修改了好幾次的資料，其實 Vue 只需要渲染最終的結果，就能省去中間一直重新渲染 DOM 的效能。

所以 Vue 提供了 nextTick 這個 API，會是在 DOM 更新渲染完成後呼叫。

- 使用 nextTick 時機: 當需要確認資料更新後，對dom進行操作時。

``` js
<div id="app"> {{ message }} </div>
const vm = new Vue({
  el: '#app',
  data: {
    message: '原始值'
  },
  methods: {
    editText() {
      this.message = '修改后的值1'
      this.message = '修改后的值2'
      this.message = '修改后的值3'
      console.log(vm.$el.textContent) // 这时候想获取页面最新的DOM节点，却发现获取到的是旧值
      this.$nextTick(() => {
        console.log(vm.$el.textContent) // 修改后的值3
      })
    }
  }
})
```