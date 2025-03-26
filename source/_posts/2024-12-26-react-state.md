---
title: React (9) state 定義建議方式
date: 2024-12-26 15:51:12
categories: React
tags: React
description: '介紹 React state 定義建議方式'
---

當你撰寫元件的 state 時，必須對使用多少個state以及其資料類型做出選擇。雖然即使使用次佳的狀態結構也可以撰寫出正確的程式，但有一些原則可以指導你做出更好的選擇：

## 將相關的 state 合併

當某些 state 經常會一起改變時，可以將它們合併成一個 state。

```js
// 合併前
const [x, setX] = useState(0);
const [y, setY] = useState(0);
```

```js
// 合併後
const [position, setPosition] = useState({ x: 0, y: 0 });
```

或是當你不知道你需要多少 state 時，也可以將這些 state 定義成物件或陣列，方便之後擴充。

```js
const [userData, setUserData] = useState({
  name: '',
  tel: '',
  address: '',
})
```

## 避免矛盾的 state

```js
  const [text, setText] = useState('');
  const [isSending, setIsSending] = useState(false);
  const [isSent, setIsSent] = useState(false);
```

上面是一個表單的 state，其中 isSending 和 isSent ，不可能同時為 true。比較好的方式是將其整合為一個 state。

```js
const [text, setText] = useState('');
const [status, setStatus] = useState('typing');
// 三種狀態，typing、sending、sent
```

## 避免多餘的 state

如果你需要的狀態可以從其他 state 計算出來，就不該將這個狀態設為 state。

```js
const [firstName, setFirstName] = useState('');
const [lastName, setLastName] = useState('');
const [fullName, setFullName] = useState('');
```

上面 fullName 這個狀態可以從 firstName 和 lastName 計算出來，就不需設為 state。

```js
const [firstName, setFirstName] = useState('');
const [lastName, setLastName] = useState('');
const fullName = firstName + ' ' + lastName;
```

fullName 可以在元件渲染時，從 firstName 和 lastName 計算出來。

## 避免重複的 state

```js
const initialItems = [
  { title: 'pretzels', id: 0 },
  { title: 'crispy seaweed', id: 1 },
  { title: 'granola bar', id: 2 },
];

export default function Menu() {
  const [items, setItems] = useState(initialItems);
  const [selectedItem, setSelectedItem] = useState(
    items[0]
  );
}
```

上面範例中，items[0]的狀態同時存在在兩個 state 中，可能導致修改了 items 的狀態，卻忘記同時修改 selectedItem 的狀態。

```js
const [items, setItems] = useState(initialItems);
const [selectedId, setSelectedId] = useState(0);

const selectedItem = items.find(item =>
  item.id === selectedId
);
```

比較好的做法是另外定義 selectedId，在元件渲染時再計算出 selectedItem 即可。

## 避免多層結構的 state

深層嵌套的結構會使狀態的管理和更新變得複雜，代碼更難閱讀和維護。

```js
// 深層結構的 state
const [state, setState] = useState({
  user: {
    profile: {
      name: "Alice",
      age: 30,
    },
    settings: {
      theme: "dark",
      notifications: true,
    },
  },
});
```

可以將深層嵌套的結構展平，將每一層級的數據存為獨立的鍵值。

```js
const [profile, setProfile] = useState({ name: "Alice", age: 30 });
const [settings, setSettings] = useState({ theme: "dark", notifications: true });
```