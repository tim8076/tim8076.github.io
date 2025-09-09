---
title: Typescript (2) 基本型別定義
date: 2025-09-01 14:23:46
categories: Typescript
description: "Typescript 基本型別定義"
---

## 基本型別定義

typescript 可以在宣告變數時，後面加上 :型別 的方式來定義，型別定義後就不能被賦予其他型別的值


```ts
let age: number = 30;  // 定義型別 number
let firstName: string = 'mario'; // 定義型別 string
let isFictional: boolean; // 定義型別 boolean
let something: null;  // 定義型別 null
let anotherSomething: undefined; // 定義型別 undefined
```

## 陣列與物件型別

```ts
// 定義型別為陣列，且陣列內型別為 string
const names: string[] = ['Mario', 'Lucy', 'Peach'];
// 定義型別為陣列，且陣列內型別為 number
const ages: number[] = [1, 2, 3];

// 定義型別為物件，且物件內只能有指定的屬性和對應型別
const users: {
  firstName: string,
  age: number,
  id: number
} = {
  firstName: 'mario',
  age: 30,
  id: 1,
}
```

## 函式

```ts
// 定義函式內的參數與型別，與回傳值的型別
function addTwoNums(a:number, b:number): number {
  return a + b;
}

const substractTwoNumber = (a:number, b:number): number => {
  return a - b;
}

// 回傳值的型別可以被自動計算，所以可以省略如下
function addAllNumbers(items: number[]) {
  const total = items.reduce((sum, num) => sum + num, 0);
  return total;
}
```

## any 型別

如果宣告變數為 any 型別，代表該變數可以是任何型別。

```ts
// 宣告型別為 any 或宣告變數但不給型別，都代表 any 型別。
let age: any;
let title;

age = 30;
age = false;

title = 'text';
title = 5;
```

陣列內的 any 型別

```ts
let things: any[] = ['hello', 123, true]
```

函式內的 any 型別

```ts
function callName(value: any): any {
  return value + value
}

const resultOne = callName('hello')
const resultTwo = callName(5)
```

## tuple 型別

Tuple 是一種「固定長度、固定型別順序」的陣列。

```ts
let tuple: [string, number];
tuple = ["Tim", 25];   // ✅ 正確
tuple = [25, "Tim"];   // ❌ 順序錯誤
tuple = ["Tim"];       // ❌ 少一個元素

let hsla: [number, string, string, number];
hsla = [200, '100%', '50%', 1];

function useCoords(): [number, number] {
  const lat = 100;
  const lon = 50;
  return [lat, lon];
}
const [lat, lon] = useCoords();
```

- named tuple:

我們可以在 tuple 的每個元素加上 名稱（label），讓可讀性更好。

```ts
let user = [id: number, name: string, isAdmin?: boolean];
```

這裡的 id、name、isAdmin 就是 tuple 的具名元素，第一個值代表 id，第二個代表名稱，帶三個代表是否為會員。

## Interface

在 TypeScript 裡，interface（介面）是一種用來定義物件結構的型別。它主要用於描述 物件有哪些屬性、屬性的型別、方法簽名。

```ts
interface Post {
  title: string,
  body: string,
  tags: string[],
  created_at: Date,
}

const newPost: Post = {
  title: 'my first post',
  body: 'something',
  tags: ['game', 'life'],
  created_at: new Date(),
}
```

函式中使用

```ts
function createPost(post: Post):void {
  console.log(`Created post ${post.title} by ${post.author.name}`)
}

createPost({
  title: 'my post',
  body: 'my body',
  tags: ['life'],
  created_at: new Date(),
  author: authorOne
});
```

陣列中使用

```ts
let posts: Post[] = [];

posts.push({
  title: 'my first post',
  body: 'something',
  tags: ['game', 'life'],
  created_at: new Date(),
  author: authorOne
})
```

## Union Types

在 TypeScript 中，Union Types 允許一個變數可以是 多種型別 之一。
用 |（直線符號）來連接多個型別。
這在實務上很常用，因為有時候資料來源不只一種型別。

```ts
let value: string | number;

value = "Hello"; // ✅ 合法
value = 123;     // ✅ 合法
value = true;    // ❌ 錯誤，因為沒包含 boolean
```

函式參數中的 Union Types

```ts
function printId(id: number | string) {
  console.log("Your ID is: " + id);
}

printId(101);    // ✅ number
printId("abc");  // ✅ string
```

如果函式參數使用 Union Types，. 只能使用所有型別「共有」的方法或屬性

```ts
function printLength(value: string | string[]) {
  console.log(value.length); // ✅ OK
}

function toUpperCase(value: string | number) {
  console.log(value.toUpperCase()); // ❌ Error: number 沒有 toUpperCase()
}
```

解法是先判斷型別

```ts
function swapId(id: number | string) {
  if (typeof id === 'string') {
    return parseInt(id);
  } else {
    return id.toString();
  }
}
```

與 Array 搭配

```ts
let data: (string | number)[] = [1, "apple", 2, "banana"];

data.push(3);        // ✅
data.push("cherry"); // ✅
data.push(true);     // ❌
```







