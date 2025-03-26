---
title: Bootstrap (11) Form 表單
date: 2024-06-18 20:05:54
categories: Bootstrap
tags: 
- Bootstrap
description: '學習 Bootstrap 的Form 表單'
---

## 表單基礎觀念

[線上範例](https://codepen.io/jskrtivy-the-animator/pen/KwPaQMM?editors=1010)

確保在輸入框上使用正確的 type 屬性（例如，email 用於電子郵件地址或 number 用於數字信息），以利用較新的輸入控制，如電子郵件驗證、號碼選擇等。相關內容可參考 [連結](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

``` html
 <div class="mb-3">
  <label for="exampleInputEmail1" class="form-label">Email address</label>
  <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
  <div id="emailHelp" class="form-text">
    We'll never share your email with anyone else.
  </div>
</div>
```

基礎注意事項
- form-control: 加在 input 標籤上
- form-label: 加在 form-label 標籤上
- form-text: 加在輔助說明文字上，id 和 aria-describedby對應
- label for 與 input id 要相對應
- 確保 button 有正確套用 type(預設值為 submit)

## 禁用表單

``` html
  <form>
    <fieldset disabled>
      <legend>Disabled fieldset example</legend>
      <div class="mb-3">
        <label for="disabledTextInput" class="form-label">Disabled input</label>
        <input type="text" id="disabledTextInput" class="form-control" placeholder="Disabled input">
      </div>
      <div class="mb-3">
        <label for="disabledSelect" class="form-label">Disabled select menu</label>
        <select id="disabledSelect" class="form-select">
          <option>Disabled select</option>
        </select>
      </div>
      <div class="mb-3">
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="disabledFieldsetCheck" disabled>
          <label class="form-check-label" for="disabledFieldsetCheck">
            Can't check this
          </label>
        </div>
      </div>
      <button type="submit" class="btn btn-primary" disabled>Submit</button>
    </fieldset>
  </form>
``` 

- 全部表單禁用: 在外層 `fieldset` 標籤加上 disabled
- 個別表單元素禁用: 在單個 input、select、button 加上 disabled

## form-control

可以在 input 和 textarea 標籤加上 form-control 樣式。[連結](https://getbootstrap.com/docs/5.3/forms/form-control/)

``` html
<div class="mb-3">
  <label for="exampleFormControlInput1" class="form-label">Email address</label>
  <input type="email" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
</div>
<div class="mb-3">
  <label for="exampleFormControlTextarea1" class="form-label">Example textarea</label>
  <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
</div>
```

### 尺寸

加上 `.form-control-lg` `.form-control-sm` 調整 input 大小 [連結](https://getbootstrap.com/docs/5.3/forms/form-control/#sizing)

``` html
<input class="form-control form-control-lg" type="text" placeholder=".form-control-lg" aria-label=".form-control-lg example">
<input class="form-control" type="text" placeholder="Default input" aria-label="default input example">
<input class="form-control form-control-sm" type="text" placeholder=".form-control-sm" aria-label=".form-control-sm example">
```

### 禁用

在 Bootstrap 中，disabled 和 readonly 都是用來限制用戶對表單元素的操作，但它們之間有一些重要的差異。以下是兩者的詳細對比[連結](https://getbootstrap.com/docs/5.3/forms/form-control/#disabled)：

| 特性        | `disabled`                               | `readonly`                          |
|-------------|------------------------------------------|-------------------------------------|
| 適用元素    | `<input>`, `<textarea>`, `<select>`, 等   | `<input>`, `<textarea>`              |
| 用戶輸入    | 用戶無法與元素互動                        | 用戶無法修改元素值                   |
| 樣式        | 通常會使元素變灰，表示不可用             | 樣式不變，但內容不可編輯             |
| 表單提交    | 該元素的值不會被提交                     | 該元素的值會被提交                   |
| 可點擊性    | 元素完全不可點擊                         | 元素仍然可點擊和聚焦（如果使用 JS）  |
| ARIA 支持   | 使用 `aria-disabled="true"` 提供可訪性支持| 無專門的 ARIA 屬性   

如果想要 `<input readonly>` 外觀能呈現單純文字樣式時，加上 `form-control-plaintext`。

### 檔案

``` html
<div class="mb-3">
  <label for="formFile" class="form-label">Default file input example</label>
  <input class="form-control" type="file" id="formFile">
</div>
```

在檔案的 input 上一樣可以加上 form-control，只是要注意要選對 `type="file"`

### 色彩

在 input 設定 `type="color"`，並在 input 加上 `form-control-color`，就可使用顏色選取器。

``` html
<label for="exampleColorInput" class="form-label">Color picker</label>
<input type="color" class="form-control form-control-color" id="exampleColorInput" value="#563d7c" title="Choose your color">
```

## form-select

在 seclet 元素上套用 `form-select`，即可加上樣式。[連結](https://getbootstrap.com/docs/5.3/forms/select/)

``` html
<div class="demo">
  <select class="form-select" aria-label="Default select example">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
  </select>
</div>
```

### 尺寸

為元素加上 .form-select-{ sm, lg } 調整尺寸

``` html
<select class="form-select form-select-lg mb-3" aria-label="Large select example">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>
<select class="form-select form-select-sm" aria-label="Small select example">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>
```

### 多選

在 select 加上 `multiple`，即可多選

``` html
<select class="form-select" multiple aria-label="multiple select example">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>
```

加上 size 限制一次顯示選項數量

``` html
<div class="demo">
  <select class="form-select" size="3" aria-label="size 3 select example">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
  </select>
</div>
```

## radio 和 checkbox

- radio: 多個選項中選擇一個
- checkbox: 多選

### checkbox

``` html
<div class="form-check">
  <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
  <label class="form-check-label" for="flexCheckDefault">
    Default checkbox
  </label>
</div>
```

結構上外層會有 `form-check`，內層 input 加上 `form-check-input`，內層 label 加上 `form-check-label`。

### radio

``` html
<div class="form-check">
  <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault1">
  <label class="form-check-label" for="flexRadioDefault1">
    Default radio
  </label>
</div>
<div class="form-check">
  <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault2" checked>
  <label class="form-check-label" for="flexRadioDefault2">
    Default checked radio
  </label>
</div>
```

結構上外層會有 `form-check`，內層 input 加上 `form-check-input`，內層 label 加上 `form-check-label`。
因為 radio 是單一選項，要加上相同的 name，將選項組成同一群組。

### switch

在 input 加上 `form-switch`，可以有滑動切換效果 [連結](https://getbootstrap.com/docs/5.3/forms/checks-radios/#switches)

``` html
<div class="form-check form-switch">
  <input class="form-check-input" type="checkbox" id="flexSwitchCheckDefault">
  <label class="form-check-label" for="flexSwitchCheckDefault">
    Default switch checkbox input
  </label>
</div>
``` 

### 行內樣式

原本 radio、checkbox 都是由上往下排列，要將選項轉成同一排，
可以加上 .form-check-inline 使其轉換成單行 [連結](https://getbootstrap.com/docs/5.3/forms/checks-radios/#inline)

``` html
<div class="form-check form-check-inline">
  <input class="form-check-input" type="checkbox" id="inlineCheckbox1" value="option1">
  <label class="form-check-label" for="inlineCheckbox1">1</label>
</div>
<div class="form-check form-check-inline">
  <input class="form-check-input" type="checkbox" id="inlineCheckbox2" value="option2">
  <label class="form-check-label" for="inlineCheckbox2">2</label>
</div>
<div class="form-check form-check-inline">
  <input class="form-check-input" type="checkbox" id="inlineCheckbox3" value="option3" disabled>
  <label class="form-check-label" for="inlineCheckbox3">3 (disabled)</label>
</div>
```

## range

在 input 加上 form-range ，即可套用 range 樣式。

``` html
<div class="demo">
  <label for="customRange1" class="form-label">Example range</label>
  <input type="range" class="form-range" id="customRange1">
</div>
```

### 最小與最大值

在 input 套用 min 加上最小值， max 加上最大值。

``` html
<div class="demo">
  <label for="customRange2" class="form-label">Example range</label>
  <input type="range" class="form-range" id="customRange2" min="1000" max="10000">
</div>
```

### 每次跳動值

如果希望每次調整能以固定數值增減，可以加上 step

``` html
<div class="demo">
  <label for="customRange3" class="form-label">Example range</label>
  <input type="range" class="form-range" min="0" max="100" 練習 id="customRange3" step="10">
</div>
```



