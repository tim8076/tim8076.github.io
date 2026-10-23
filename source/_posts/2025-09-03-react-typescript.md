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

## useRef

綁定 dom 時

```tsx
export const DomRef = () => {
  const inputRef = useRef<HTMLInputElement>(null!);
  // 使用了 !（TypeScript 的斷言），
  // 告訴編譯器「我知道它一開始是 null，但之後一定會被填入值」，
  // 以此繞過 TypeScript 的嚴格型別檢查。

  useEffect(() => {
    if (inputRef.current) {
      inputRef.current.focus();
    }
  }, []);

  return (
    <div>
      <input ref={inputRef} type="text" />
    </div>
  );
}
```

綁定資料時

```tsx
export const MutableRef = () => {
  const [timer, setTimer] = useState(0);
  const intervalRef = useRef<number | null>(null);

  const stopTimer = () => {
    if (intervalRef.current) {
      window.clearInterval(intervalRef.current);
    }
  }
  useEffect(() => {
    intervalRef.current = window.setInterval(() => {
      setTimer(prevTimer => prevTimer + 1);
    }, 1000)
    return () => {stopTimer()}
  }, [])

  return (
    <div>
      <p>Timer: {timer}</p>
      <button onClick={stopTimer}>Stop Timer</button>
    </div>
  )
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

## Style

React 裡的 style 使用 React.CSSProperties：

```tsx
type ContainerProps = {
  style?: React.CSSProperties;
};

export function Container({ style }: ContainerProps) {
  return (
    <div style={style}>
      Text content
    </div>
  )
}
```

## import types

可以將 type 獨立一個檔案，並 import 使用

``` tsx
// Person.types.ts
export type PersonProps = {
  personName: {
    first: string;
    last: string;
  }
}
```

```tsx
import type { PersonProps } from "./Person.types"
export function Person({ personName }: PersonProps) {
  return <div>{personName.first} {personName.last}</div>
}
```

## class component

```tsx
import { Component } from "react";

type CounterProps = {
  message: string;
};

type CounterState = {
  count: number;
};

export class Counter extends Component<CounterProps, CounterState> {
  state = {
    count: 0,
  }
  handleClick = () => {
    this.setState((prevState) => ({
      count: prevState.count + 1,
    }));
  }
  render() {
    return (
      <div>
        <h1>{this.props.message} {this.state.count}</h1>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}
```

## 當props 為元件時

type 為 React.ComponentType

```tsx
import {Login} from './Login';
import type { ProfileProps } from './Profile';

type PrivateProps = {
  isLogIn: boolean;
  component: React.ComponentType<ProfileProps>;
};
export function Private({ isLogIn, component: Component }: PrivateProps) {
  if (isLogIn) {
    return <Component name="John Doe" />;
  } else {
    return <Login />;
  }
}
```

## 型別斷言

```tsx
type AuthUser = {
  name: string,
  email: string
}

const [user, setUser] = useState<AuthUser>({} as AuthUser);
```

是 React + TypeScript 很常見的寫法，它包含了三個重點：

1. useState<AuthUser>
2. {} 空物件
3. as AuthUser 型別斷言（Type Assertion）

我知道現在它是空的物件，但請先把它當成 AuthUser。

## 限制Props

這段程式碼是 TypeScript 的 Union Type（聯集型別）+ Intersection Type（交集型別）+ never 的經典應用，用來限制 Props 的組合，避免 React 元件收到不合法的 props。

```tsx
type RandomNumberTypes = {
  value: number;
}

type PositiveNumber = RandomNumberTypes & {
  isPositive: boolean;
  isNegative?: never;
  isZero?: never;
}

type NegativeNumber = RandomNumberTypes & {
  isNegative: boolean;
  isPositive?: never;
  isZero?: never;
}

type ZeroNumber = RandomNumberTypes & {
  isZero: boolean;
  isPositive?: never;
  isNegative?: never;
}

type RandomNumberProps = PositiveNumber | NegativeNumber | ZeroNumber;
export function RandomNumber({
  value,
  isPositive,
  isNegative,
  isZero
}: RandomNumberProps) {
  return (
    <div>
      { value } { isPositive && 'positive' } {isNegative && 'negative'} {' '}
      {isZero && 'zero'}
    </div>
  )
}
```

## Template Literal Type

```js
type HorizontalPosition = 'left' | 'center' | 'right';
type VerticalPosition = 'top' | 'center' | 'bottom';

type ToastProps = { position: `${VerticalPosition}-${HorizontalPosition}`; };
```

這是 TypeScript 的 模板字面量型別。
它會把兩個 union 自動組合。相當於：

```tsx
type Position =
  | "top-left"
  | "top-center"
  | "top-right"
  | "center-left"
  | "center-center"
  | "center-right"
  | "bottom-left"
  | "bottom-center"
  | "bottom-right";
```

但因為 position 不會有 'center-center'，可以用 `Exclude<T, U>` 方法，
意思：從 T 裡面，把 U 移除。


```tsx
type positionProps = { 
  position:Exclude<`${VerticalPosition}-${HorizontalPosition}`,
   'center-center'>
}
```

## HTML element

利用 React.ComponentProps<'button'> 繼承 HTML <button> 的所有屬性。

```tsx
type ButtonProps = {
  varients: 'primary' | 'secondary';
} & React.ComponentProps<'button'>;

export default function CustomButton({ varients, children, ...rest }: ButtonProps) {
  return (
    <button className={`btn btn-${varients}`} {...rest}>
      {children}
    </button>
  )
}
```

## 複製別的元件的props type

這段程式碼的重點在於 React.ComponentProps<typeof Greet>。
它可以直接取得另一個 React 元件的 Props 型別，不用再自己重新定義一次。

```tsx
import type { Greet } from "../Greet"

const CustomComponent = (props: React.ComponentProps<typeof Greet>) => {
  return (
    <div>
      {props.name}
    </div>
  )
}
```

