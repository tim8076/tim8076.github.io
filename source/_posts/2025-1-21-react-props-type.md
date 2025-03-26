---
title: React (12) React Prop types
date: 2025-01-21 16:29:11
categories: React
tags: React
description: '介紹 React Prop types 原理'
---

## 安裝與使用

在 React 中，PropTypes 用於驗證元件接收的 props 是否符合預期的類型或格式。這有助於在開發時捕捉錯誤，提升元件的可維護性。


1. 安裝 prop-types

```
npm install prop-types
```

2. 在元件中使用 PropTypes：

```jsx
import React from 'react';
import PropTypes from 'prop-types';

const MyComponent = ({ name, age, isActive, tags }) => {
  return (
    <div>
      <h1>{name}</h1>
      <p>年齡: {age}</p>
      <p>狀態: {isActive ? '啟用中' : '未啟用'}</p>
      <ul>
        {tags.map((tag, index) => (
          <li key={index}>{tag}</li>
        ))}
      </ul>
    </div>
  );
};

MyComponent.propTypes = {
  name: PropTypes.string.isRequired, // 必填，需為字串
  age: PropTypes.number,            // 選填，需為數字
  isActive: PropTypes.bool,         // 選填，需為布林值
  tags: PropTypes.arrayOf(          // 選填，需為字串陣列
    PropTypes.string
  ),
};
export default MyComponent;
```

## 常見 PropTypes 類型

- PropTypes.string：字串
- PropTypes.number：數字
- PropTypes.bool：布林值
- PropTypes.array：陣列
- PropTypes.object：物件
- PropTypes.func：函式

進階驗證

- PropTypes.arrayOf(PropTypes.string)：必須是陣列，且陣列裡要是數字。
- PropTypes.shape({
  street: PropTypes.string,
  city: PropTypes.string,
})：對物件做深層驗證

## 陣列與物件進階運用

### 陣列包物件驗證方法

```js
const friends = [
  { name: '漂亮阿姨', age: 21 },
  { name: '杰倫', age: 19 },
  { name: '小美', age: 16 }
]

MyComponent.propTypes = {
  friends: PropTypes.arrayOf(
    PropTypes.shape({
      name: PropTypes.string.isRequired,
      age: PropTypes.number.isRequired,
    })
  ),
};
```

### 陣列包各種值

用 onOfType 方法驗證可能的值

```js
const tags = [
  '喜歡漂亮阿姨',
  18,
  { type: '飲食', description: '喜歡鍋燒意麵' },
  true
];

MyComponent.propTypes = {
  tags: PropTypes.arrayOf(
    PropTypes.onOfType([
      PropTypes.string,
      PropTypes.number,
      PropTypes.shape({
        type: PropTypes.string,
        description: PropTypes.string
      })
    ])
  ),
};
```

### 驗證指定的值

```js
const status = '啟用中'

MyComponent.propTypes = {
  status: PropTypes.oneOf(['啟用中', '暫停', '未完成']), // 僅能是這三個值其中之一
};
```