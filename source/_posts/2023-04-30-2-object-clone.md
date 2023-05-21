---
title: Js裡物件的拷貝
date: 2023-04-30 15:17:15
categories: Javascript
description: '物件的淺拷貝與深拷貝'
---

## 複製物件

``` js
let obj1 = {
  food: 'rice'
}
let obj2 = obj1;

obj1.food = 'noodle';

console.log(obj2.food) // 'noodle';
```

在js裡若複製的資料型態是物件時，我們複製的其實是改物件的記憶體位置，如上例，obj2 和 obj1都指向同一個記憶體位置，所以當改變obj1裡的值時，obj2同時會被改變。

## 淺拷貝

為了避免這個問題，我們可以用淺拷貝的方式，也就是新建立一個物件，將原本資料全部的屬性都複製進去。

### Object.assign()

``` js
let obj1 = {
  food: 'rice',
}

let obj2 = Object.assign({}, obj1);
obj1.food = 'noodle';

console.log(obj2.food) // 'rice'
```

或是利用es6的展開運算子寫法

``` js
let obj1 = {
  food: 'rice',
}

let obj2 = { ...obj1 };
obj1.food = 'noodle';

console.log(obj2.food) // 'rice'

```
利用這個方法，可以拷貝物件裡第一層的屬性，但如果物件中屬性的值也是物件，就無法拷貝。

## 深拷貝

``` js
let obj1 = {
  food: 'rice',
  flavor: ['spicy', 'sweet']
}

let obj2 = Json.parse(JSON.stringify(obj1));
obj1.food = 'noodle';
obj1.flavor[0] = 'sour';

console.log(obj2.food) // 'rice'
console.log(obj2.flavor) // ['spicy', 'sweet']
```

若要連物件內的物件也拷貝，可以使用深拷貝的方法，就是將物件依序經過 JSON.stringify 及 JSON.parse 兩個方法，建立全新的物件。

上例中可以發現 obj2經過深拷貝後，就算改動 obj1內陣列的值，obj2也不會被影響。

