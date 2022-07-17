---
title: MongoDB (四) 更新與刪除
date: 2022-07-17 10:46:56
tags: MongoDB
description: '更新和刪除mongodb資料'
---

## 資料更新

```
updateOne({被更新的資料}, {更新的值})  // 更新一筆資料
```

![使用$set設定新的值](https://miro.medium.com/max/1400/1*ug2VR90bERK_zuhJmFfx8g.png)

```
inc: 加上指定的值
```

![inc: 加上指定的值](https://miro.medium.com/max/1400/1*W51QCzgqqGCkg1kerrN5zQ.png)


```
rename: 更改資料的key值
```

![將name欄位改為lora欄位](https://miro.medium.com/max/1400/1*HY-saJY9Gpey46CwgZ5oUg.png)


```
unset: 移除指定欄位，欄位值設為" "
```

![移除age欄位](https://miro.medium.com/max/1400/1*-Mua6NP_A-PuJvpEEL3OaA.png)


```
push: 新增值到陣列裡
```

![新增swimming到hobbies陣列裡](https://miro.medium.com/max/1400/1*cmlaV3bI4wBQIEHXQLfygw.png)


```
pull: 移除陣列裡的值
```

![移除陣列裡Running的值](https://miro.medium.com/max/1400/1*soqRd9QGuXDnt0fV-OWsMQ.png)

```
updateMan: 更新多筆資料
```

![將所有有address的欄位取消address欄位](https://miro.medium.com/max/1400/1*sRe0B1aVt_Pv46R0II2ifA.png)


## 取代資料

```
replaceOne: 將原本物件刪除後，取代成新的物件
```

![將原本name為lin的物件刪除後，更新成name為linda的物件](https://miro.medium.com/max/1400/1*yjbgM_WfQTt2c7DGmbVPCQ.png)

## 刪除資料

```
deleteOne: 將指定物件刪除
```

![](https://miro.medium.com/max/1180/1*BcicLblVY6EVtI7JwnPe9g.png)

```
deleteMany: 刪除多筆資料
```
