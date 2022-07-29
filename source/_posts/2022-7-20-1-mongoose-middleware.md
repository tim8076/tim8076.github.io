---
title: Mongoose (4) middleware介紹
date: 2022-07-20 10:24:53
tags:
- Mongoose
- Express
description: '使用middleware'
---

## 使用 middleware

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

## 範例 連帶移除資料

假設我們在資料庫想刪除一筆 product 資料，並連帶刪除所有該 product 的review資料，可以先用 .remove() 刪除該product

``` js
const deleteProduct = async (req, res) => {
  const productId = req.params.id;
  const product = await Product.findOne({ _id: productId });
  await product.remove();
  res.status(StatusCodes.OK).json({ msg: 'success product removed' })
};
```

在 product的 schema 上用pre hook來刪除連帶的 reviews資料

``` js
ProductSchema.pre('remove', async function(next) {
  await this.model('Review').deleteMany({ product: this._id });
})
```

await product.remove() 會觸發 schema上的 pre hook，先用 this.model('Review')連到 reivew model，在將所有 包含product id的review刪除。








