---
title: React (13) React 和 Typescript
date: 2025-09-03 11:24:17
categories: React
tags: React
description: 'React 中使用 typescript'
---

## Props 型別

元件中的 props 要帶入型別檢查，有以下寫法:


- 行內型別: 最簡單、但不適合 props 太多的情況。

```tsx
function MyButton({ title }: { title: string }) {
  return (
    <button>{title}</button>
  );
}
```
props 物件必須是一個 有 title 屬性的物件，且 title 的型別必須是 string。

- Type Alias: 

```jsx
type ButtonProps = {
  title: string;
  size: number;
};

function MyButton({ title, size }: ButtonProps) {
  return <button style={{ fontSize: size }}>{title}</button>;
}
```

- Interface: 和 type 類似，但更適合在大型專案中擴充（可以繼承）。

```tsx
interface ButtonProps {
  title: string;
  size: number;
}

function MyButton({ title, size }: ButtonProps) {
  return <button style={{ fontSize: size }}>{title}</button>;
}
```

## Hook 中的型別檢查

### useState

```tsx
// Infer the type as "boolean"
const [enabled, setEnabled] = useState(false);
```

useState 會依照初始值，自動綁定型別，如上 enabled 只能是 boolean。

```tsx
const [enabled, setEnabled] = useState<boolean>(false);
```

useState 型別也能自己在 <> 內加上

```tsx
type Status = "idle" | "loading" | "success" | "error";
const [status, setStatus] = useState<Status>("idle");
```

也能帶入自己定義的 union type

```tsx
type User = {
  id: number;
  name: string;
  email?: string; // 可選欄位
};
const [user, setUser] = useState<User>({ id: 1, name: "Tim" });
```

可以使用 type 檢查物件內型別

```tsx
const [items, setItems] = useState<string[]>([]); // 陣列裡都是 string
```

陣列型別檢查

### useReducer

```tsx
type State = { count: number };
type Action =
  | { type: "increment" }
  | { type: "decrement" }
  | { type: "set"; payload: number };

function reducer(state: State, action: Action): State {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "set":
      return { count: action.payload };
    default:
      return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });

// 使用
dispatch({ type: "set", payload: 100 });
```

### useContext

```tsx
import React, { createContext, useContext, useState } from "react";

// 1️⃣ 定義 Context 的資料型別
type User = {
  name: string;
  age: number;
  login: () => void;
};

// 2️⃣ 建立 context，初始值可以先用 null
const UserContext = createContext<User | null>(null);

// 3️⃣ 建立 Provider
export function UserProvider({ children }: { children: React.ReactNode }) {
  const [name, setName] = useState("Tim");
  const [age, setAge] = useState(20);

  const login = () => console.log("User logged in");

  const value: User = { name, age, login };

  return <UserContext.Provider value={value}>{children}</UserContext.Provider>;
}
```

## Dom Events

事件監聽的 typescript 寫法

- Input 的 change 事件

```tsx
export default function InputBox() {
  const [value, setValue] = useState("");

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setValue(e.target.value);
  };

  return <input type="text" value={value} onChange={handleChange} />;
}
```

- Button 的 click 事件

```tsx
const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
  console.log("Button clicked", e.clientX, e.clientY);
};

export default function App() {
  return <button onClick={handleClick}>Click me</button>;
}
```

- Form submit 事件

```tsx
const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
  e.preventDefault(); // 阻止預設提交
  console.log("Form submitted");
};

export default function MyForm() {
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

- Keyboard 事件

```tsx
const handleKeyDown = (e: React.KeyboardEvent<HTMLInputElement>) => {
  if (e.key === "Enter") {
    console.log("Enter pressed");
  }
};

export default function InputKey() {
  return <input onKeyDown={handleKeyDown} />;
}
```

## Children

React 裡的 children 通常使用 React.ReactNode：

```tsx
type CardProps = {
  title: string;
  children: React.ReactNode; // 支援文字、元素、陣列、Fragment 等
};

export function Card({ title, children }: CardProps) {
  return (
    <div className="card">
      <h2>{title}</h2>
      {children}
    </div>
  );
}
```

您好，我是周廷祐。之前是做行政工作，後來在前端培訓班中進修，熟悉 React、HTML、CSS，
希望能在公司中與團隊合作並持續加強前端開發能力。