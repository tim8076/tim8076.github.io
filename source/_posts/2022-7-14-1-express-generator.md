---
title: Express框架(8) express-generator
date: 2022-07-14 16:04:20
categories: Node.js
tags: 
- Node.js
- Express
description: '使用express-generator產生專案'
---

## 安裝產生器

我們可以用express 產生器快速建立一個nodeJs專案。

``` 
npm install express-generator -g  // 安裝套件
```

使用 -h 選項來顯示指令選項：

```
$ express -h
  Usage: express [options][dir]
  Options:

    -h, --help          output usage information
        --version       output the version number
    -e, --ejs           add ejs engine support
        --hbs           add handlebars engine support
        --pug           add pug engine support
    -H, --hogan         add hogan.js engine support
        --no-view       generate without view engine
    -v, --view <engine> add view <engine> support (ejs|hbs|hjs|jade|pug|twig|vash) (defaults to jade)
    -c, --css <engine>  add stylesheet <engine> support (less|stylus|compass|sass) (defaults to plain css)
        --git           add .gitignore
    -f, --force         force on non-empty directory
```

舉例來說，以下是在現行工作目錄中建立一個名為 myapp 的 Express 應用程式：

```
$ express --view=pug myapp

   create : myapp
   create : myapp/package.json
   create : myapp/app.js
   create : myapp/public
   create : myapp/public/javascripts
   create : myapp/public/images
   create : myapp/routes
   create : myapp/routes/index.js
   create : myapp/routes/users.js
   create : myapp/public/stylesheets
   create : myapp/public/stylesheets/style.css
   create : myapp/views
   create : myapp/views/index.pug
   create : myapp/views/layout.pug
   create : myapp/views/error.pug
   create : myapp/bin
   create : myapp/bin/www
```

然後安裝相依項目：

```
$ cd myapp
$ npm install
```

執行專案

```
npm start
```


