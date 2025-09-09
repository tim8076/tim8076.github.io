---
title: Typescript (3) Type Aliases
date: 2025-09-02 15:23:52
categories: Typescript
description: "用 Aliases 替型別命名"
---

## 什麼是 Aliases

在 TypeScript 裡，Type Alias（型別別名） 是用 type 關鍵字來 為一個型別取名字。
👉 它本質上只是「型別的別名」，不會建立新的型別。

## 基本語法

```ts
type ID = number;
type Username = string;

let userId: ID = 123;
let userName: Username = "Alice";
```

這裡的 ID 和 Username 只是 number 與 string 的別名，方便程式更具語意。

## 搭配陣列

```ts
type Rgb = [number, number, number];

function getRandomColor(): Rgb {
  const r = Math.floor(Math.random() * 255);
  const g = Math.floor(Math.random() * 255);
  const b = Math.floor(Math.random() * 255);
  return [r, g, b];
}

const color1 = getRandomColor();
const color2 = getRandomColor();
```

## 搭配物件

```ts
type User = {
  name: string,
  score: number,
}

const userOne: User = {
  name: 'mario',
  score: 72,
}

function formatUser(user: User) {
  console.log(`${user.name} has score ${user.score}`)
}
formatUser(userOne);
```





