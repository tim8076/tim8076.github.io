---
title: (2) SCSS練功坊-變數variable
date: 2022-06-19 14:41:43
categories: scss
tags: 
- scss
description: 'scss 變數介紹'
---

## 以往css遇到的問題

以往在寫css時，可能我們會直接將顏色的值寫死，例如:

``` css
.card p {
  color: #f0a;
}
.title {
  color: #f0a;
}
.article {
  color: #f00;
}
```

這樣做的問題是，當今天客戶想將某個顏色替換時，我們必須手動一個一個更改，假如網站有300個地方用到該顏色，就需要手動改300次。

在 SCSS裡，我們可以使用變數來管理重複的值，例如 我們可以將色碼設定為變數，當後續需要調整顏色時，只要調整變數，就改完全站的設定。

## 變數設定方式

首先先在程式碼最上面打個『$』字號，後面則是自己命名的變數，之後在填上變數的值。

``` scss
$color-primary: #fa0;
$color-gray: #aaa;
```

之後需要設定顏色樣式時，就可以引入變數。

``` scss
.card {
  color: $color-primary;
}
```

變數除了支援色碼外還支援「字串」、「數字」等等。

雙引號的字串也可用 #{ }取出來:

![va](https://miro.medium.com/max/1004/1*jvZyuT0ob0GIxXyu3fdjoQ.png)

![編譯後](https://miro.medium.com/max/1048/1*ZgC18gRiXbzEUl_FiZrwuQ.png)

## 小結

學會使用變數以後，就不用辛苦的一個一個修改css了，全站的設定統一由變數管理，讓之後的修改與維護更輕鬆。









