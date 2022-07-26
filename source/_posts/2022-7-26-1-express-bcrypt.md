---
title: Express框架(14) bcrypt 套件
date: 2022-07-26 17:48:55
categories: Node.js
tags: 
- Node.js
- Express
description: '用 brypt 替密碼加密'
---

## 什麼是 bcrypt 

在儲存密碼到後端資料庫時，要避免直接將密碼以字串方式存入，以防資料庫被害時密碼洩漏。所以應該再存入密碼前將密碼加密，也就是本文會介紹的 bcrypt套件 來加密。

bcrypt 能夠將一個字串做雜湊加密，其中有個參數叫 saltRounds 是在密碼學中的加鹽(salt)，加鹽的意思是在要加密的字串中加特定的字符，打亂原始的字符串，使其生成的散列結果產生變化，其參數越高加鹽次數多越安全相對的加密時間就越長。

## 安裝套件

``` 
npm install bcrypt --save
```

## 使用方法

- saltRounds: 整數型態，數值越高越安全。
- myPassword: 要加密的字串。
- testPassword: 測試驗證密碼的變數。
- myHash: myPassword加密後結果(給驗證用)

以下為promises 非同步的加密與解密方法

``` js
  // 加密
  bcrypt.hash(myPassword, saltRounds).then(function (hash) {
    // Store hash in your password DB.
    console.log(hash);
  });

  // 驗證密碼
  bcrypt.compare(myPassword, myHash).then(function (res) {
    console.log(res); // true
  });
  bcrypt.compare(testPassword, myHash).then(function (res) {
    console.log(res); // false
  });
```

也支援 async/await 的寫法

``` js
async function checkUser(username, password) {
    //... fetch user from a db etc.
    const match = await bcrypt.compare(password, user.passwordHash);
    if(match) {
        //login
    }
    //...
}
```
