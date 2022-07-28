---
title: Express實戰系列(1) 製作註冊登入功能
date: 2022-07-20 21:16:43
tags: Express實戰系列
description: '製作註冊登入功能'
---

## 環境簡介

``` 
- controllers  
  - auth.js
- model
  - User.js
- route    
  - auth.js
- middleware
  - authentication
```

這次要製作註冊登入功能，route 和 controllers 資料夾理會有 auth的 路由(route) 和 函式(controller)，另外有建立User的model。本次使用 express搭配 mongoDB製作。

## 建立User的schema

首先在 model裡的 User.js建立user的 schema，也就是每筆使用者的資料格式，包括用戶姓名、email、password等等。會用到mongoose提供的驗證方法。

``` js
const UserSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, 'Please provide name'],
    maxlength: 50,
    minlength: 3,
  },
  email: {
    type: String,
    required: [true, 'Please provide email'],
    match: [
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
      'Please provide a valid email',
    ],
    unique: true,
  },
  password: {
    type: String,
    required: [true, 'Please provide password'],
    minlength: 6,
  },
})
```

在user的schema裡可以新增加密的方法，使用 bcrypt套件來對password加密，因為希望password加密後再存入資料庫。

``` js
UserSchema.pre('save', async function () {
  const salt = await bcrypt.genSalt(10)
  this.password = await bcrypt.hash(this.password, salt)
})
```


## 註冊路由

註冊使用者的 controller 函式如下: 

``` js
const User = require('../models/User')
const { StatusCodes } = require('http-status-codes')
const { BadRequestError, UnauthenticatedError } = require('../errors')

// 使用者註冊
const register = async (req, res) => {
  const user = await User.create({ ...req.body })
  const token = user.createJWT()
  res.status(StatusCodes.CREATED).json({ user: { name: user.name }, token })
}
```

製作註冊功能時，使用者在前端會傳入 name 跟 password 的資料，資料會以物件方式存在 req.body裡

``` js
{
  name: '王曉明',
  password: '123456'
}
```
當路由收到資料後，用 `.create()`建立新的使用者，此時如果使用少傳了name或password，會觸發 mongoose 的驗證機制，直接拋出錯誤。

建立使用者後，用寫在[User的schema上的方法](https://tim8076.github.io/2022/07/17/2022-7-17-8-mongoose-model/?highlight=schema#schema-%E5%8A%A0%E4%B8%8A%E6%96%B9%E6%B3%95)來產生 jwt的 token，最後這個token會回傳給前端做下次登入驗證用，詳細[jwt用法看這裡](https://tim8076.github.io/2022/07/18/2022-7-18-1-jwt/?highlight=jwt#%E5%AF%A6%E6%88%B0%E5%8A%A0%E5%AF%86%E6%B5%81%E7%A8%8B)

``` js
UserSchema.methods.createJWT = function () {
  return jwt.sign(
    { userId: this._id, name: this.name },
    process.env.JWT_SECRET,
    {
      expiresIn: process.env.JWT_LIFETIME,
    }
  )
}
```

## 登入路由

當使用者成功註冊後，可以進行登入

``` js
const login = async (req, res) => {
  const { email, password } = req.body

  if (!email || !password) {
    throw new BadRequestError('Please provide email and password')
  }
  const user = await User.findOne({ email })
  if (!user) {
    throw new UnauthenticatedError('Invalid Credentials')
  }
  const isPasswordCorrect = await user.comparePassword(password)
  if (!isPasswordCorrect) {
    throw new UnauthenticatedError('Invalid Credentials')
  }
  // compare password
  const token = user.createJWT()
  res.status(StatusCodes.OK).json({ user: { name: user.name }, token })
}
```
首先從req.body裡可以取得前端傳來的 email和password資料

1. 先檢查 email 和 password 是否存在，不存在的話直接丟出錯誤。

2. 確認有帳密資料後，用 email資料取得資料庫裡對應的user資料，如果找不到user則回傳錯誤。

3. 再來比對使用者輸入的密碼是否一樣，使用 bcrypt套件裡的compare功能，比對的函式一樣放在UserSchema的methods裡。

``` js
UserSchema.methods.comparePassword = async function (canditatePassword) {
  const isMatch = await bcrypt.compare(canditatePassword, this.password)
  return isMatch
}
``` 

確認密碼一樣後，就可以新增 jwt token 並回傳端，登入成功。

## 新增驗證的middleware

使用者註冊和登入後，前端會獲得token，作為之後驗證使用。可以在middleware資料夾內新增 autentication的js檔。

``` js
const auth = async (req, res, next) => {
  const authHeader = req.headers.authorization;
  if (!authHeader || !authHeader.startsWith('Bearer')) {
    throw new UnauthenticatedError('Authentication invalid')
  }
  const token = authHeader.split(' ')[1];
  try {
    const payload = jwt.verify(token, process.env.JWT_SECRET);
    req.user = { userId: payload.userId, name: payload.name };
    next();
  } catch(err) {
    throw new UnauthenticatedError('Authentication invalid')
  }
}
```
在驗證邏輯中，前端會將token放在headers.authorization裡，所以先判斷 req 裡有沒有 authorization 的資料，沒有則回報錯誤。
若有則將token字串取出，之後用

```
jwt.verify(token, token金鑰)
```

將token資料解析回當初加密前的物件格式

``` js
{
  name: 'user',
  userId: '123456'
}
```
取得物件後，就將資訊存在 req.user裡，方便之後再路由裡取得user資訊。






