---
title: Mongoose (4) middleware介紹
date: 2022-07-20 10:24:53
tags:
- Mongoose
- Express
description: '使用middleware'
---

## 使用middleware

在mongoose裡，我們也可以使用middleware函式，middlware作用在schema層級，分為  pre and post 兩種，以下介紹使用方法。

## 使用 pre 函示

``` js
const UserSchema = new mongoose.Schema({
  name: String,
  password: String
})

UserSchema.pre('save', async function() {
  const salt = await bcrypt.genSalt(10);
  this.password = await bcrypt.hash(this.password, salt);
})
```

document middleware可以被綁定不同的函式如下:
- validate
- save
- remove
- updateOne
- deleteOne

如上例 ， 當UserSchema被儲存 `.save()` 時，會先觸發middleware將password加密。





