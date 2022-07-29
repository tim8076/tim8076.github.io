---
title: Async Await
date: 2022-07-29 16:37:55
categories: Javascript
description: '使用 async await 來處理非同步程式'
---

## promise的作法

![](https://miro.medium.com/max/1292/1*kbLtHl6rlpk9mQZMh6vjyg.png)

![](https://miro.medium.com/max/1192/1*_qmqlT1cYHhKxdPw2oHpVA.png)

傳統的promise寫法，我們會用 .then()去接收成功的結果，.catch()接收失敗的結果。但不斷用.then去接收結果，程式上的可讀性較差，所以可以改用async await的寫法來改寫。

## async await

![](https://miro.medium.com/max/1392/1*7xEFqbxd6W5rOHC5wmnXjQ.png)

async 的使用方法很簡單，只要在定義 function 時，前面加個 async 就可以了。而 await 會接收promise執行完的結果，等 Promise 執行完再執行下一行，後面的任務會等前面的任務完成後才繼續下去。

如果想接收錯誤的結果，可以用try catch寫法，將所有可能出錯的程式放在try裡，當有程式回傳錯誤時，會立即停止，並執行catch裡的程式

![](https://miro.medium.com/max/1356/1*3P-AW4xqVs-gGroh5rU36g.png)

當 async function 的內容全都結束後，會返回一個 promise，這表示後方可以使用.then語法來做連接，基本的程式長相就像下面這樣：

``` js
async function a(){
  await b();
  .....       // 等 b() 完成後才會執行
  await c();
  .....       // 等 c() 完成後才會執行
  await new Promise(resolve=>{
    .....
  });
  .....       // 上方的 promise 完成後才會執行
}
a();
a().then(()=>{
  .....       // 等 a() 完成後接著執行
});
```

[範例參考:](https://codepen.io/tim-chou/pen/ZEyBzpb?editors=1012)

