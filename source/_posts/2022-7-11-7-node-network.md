---
title: Express框架(2) 網址規則
date: 2022-07-11 16:39:19
categories: Node.js
tags: 
- Node.js
- Express
description: '講解網址規則'
---

## 網址的組成

![網址組成](https://miro.medium.com/max/1400/1*IeJWJEhLIuP0HUfUKMcPgA.png)

![https](https://miro.medium.com/max/1400/1*QuRd_DEPJoO76rLIFYklQw.png)

https相較http協定，因為有加密是較安全的。

![網域](https://miro.medium.com/max/1400/1*324Ulsn-ffPuzx9EX1eMwg.png)

購買好主網址後，次網域可以依據不同服務掛在主網域下。

![參數](https://miro.medium.com/max/1400/1*mXxjTDg-yFBJUeKlT2zo4g.png)

在路徑search之後，可以設置query也就是參數，傳到後端後會解析成物件格式，再用這個物件去資料庫撈出對應資料。參數可以有多個，彼此用 & 符號連接。


