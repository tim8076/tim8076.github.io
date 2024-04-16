---
title: HTTP Networking(4) Asynchronous
date: 2024-04-13 11:03:34
categories: HTTP Networking
tags: HTTP Networking系列
description: '介紹 Asynchronous 運作'
---

## 同步與非同步

- synchronous: 也就是同步的程式碼，代表程式是按照順序執行，一行執行結束才執行下一行。

舉例來說 下面 console 的程式碼會逐行執行。

``` js
console.log("I print first");
console.log("I print second");
console.log("I print third");
```

- asynchronous: 非同步的程式碼，讓我們可以同時執行不同的程式碼，舉例來說:

``` js
console.log("I print first");
setTimeout(() => console.log("I print third because I'm waiting 100 milliseconds"), 100);
console.log("I print second");

// I print first
// I print second
// I print third because I'm waiting 100 milliseconds
```

在js裡，當執行一般同步的程式碼時，那沒有問題就一行接一行執行，但當遇到非同步的程式碼時，如 setTimeout、打api時，js會將非同步程式碼放到事件儲列，並接著執行下面的程式碼，等同步的程式碼跑完後就會跑事件儲列裡的程式碼。

好處是，我們不用等待非同步的程式碼執行完才能執行下一步，我們可以同時進行。

## 為什麼需要非同步

我們會希望盡量保持程式是同步執行的，因為那比較簡單了解。但有時也需要非同步的程式碼，例如當使用者操作更新一個網頁時，瀏覽器需要和伺服器溝通取得新資料，這個 HTTP request  通常會花 100 毫秒左右，如果使用者必須等 100毫秒才能在操作網頁，甚至連滑鼠都不能使用，會是很糟的使用者體驗。

藉由非同步的程式碼，可以讓網頁在等待 HTTP request 的同時，執行其他code，讓使用者體驗更好。

## [Promise](https://www.boot.dev/assignments/e9d87b33-df09-4d49-9c96-ce085b81ec92)

在 js 中有內建的 Promise物件來處理非同步程式，就和現實世界做一個承諾(promise)一樣，會有兩種結果，要嘛我成功行承諾(resovle)，要嘛我沒有履行承諾(reject)，程式碼如下:

``` js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    if (getRandomBool()) {
      resolve("resolved!")
    } else {
      reject("rejected!")
    }
  }, 1000)
})

function getRandomBool(){
  return Math.random() < .5
}
```

上面程式碼會在1秒後，若成功回傳 resolved! 、失敗回傳rejected! 當我們在等待 promise 結果回傳前，其他程式碼會同時被執行。

### 如何使用 pormise

pormise 物件有兩個方法:

- .then: 如果promise resolve， .then方法會被執行。
- .catch: 如果promise reject， .catch方法會被執行。

```js
promise.then((message) => {
    console.log(`The promise finally ${message}`)
}).catch((message) => {
    console.log(`The promise finally ${message}`)
})

// prints:
// The promise finally resolved!
// or
// the promise finally rejected!
```

## await 

除了 `.then() .catch()`，也可以用 await 。
await 會等待 Promise 被 resolve 後將值回傳。

``` js
const message = await promise
console.log(`Resolved with ${message}`)
```

但這不代表整個 js 程式會停止並等待，而只是這段程式會 await 等待。
await 可以讓我們將非同步的程式碼寫得和同步的程式碼一樣，
且 await keyword 只能使用在 async function 中或程式的第一層[top level module](https://stackoverflow.com/questions/46515764/how-can-i-use-async-await-at-the-top-level)。

## async function

就像 await 被用來取代 .then() 一樣， async function 被用來取代 `new Promise`。
當一個 function 前面加上 async 關鍵字時，這個function 會自動回傳一個 promise，這個promise resolve的值，就是function return 出來的值。

以下為 promise 和 async function 的範例:

``` js
// promise 範例
function getPromiseForUserData(){
  return new Promise((resolve) => {
    fetchDataFromServerAsync().then(function(user){
      resolve(user)
    })
  })
}
const promise = getPromiseForUserData()
```

``` js
// async function 範例
async function getPromiseForUserData(){
  const user = await fetchDataFromServer()
  return user
}

const promise = getPromiseForUserData()
```

## async function  的優點

比起 `.then()` 使用 async function 可以讓程式碼更簡單易懂

`.then()`寫法
``` js
fetchUser.then(function(user){
  return fetchLocationForUser(user)
}).then(function(location){
  return fetchServerForLocation(location)
}).then(function(server){
  console.log(`The server is ${server}`)
});
```

async 寫法
``` js
const user = await fetchUser()
const location = await fetchLocationForUser(user)
const server = await fetchServerForLocation(location)
console.log(`The server is ${server}`)
```



