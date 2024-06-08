---
title: Firebase 資料庫 (4) 新增資料
date: 2024-04-23 21:54:14
categories: Firebase
tags: Firebase 
description: '新增資料到資料庫'
---

## 新增資料

在學習新增資料以前，先學習2個語法

1. ref() 尋找資料庫路徑
2. set() 新增資料

``` js
firebase.database().ref().set('hi');
```

上面的程式碼代表，我要使用firebase裡的database功能，並在這個資料庫的ref()路徑裡新增 hi這筆資料，注意ref如果不帶路徑，預設是指向根目錄。

這時會跳錯，因為 firebase 因為安全性問題，預設是不能讀取與寫入的，所以先到規則頁面將 讀取與寫入 改為true。

![](https://cdn-images-1.medium.com/max/1000/1*0yl7fQkVFq09oq18FwZqEg.png)

將 html重新整理後，會發現資料 hi 被寫入資料庫了

![](https://cdn-images-1.medium.com/max/1000/1*qBPhRblil-11V187Wrhh2A.png)

也可以寫入物件

``` js
firebase.database().ref().set({ home: 'TW' })
```

![](https://cdn-images-1.medium.com/max/1000/1*7l4j8nnIq1skG03DHGoQdA.png)


firebase全部是物件格式，無法寫入陣列

![](https://cdn-images-1.medium.com/max/1000/1*83fBM2iTLN-Rxrl_ZUzWPQ.png)

假設想將一個陣列寫入firebase時，會發現資料並不是以陣列的方式存在

![](https://cdn-images-1.medium.com/max/1000/1*zYR86Mb16ZxsIvxW5RRAyA.png)

因為無法寫入陣列，所以可以用物件的方式來寫入多筆資料

![](https://cdn-images-1.medium.com/max/1000/1*1aQf4x3FdBdSdqxazalt-w.png)

在firebase資料庫會呈現如下:

![](https://cdn-images-1.medium.com/max/1000/1*79FrgpKXe5XgKnKba9dNJQ.png)

如果要修改stydent1的name時，可以在ref裡帶入 student1/name這個路徑，再用set去修改資料即可。

![](https://cdn-images-1.medium.com/max/1000/1*jXdvV3t4xNIAOIc3DRmdVg.png)

