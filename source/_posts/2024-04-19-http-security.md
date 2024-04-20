---
title: HTTP Networking(9) HTTP security
date: 2024-04-19 10:15:41
categories: HTTP Networking
tags: HTTP Networking系列
description: '介紹 HTTP security'
---

## 什麼是 https

HTTPS(Hypertext Transfer Protocol Secure)，是 http 協議的延伸。它確保 在 client 和 server 端之間傳送的資料都是加密的。這樣就可以安全的傳送像 信用卡資料、密碼、銀行帳號的資料。

![](https://www.shubo.io/9cc769693e50c090178068e8efd3338e/http-vs-https.svg)

## HTTP 過程解說

![](https://cdn-images-1.medium.com/max/1000/1*guPOaNV8Ma-zueBpQu1b8g.png)

當 client 向 server 發出 http 請求時，中間會有許多人可以看到你的資料，如下

- Public wifi: 使用的公用 wifi
- ISP: Internet Service Provider 網際網路連線服務公司 ，如 HiNet
- cloud provider: 雲端伺服器的供應商，如 AWS

所以在 client 發出請求前要先加密，而伺服器收到請求後在解密。

![](https://cdn-images-1.medium.com/max/1000/1*DBHHn56dkgepJwvqz79v0A.png)

在 server 端會有兩把鑰匙

- public key: 用來加密資料，但無法解密。
- private key:  用來解密

![](https://cdn-images-1.medium.com/max/1000/1*vdOe-IQxF0kHwFEFR0ccKw.png)

前後端之間通常會用 symmetric encription key 來加密和解密資料。這意味著發送方和接收方都需要知道並使用相同的金鑰來加密和解密數據。


詳細流程如下:

1. server 產生 public 和 private key(伺服器端只需產生一次，在https協議建立時)
2. client 向 server 接觸，說明想發出 secure request 給你。
3. server 將 public key 傳給 client
4. client 產生一組 secret token，並將 secret token 用 public key 加密後，回傳 server
5. server 用 private key 解密
6. client 和 server 協議出 symmetric encription key
7. client 成功發出 https 請求。
8. server 成功解密請求，並回傳 加密的 response。
9. client 解密回傳的 response





