---
title: Mongoose (4) populate介紹
date: 2022-07-28 21:39:13
tags:
- Mongoose
- Express
description: '使用populate擴展屬性內容'
---

## model 關聯屬性建立

在 mongoose 的 modle 屬性裡，我們可以互相連結不同 model 的資料

``` js
const ProductSchema = new mongoose.Schema(
  {
    name: {
      type: String,
    },
    user: {
      type: mongoose.Types.ObjectId,
      ref: 'User',
      required: true,
    },
  })
```

例如上面的 product 的 schema 我連結了 user 的資料。

## 使用 populate 擴展資料

在沒有 populate前，當我們get product資料時，只會得到 user的 id。

但我們可以使用 populate 來擴展 user 的完整資料

``` js
const getAllProducts = async (req, res) => {
  const products = await Review.find({})
  .populate({
    path: 'user',
    select: 'name age gender',
  })
  res.status(StatusCodes.OK).json({ products });
}
```

populate可用屬性

- path: 要擴展的屬性名稱
- select: 需要擴展的key



