---
title: JS 基礎篇 (4) 流程控制與迴圈
date: 2024-04-21 12:17:04
categories: JS 基礎篇
tags: JS 基礎篇
description: '使用 if else 進行流程控制'
---

## if else

就如同字面上一樣，「如果」怎樣怎樣，就做某件事，「否則」做另一件事，語法像這樣︰

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*ioRuQzg0mgPzHzV6BB_bsQ.png)

除了 if else 之外，你也可以使用 else if 來新增條件：

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*KbgXoVzcuXYYrQ54sYgk_Q.png)

## 三元運算子

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*38CeRDOo_tVhtKHEeCc5BA.png)

如果單純做賦予值的判斷時，可用三元運算判斷式。

如果 today ==3 就將水餃的值賦予到 eat，不然就將飯賦予到eat。

## switch

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*f1kFLkDw4eqcxekWf1VJHQ.png)

switch 括號內的語法可能是運算式或是某個變數、值，像上面就是 Math.ceil(month/3)。
接著會進入 case 來判斷，若switch 括號內的結果剛好是 case 後面的「值」，則會執行 case 區塊內的指令。
而 default 的區塊就是當上面所有 case 都不成立的時候會執行。

## for 迴圈

所謂「迴圈」指的是，想要重複做某件事，而數值會依次數有「遞增」或「遞減」的變化來完成退出的條件。

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*WhtkqGEPX10xhHfQKNWA_Q.png)

綠線的部分是「執行迴圈的條件」，指的是當滿足這個條件 (結果為 true) 的時候，就會進入大括號 { } 的區塊，然後執行內部程式。

藍線的部分是，在每一次執行完大括號 { } 區塊的程式碼之後，會執行這段程式碼。

``` js
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

這段程式碼將輸出

``` js
1
2
3
4
5
```

## while 迴圈

``` js
var i = 1;
while (i <= 5) {
    console.log(i);
    i++;
}
```

括號 () 內代表的是「執行迴圈的條件」，指的是當滿足這個條件 (結果為 true) 的時候，就會進入大括號 { } 的區塊，然後執行內部程式。

while 迴圈特別適用於當你無法確定迴圈需要執行多少次，但可以確定某個條件會在適當的時候變為 false 的情況下。

## 跳脫迴圈

使用迴圈時，若想跳過其中幾次或提早離開迴圈，可用:

- break: 直接跳離迴圈
- continue: 跳過一次，再繼續下個迴圈

假設想印出 1 - 10 的所有數字，但跳過3的倍數:

``` js
for (var i = 1; i <= 10; i++) {
    if (i % 3 === 0) {
        continue; // 跳過3的倍數
    }
    console.log(i);
}
```





