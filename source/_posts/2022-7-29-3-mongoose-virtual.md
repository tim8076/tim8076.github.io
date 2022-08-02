---
title: Mongoose (6) virtual
date: 2022-07-29 21:02:42
tags:
- Mongoose
- Express
description: '使用 virtual 擴展屬性內容'
---

## virtual

我們知道可以用 populate 來擴展實際在model裡有聯結的屬性，如下我們在 product裡連結了 user

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

但當 model裡沒有連結屬性有想擴展該屬性時，可以用 virtual。

## 開啟virtual

``` js
const ProductSchema = new mongoose.Schema(
  {
    name: {
      type: String,
    },
  }, 
  {
    toJSON: { virtuals: true },
    toObject: { virtuals: true },
  })
```

首先在 schema的第二個參數裡，將 toJSON 、toObject 的 virtuals 設為 true，讓schema能接收 vritual。

## 設定 virtual

``` js
ProductSchema.virtual('reviews', {
  ref: 'Review',
  localField: '_id',
  foreignField: 'product',
  justOne: false,
  match: { rating: 5 }
})
```

在 productSchema 上先設定 virtual 連結到 reviews

- ref: 要連結的 model 名稱
- localField: schema要連結的屬性
- foreignField: 連結model裡的屬性
- justone: 是否只取回一筆資料
- match: 只取回符合條件的資料

以上範例中，在productSchema上新增一個 virtual的屬性命名為 reviews，將ref設定為 'Review' 來取得Review model的資料。
在 localField 中設定 '_id' 代表 product 的id， foreignField 設為 product 則會將 Review model 裡所有有該 product id的reviews回傳。


## pupulate

當以上都設定好後，在controller裡 populate 該 virtual 屬性即可

``` js
const getSingleProduct = async (req, res) => {
  const productId = req.params.id;
  const product = await Product.findOne({ _id: productId }).populate({ path: 'reviews' });
};
```

