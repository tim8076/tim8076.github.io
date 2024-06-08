---
title: vue (3) 屬性綁定與表單操作
date: 2024-05-02 15:06:39
categories: Vue
tags: vue
description: '使用v-bind、v-model指令綁定資料與畫面'
---

## 指令

Vue 裡提供了 v- 開頭的指令，可以套用在 html 上，當與指令搭配的值改變時，元素標籤的狀態也會跟著改變。

## v-bind 屬性綁定

v-bind 指令可以將 data 內的資料與 html 做綁定，常見的標籤屬性如 a 連結的 href 和 圖片的 src 都可以綁定
用法如下:

``` html
<p v-bind:id="customId">123</p> 
```

實際在瀏覽器渲染時會變成:

``` html
<p id="item-id-1">123</p> 
```

v-bind 指令的簡寫為 `:`

``` html
<p :id="customId">123</p> 
```
## v-model 表單綁定

常見的表單元素如 `<select> <input>` 等，可以透過 v-model 來做資料的雙向綁定，v-model 會根據不同表單類別來更新元素內容。

### input 文字框

在常見的 input 加上 v-model 後，此時輸入框會自動綁定 input 事件。當輸入框的文字被更改，會自動更新data內資料。

``` html
<input v-model="message" placeholder="edit me"> 
<script>
  // vue3 寫法
  const { createApp } = Vue;
  const vm = createApp({
    data() {
      return {
        message: '',
      }
    },
  });
  vm.mount('#app');
</script>
```


### select操作

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*xrOqe84wqQInvBRcpV_IEg.png)
![](https://miro.medium.com/v2/resize:fit:604/format:webp/1*OpRPvvV7Bn3o_-w3jCA9xA.png)

利用在select 標籤上加上v-model，可將option的值寫入變數內。

也可用 v-for 繪製 select 裡的 option

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*FO6LK3IlSyitQTAMNLC3CQ.png)

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*IhZsOUO10nS1WFWg_oPORg.png)

### select多選方法

![](https://miro.medium.com/v2/resize:fit:572/format:webp/1*qKRGDbICZJasWdhDne5ETw.png)

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*rJ6cVTLJJzUe0rwNT4_fPQ.png)

利用在 select 標籤中加入 mutiple屬性，就可以多選，此時v-model會將多筆資料寫入空陣列裡。

### checkbox 單選框

checkbox 單選框搭配 true-value、false-value 可以直接將值寫到綁定的變數，如下為 checkAnswer2

``` html
  <h3>checkbox 單選延伸</h3>
  <p>小明，你是吃飽沒？</p>
  <p>{{ checkAnswer2 }}</p>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check2" 
      v-model="checkAnswer2"
      true-value="吃飽了" false-value="還沒">
    <label class="form-check-label" for="check2">小明回覆</label>
  </div>
```

### checkbox 複選框

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*97jnNjMymYbcWcXoZHS9hg.png)

![](https://miro.medium.com/v2/resize:fit:532/format:webp/1*a6mUEzh4fFpJhQb7F5l7-g.png)

利用v-model將 value寫入 checkAnswer陣列裡，當被勾選時就加入陣列，取消勾選時value移除陣列。

### radio 單選框

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*CxnLrcfgrnb6_2mdHYScAw.png)

![](https://miro.medium.com/v2/resize:fit:556/format:webp/1*SXeW5UYLbT6hcTL51ic0Ow.png)

利用v-model將 radio 的 value 寫入 radioAnswer。

## v-model修飾符

- v-model.lazy: 當input輸入完文字後，才會將值顯示。

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*OkR_BJTJ1jnLmmymo3rgeg.png)
![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*fEYfFJwc1MVDSq_OM9-6ZQ.gif)

- v-model.number: 將值轉為數字型別

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*lQpSfwvelQSht2zk83u9xA.png)

- v-model.trim: 將前後多餘的空白刪除

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*MAV67_em8CmFY05vVDtnFQ.png)

[表單範例](https://codepen.io/tim-chou/pen/wvoyKxN)




