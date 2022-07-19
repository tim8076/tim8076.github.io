---
title: Mongoose (3) model方法介紹
date: 2022-07-17 16:13:59
tags:
- Mongoose
- Express
description: '使用model操作資料'
---

## 搜尋資料

### 搜尋全部資料

``` js
const Person = require('../models/person');
const person = await Person.find({});
```

使用 find 方法傳入空物件，會回傳所有資料。因為find會回傳 .then() ，所以可以用 await 來接收結果。

### 搜尋特定資料

``` js
Person.
  find({
    occupation: /host/,
    'name.last': 'Ghost',
    age: { $gt: 17, $lt: 66 },  // 年齡 >17 && <66
    likes: { $in: ['vaporizing', 'talking'] }
  })
``` 
如果要對值進行篩選，可以在後方加入篩選語法，語法和 [mongodb](https://tim8076.github.io/2022/07/16/2022-7-17-2-mongodb-filter/) 是一樣的。

### 限制資料比數

想限制資料筆數，可以加上 .limit

``` js
Person.find({}).limit(10) // 回傳前10筆資料
```

### 資料排序

要對特定值做排序，用 sort方法，。加上 - 代表降冪排序，反之則正向排序。

``` js
Person.find({}).sort('name -occupation')
```

### 回傳特定的key值

如果只想回傳特定的key值，用 select()。 加上 - 代表降冪排序，反之則正向排序。

``` js
Person.find({}).select('name -gender')
```


## 新增資料

``` js
const Person = require('../models/person');
const person = new Person({ name: 'Kyle', age: 16 });
await person.save();
```
用mongoose新增一筆資料很簡單，假設有一個 Person 的model，只要用 new Person({})帶入新增的值即可建立資料，再用.save()將資料存進資料庫，因為.save()是 async function ，所以記得加上 await。


## 修改資料

``` js
const Person = require('../models/person');
const person = new Person({ name: 'Kyle', age: 16 });
person.name = 'Sally';
await person.save();
```

修改資料可以直接將物件的值賦予新的值，再用 .save() 存入資料庫即可。如上我們將 Kyle 改為 Sally。

## 刪除資料

``` js
const Person = require('../models/person');
await Person.deleteOne({ name: 'Kyle' });
```

deleteOne 會刪除符合條件的第一筆資料。

``` js
const Person = require('../models/person');
await Person.deleteMany({ name: 'Kyle' });
```

deleteMany 刪除所有符合條件的資料。














