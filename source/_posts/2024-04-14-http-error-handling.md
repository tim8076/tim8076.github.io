---
title: HTTP Networking(4) 錯誤處理
date: 2024-04-14 11:29:21
categories: HTTP Networking
tags: HTTP Networking系列
description: '介紹 js 中如何進行 error handling'
---

## try catch

當 js 中的程式有錯誤時，可以用 try catch 來處理錯誤。
以下程式，因為變數 car 沒有定義會出現錯誤。

``` js
const speed = car.speed
// The code crashes with the following error:
// "ReferenceError: car is not defined"
```

此時可以用 try catch 來處理

``` js
try {
  const speed = car.speed
} catch (err) {
  console.log(`An error was thrown: ${err}`)
  // the code cleanly logs:
  // "An error was thrown: ReferenceError: car is not defined"
}
```

## BUGS VS ERRORS

- Bugs: 指的是程式運行的結果和想的不同，此時需要 fix the bug

        例如有一個加法函式 `add(5, 3)` 預期會得到 8 但卻出現 10 的，就是bug。

- Error: 指的是程式在預期中可能出現的錯誤，例如:
         `No Internet connection`、`server down`、`user input`
         此時要做得是 handle the error。

## Debugging

當程式運行的結果和想的不同時，需要 debugging，例如:

- 新增一個缺少的參數到函式裡。
- 修正一個有錯誤的 url後，在執行 HTTP request
- 修復應用程序中未正確顯示的日期選擇元件

## Error handling

是指在程式中，處理那些預期中可能出現的錯誤，例如:

- 使用 try/catch 來檢測用戶輸入的問題
- 使用 try/catch 在沒有網絡連接時，顯示錯誤。

## Async await 讓錯誤處理更容易

``` js
try {
  const user = await fetchUser()
  console.log(`user fetched: ${user}`)
} catch (err) {
  console.log(`an error was thrown: ${err}`)
}
```

try catch 是js中處理錯誤的標準方法，但在 Promise API 中無法使用。若使用 Async await 則可以配合 try catch。






