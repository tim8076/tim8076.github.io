---
title: CSS Button 按鈕設計
date: 2024-05-05 20:53:16
categories: CSS
description: '介紹CSS 按鈕設計'
---

## 按鈕設計

本單元參考 Pure.css 對按鈕的設計，來解說 css 按鈕設計上要注意的細節

按鈕基礎設定，如下圖。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*7ECXOQhqPGqnidOSzqaIlg.png)

- display:inline-block 讓按鈕能並排同時設定大小
- white-space: nowrap 文字不換行。
- text-align : center 文字置中
- cursor: pointer 顯示滑鼠手指頭
- urser-select : none 使用者不能選取按鈕文字

### 按鈕基礎樣式

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*1FjphYG9AKapFNeBjlVe1w.png)

設定文字大小、 padding、文字顏色、背景顏色、border-radius圓角設定

padding 使用em來設定，可以根據文字大小自動調整內距。

- 按鈕 hover active樣式

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*yYjcH9hdxAeTHoRH548fCw.png)

- 按鈕無效設定

當今天想讓使用者無法點選按鈕時，像是表單沒填完等情況 可以用以下設定

加上 cursor:not-allowed 和 pointer-events:none 讓使用者無法點選

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*7zdBtJHTHJYRx1bcWnFMTA.png)