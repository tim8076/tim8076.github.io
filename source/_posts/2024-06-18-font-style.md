---
title: (0-4) CSS基礎篇 文字樣式 (Font Style)
date: 2022-06-20 11:24:54
tags: 
- CSS基礎篇
categories: CSS
description: 'CSS 文字樣式 (Font Style)設定'
---

## Font Style

font-style 屬性用於設置文字的字體樣式。
可以設定的值如下: 

- normal: 無斜體
- italic: 仿斜體
- oblique: 斜角字
- inherit
- initial
- unset

## italic 與 oblique 區別

- italic: 指的是仿斜體字，有些字型本身就有斜體設定，但有些沒有。當文字沒有斜體設定時，瀏覽器會將字體轉成斜體外觀。

- oblique: 斜角字是羅馬字的一種，本身在設計時期就有傾斜角度。

不過目前網頁上不管是設定 italic 或 oblique 外觀都差不多。

## em 與 i

html 的 `<em>` 與 `<i>` 預設外觀都是斜體，採用的是 font-style: italic。

`<em>`: 強調斜體的語意
`<i>`: 單純描述外觀是斜體，沒有語意。