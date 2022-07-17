---
title: MongoDB Atlas(二) cluster
date: 2022-07-17 11:17:23
tags: MongoDB Atlas
description: '建立 MongoDB Atlas帳號'
---

建立好新的資料庫後，先設定 Database Access ，也就是誰能讀取這個資料庫。

![](https://miro.medium.com/max/963/1*F2bjbKiANh6uFsQp1tpkSA.png)

點選 Add New Database User， 並設定user的帳號密碼

![](https://miro.medium.com/max/963/1*m_dIUQS6di3FJapbiGozvg.png)

再來點擊左側 Network Access ，設定能讀取資料庫的ip位置

![](https://miro.medium.com/max/963/1*mtkdr8aabVXwwI6IsatThw.png)

點選 allow access from anywhere，

![](https://miro.medium.com/max/963/1*Uqnh7SBIp_tYBAUm1pYG6g.png)

再來點擊左側 database，再點選connect，來連接資料庫

![](https://miro.medium.com/max/963/1*121AdSPsVRfepmRDFuk6uA.png)

點選第二個 connect your application

![](https://miro.medium.com/max/963/1*ao4jvrYVDTBkrjJbSIJFCQ.png)

選擇 node版本 3.6以後

![](https://miro.medium.com/max/963/1*_SUU-2aT2xZg0Es9UyvL8w.png)

複製程式碼到我們的node js專案

![](https://miro.medium.com/max/963/1*57tPw1zIMwFn-utOPvOcQg.png)

在專案裡新增 db資料夾，並新增 connect.js

![](https://miro.medium.com/max/572/1*NqGtYaYQtlb0WRYAo-FZfw.png)

將剛才mongodb複製的程式碼貼到js檔裡，存成字串。

![](https://miro.medium.com/max/963/1*kJYiQqrSShd0_KFCJ7ydmw.png)

## 建立collection

再來建立collection，點選 browser collection

![](https://miro.medium.com/max/963/1*b7CtG2I0gJMQyiMJF6HQog.png)

點新增資料

![](https://miro.medium.com/max/963/1*jpcAAKfrTjYuQF-E53gd_Q.png)

輸入資料庫名稱

![](https://miro.medium.com/max/648/1*qBIe4FrsTM63sUQMKusSzQ.png)


在database中，可以創建不同的collections ，裡面是不同的資料集。如下圖我創建了 products跟 users兩個collection

![](https://miro.medium.com/max/1400/1*KaQPsHVvi9EDSRBM_l0dyQ.png)

點選右邊 建立 document，可以建立collection 裡的資料

![](https://miro.medium.com/max/794/1*blQsTCUmepOwQsf3qOSAcw.png)

![](https://miro.medium.com/max/1400/1*_KsCSl0FYeKEMLiZkaAHTA.png)