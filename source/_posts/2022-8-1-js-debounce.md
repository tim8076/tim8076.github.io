---
title: Debounce & Throttle
date: 2022-08-01 14:05:51
categories: Javascript
tags: 
- debounce
description: '使用 debounce 和 throttle 提升網頁效能'
---

## 前言

當出現頻繁發出 api 請求的情況時，我們可以用 debounce 或 throttle來控制發出請求的頻率，來提升使用者體驗。

## debounce

![](https://firebasestorage.googleapis.com/v0/b/project-fb4ac.appspot.com/o/2022080101.png?alt=media&token=60283d21-62fb-48cd-aed8-48b0fd2bc642)

假設今天我們在搜尋欄位輸入文字，底下會自動跳出相關結果，這代表每次使用者打字時都會發出一次api請求，去取得搜尋結果。若要降低請求的頻率，我們可以使用 debounce 讓請求經過指定的等待時間後再發出。

``` js
const updateDebounceText = debounce((text) => {
  debounceText.textContent = text;
}, 250)

input.addEventListener('input', e => {
  defaultText.innerHTML = e.target.value;
  updateDebounceText(e.target.value);
});

function debounce(cb, delay = 1000) {
  let timeout
  return (...args) => {
    clearTimeout(timeout);
    timeout = setTimeout(() => {
      cb(...args)
    }, delay)
  }
}
```

在 input 搜尋欄位偵聽 input 事件，也就是使用者每次打字時 會去觸發 debounce 函式。在 debounce 函式中我們會傳入一個 callback function 並回傳一個新的函式。 在這個新的函式中，會設定 setTimeout 來指定等待的時間，等時間到後再去執行 cb 函式。

要注意的是，每次執行函式時會先 clearTimeout，清除 setTimeout的計時器，再重新設定新的計時器。也就是說當使用者不斷打字觸發函式時，會不斷清除計時器，讓計時器重新計時，此時 cb 函式 都不會被執行，直到使用者停止打字並且計時器到時時，才會去執行函式。

以上就能做到等使用者打完字，在一次發出請求的目的了。

## throttle

Throttle 是另一種減緩事件觸發方法，它與Debounce的差異是，為使用者觸發相同事件時提供間隔，控制特定時間內事件觸發的次數。適合用在像 卷軸事件 和 滑鼠事件 這些會頻繁觸發的事件中。

``` js
input.addEventListener('input', e => {
  updateThrottleText(e.target.value);
});

function throttle(cb, delay = 1000) {
  let shouldWait = false;
  let watingArgs;
  const timeoutFunc = () => {
    if (watingArgs == null) {
      shouldWait = false;
    } else {
      cb(...watingArgs);
      watingArgs = null;
      setTimeout(timeoutFunc , delay)
    }
  }

  return (...args) => {
    if (shouldWait) {
      watingArgs = args;
      return;
    };
    cb(...args);
    shouldWait = true;
    setTimeout(timeoutFunc , delay)
  }
}
```
和 debounce 一樣會傳入 cb 函式到 throttle 中，並設定 shouldWait 預設為 false，讓事件第一次會被執行，並在被執行後將shouldWait 設為true，讓事件在等待的時間間隔內不會被執行，直到 setTimeout 的時間到後，會再將 shouldWait 設為 false讓事件執行。




