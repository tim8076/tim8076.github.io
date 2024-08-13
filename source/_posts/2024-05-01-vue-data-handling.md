---
title: vue (2) 資料加工與處理
date: 2024-05-01 17:02:34
categories: Vue
tags: vue
description: '使用 computed 與 methods 處理資料'
---

## Methods 方法

當在模板上需要計算複雜的運算式時，可以先將資料用 methods 計算後再放到模板上。

``` js
<div id="app">
  總金額共: {{ subtotal() }} 元
  總金額共: {{ subtotal() }} 元
</div>

<script>
  // vue3 寫法
  const { createApp } = Vue;

  const vm = createApp({
    data() {
      return {
        price: 500,
        quantity: 50,
      }
    },
    methods: {
      subtotal() {
        return this.price * this.quantity;
      }
    }
  });
  vm.mount('#app');
</script>
```

幾個要注意的點是:

1. Vue.js的實體裡，可以透過 this 指回Vue.js的實體，所以可以透過 this.price 指回 data 內 price 的資料。
2. 在模板上呼叫 methods 方法時要加上小括號，如 `subtotal()`
3. 在Vue.js的實體裡呼叫 subtotal 時，透過  `this.subtotal()` 即可。

## Computed 計算屬性

除了可用 methods 處理資料外，vue 也提供computed計算屬性。和 methods不同的是，在模板上套用時不須加上 ()。

``` js
<div id="app">
  總金額共: {{ subtotal }} 元
  總金額共: {{ subtotal }} 元
</div>

<script>
  // vue3 寫法
  const { createApp } = Vue;

  const vm = createApp({
    data() {
      return {
        price: 500,
        quantity: 50,
      }
    },
    computed: {
      subtotal() {
        return this.price * this.quantity;
      }
    }
  });
  vm.mount('#app');
</script>
```

## computed 注意事項

當在 computed 裡使用會改變原本陣列的方法時，如 reverse() and sort()，應該先將原始陣列解構後再使用

``` js
- return numbers.reverse() // 錯誤
+ return [...numbers].reverse() // 正確
```

## computed setter

一般來說，computed預設只能讀取資料，也就是只有getter功能，將資料讀取後運算完return新的資料。
但我們可以用物件的形式，加入setter功能，來修改資料。

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*HL7DpvW-aC3DglwAKmk9tA.png)

## Computed 和 Methods 使用差異

``` js
<div id="app">
  總金額共: {{ subtotalComputed }} 元
  總金額共: {{ subtotalComputed }} 元
  總金額共: {{ subtotalComputed }} 元

  總金額共: {{ subtotalMethod() }} 元
  總金額共: {{ subtotalMethod() }} 元
  總金額共: {{ subtotalMethod() }} 元
</div>
```
- Computed: 計算的資料會暫存，直到觀察的屬性被更新，才會重新計算
- Methods: 每呼叫一次，就計算一次。

所以上面模板 console.log 出來會是如下，Computed 只執行一次，methods執行三次:

``` js
Computed
Method
Method
Method
```

所以 Computed 會效能優於 methods，但如果需要帶入參數的情形，還是只能用 methods。

