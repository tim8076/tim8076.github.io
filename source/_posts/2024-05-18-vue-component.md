---
title: vue (9) vue 元件概念
date: 2024-05-18 13:44:01
categories: Vue
tags: vue
description: '說明 vue 元件的概念與操作'
---

## vue 元件概念

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*kmzaHJCrVVVgrTwGexvSJA.png)

每個 Vue.js 的應用程式都是由vue的建構式建構的實體，在實體上，我們可以掛上不同的元件。 元件除了單一個呈現以外，也可以元件包元件。使用元件的好處是，每個元件都可以重複的使用，且是獨立的運作，便於程式碼的管理。

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*9pqERAQgRjIFVkW8Zqafzw.png)

像上圖中，三個元件的 myData都是獨立的，裡面的值沒有任何關聯。

## Component(全域註冊)

``` html
<script type="module">
  const app = Vue.createApp({
    data() {
      return {
        text: '外部元件文字',
      };
    },
  }).component('alert', {
    data() {
      return {
        text: '內部文字'
      };
    },
    template: `<div class="alert alert-primary" role="alert">
      {{ text }}
    </div>`
  });

  app.component('alert2', {
    data() {
      return {
        text: '內部文字'
      };
    },
    template: `<div class="alert alert-primary" role="alert">
      {{ text }}
    </div>`
  });

  app.mount('#app');
</script>
```
- 元件需要在 createApp 後，mount 前進行定義
- 元件需指定一個名稱
- 元件結構與最外層的根元件結構無異（除了增加 Template 的片段）
- 元件另有 prop, emits 等資料傳遞及事件傳遞

全域註冊的元件可以在 Vue.createApp 後接上 .component 方法來註冊，並在 app.mount('#app'); 之前可以掛在多個全域元件，只要注意元件的名稱要不同。

### [全域註冊優缺點](https://vuejs.org/guide/components/registration.html#local-registration)

- 優點: 能在 app 內的全部元件內使用，比較方便。
- 缺點: 
  1. 若元件被註冊，但完全沒使用，仍會被打包到專案(也就是沒有tree shaking)。
  2. 讓元件間彼此依賴的關係不清楚，大型專案會較難維護。

``` html
// 模板上引入元件
<alert></alert>
```

## Component(區域註冊)

``` js
const alert3 = {
  data() {
    return {
      text: '內部文字3'
    };
  },
  template: `<div class="alert alert-primary" role="alert">
    {{ text }}
  </div>`
}

const app = Vue.createApp({
  data() {
    return {
      text: '外部元件文字',
    };
  },
  components: {
    alert3
  },
})
```

區域註冊的元件使用一個物件來建立，並在要引入的 component 中 加入 components 選項帶入元件名稱。區域註冊的元件只有在註冊的元件內可以使用。

## 元件樣板及綁定方式

元件的 template 除了上面介紹的 直接寫在元件的 template 內以外，也可以使用

X-template建立模板:

``` js
<script type="text/x-template" id="alert-template">
  <div class="alert alert-primary" role="alert">
    x-template 所建立的元件
  </div>
</script>

// 在元件內帶入 text/x-template
app.component('alert2', {
  template: '#alert-template',
});
```

## 元件註冊名稱

當使用 SFC(single file component)或 string template 時，建議使用 PascalCase 來註冊元件。

``` js
import { createApp } from 'vue'

const app = createApp({})

app.component(
  // the registered name
  'MyComponent',
)
```

當元件以 PascalCase 註冊後，在 template 上可以使用

1. <MyComponent> : PascalCase
2. <my-component>:  kebab-case 


