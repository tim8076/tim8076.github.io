---
title: Factory function 工廠函式
date: 2023-08-27 15:04:18
categories: Javascript
description: '使用工廠函式產生物件'
---

## 遇到的問題

``` js
const me = {
  name: 'Sina',
  talk() {
    console.log(`My name is ${this.name}`)
  },
}

const you = {
  name: 'Tim',
  talk() {
    console.log(`My name is ${this.name}`);
  },
}

me.talk() // My name is Sina
you.talk() // My name is Tim

me.name = 'Tom'
me.talk() // My name is Tom
```

當我們有許多屬性一樣的物件時，若直接撰寫物件，會多出許多重複的code，並且物件的屬性是可以直接被修改，容易造成bug。

這時可以改用工廠函式來產生這些物件。

## 工廠函式

``` js
function Person(name) {
  return {
    name,
    talk() {
      console.log(`My name is ${name}`)
    }
  }
}

const me = Person('Tom');
me.talk() // My name is Tom
```

工廠函式即是用函式直接回傳一個新的物件，物件的屬性的值可由函式的參數傳入。如此不僅避免重複的code，也防止物件的內容被任意修改。

## 範例

``` js
function createElement(type, text, color) {
  const el = document.createElement(type);
  el.innerText = text;
  el.style.color = color;
  document.body.append(el);

  return {
    el,
    setText(text) {
      el.innerText = text,
    },
    setColor(color) {
      el.style.color = color,
    },
  }
}

const h1 = createElement('h1', 'Hey guys', 'red');

```

上面範例中使用工廠函式來快速製造 h1 元素並掛載到dom上。

## 工廠函式的問題

``` js
function Person(name) {
  return {
    name,
    talk() {
      console.log(`My name is ${name}`)
    }
  }
}

const me = Person('Tom');
const you = Person('Lisa');

me.talk = function() {
  return `Hello I am ${this.name}`;
}

me.talk() // Hello I am Tom
you.talk() // My name is Lisa
```

使用工廠函式產生物件時，每個回傳的物件都是獨立的記憶體位置，如上我修改了 me.talk()的函式內容，
you.talk()並不會被修改，因為兩個是不同的獨立物件。


### 解決方法

``` js
const myProto = {
  talk() {
    return `I am ${this.name}`
  }
}

function createPerson(name) {
  return Object.create(myProto, {
    name: {
      value: name,
    }
  })
}

const me = createPerson('Sina');
const you = createPerson('Lisa');
```

這次在工廠函式中，我們不直接回傳一個物件，而是用 Object.create() 方法，指定 myProto 為 prototype物件，
這樣 me.talk() 和 you.talk() 就會指向同一個函式了。








