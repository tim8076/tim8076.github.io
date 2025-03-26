---
title: Composition api (十一) 使用 composable
date: 2024-08-16 14:51:32
categories: Vue
tags: Composition api
description: "使用 composable 共用邏輯"
---

## composables 是什麼

在 Vue 3 中，composable 是一種可重複使用的邏輯單元，它通常封裝了一些與組件狀態或行為相關的功能，並可以在多個組件中共享。composable 通常是一個函數，它利用 Vue 3 的 Composition API 來組織和管理狀態、計算屬性、生命週期鉤子等。

Composable 的結構:
通常，composable 是一個返回一組狀態和行為的函數。它可能包含：

- 狀態: 使用 ref 或 reactive 來創建狀態。
- 計算屬性: 使用 computed 來創建基於狀態的衍生數據。
- 副作用和生命週期鉤子: 使用 watch, watchEffect, 或 onMounted, onUnmounted 等鉤子來管理副作用和組件生命週期。

## 實作範例

首先可以在專案根目錄新增 composables 資料夾，新增 composable 的 js 檔，檔名通常以 use 開頭。

```
- composables
  - useCounter.js
```

```js
// useCounter.js
import { ref } from "vue";

export function useCounter() {
  const count = ref(0);

  const increment = () => {
    count.value++;
  };

  const decrement = () => {
    count.value--;
  };

  return {
    count,
    increment,
    decrement,
  };
}
```

在一個 Vue 元件中，我們可以導入並使用這個 useCounter 函數。

```html
<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>
</template>

<script>
  import { useCounter } from "./useCounter.js";

  export default {
    setup() {
      const { count, increment, decrement } = useCounter();

      return {
        count,
        increment,
        decrement,
      };
    },
  };
</script>
```

更多範例可參考[官網](https://vuejs.org/guide/reusability/composables.html)
