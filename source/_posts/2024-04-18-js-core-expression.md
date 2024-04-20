---
title: JS 核心篇 (7) 陳述式與表達式
date: 2024-04-18 14:18:48
categories: JS 核心篇
tags: JS 核心篇
description: '介紹 JS 陳述式與表達式'
---

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*QF0Pqw1z3lIZBTlKOwrd6A.png)

## 陳述式:

舉凡流程判斷用，但不回傳結果的，稱為陳述式。

陳述式有幾大分類，如：

- 宣告（var、function）
- 流程控制（block、if…else）
- 迴圈（for、for…in）
- 其它（import, export）

## 表達式

表達式的重點是會回傳一個結果，因此是否能夠回傳結果就能判斷該語句或詞是否為表達式。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*KGg1cezTRo22qhp0kkf4rA.png)

例子：
- 數字運算：5 + 3
- 字串拼接："Hello, " + "world!"
- 變數：var y = x * 2;
- 函式呼叫：Math.max(10, 20)
- 陣列索引：arr[0]