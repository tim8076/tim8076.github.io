---
title: Express實戰系列(2) 使用cookie傳送JWT token
date: 2022-07-24 19:56:22
tags: 
- cookie
- Express實戰系列
description: '使用cookie傳送JWT token'
---

## 註冊功能

``` js
const attatchCookieToResponse = ({ res, user }) => {
  const token = createJWT({ payload: user });
  const oneDay = 1000 * 60 * 60 * 24; //one day in miliseconds
  res.cookie('token', token, {
    httpOnly: true,
    expires: new Date(Date.now() + oneDay),
    secure: process.env.NODE_ENV === 'production',
    signed: true,
  })
}
```

使用res.cookie 回傳 jwt 產生的token，

``` js
const register = async (req, res) => {
  const { email, name, password } = req.body;
  const user = new User({ email, password, name, role });
  await user.save();
  const tokenUser = { 
    name: user.name, 
    userId: user._id, 
    role: user.role 
  };
  attatchCookieToResponse({ res, user: tokenUser });
  res.status(StatusCodes.CREATED).json({ user: tokenUser });
}
```

