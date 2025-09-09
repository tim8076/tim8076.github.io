---
title: React Native (5) Theme Component
date: 2025-08-14 20:11:04
categories: React Native
description: "Theme Component"
---

## 製作 theme 元件

和網頁的 react 一樣，react native 也能將常用的版型製作成元件

```jsx
import { View, useColorScheme } from 'react-native'
import { Colors } from '../constants/Colors'

const ThemeView = ({ style, ...props }) => {
  const colorScheme = useColorScheme();
  const theme = Colors[colorScheme] ?? Colors.light
  return (
    <View style={[{backgroundColor: theme.background}, style]}
     {...props}
    />
  )
}

export default ThemeView
```

上面是一個套用主題色的元件，預設會帶入 theme.background 的背景色

在頁面上可以這樣套用，ThemeView 內的元素會自動傳入 ThemeView 元件內。

```jsx
import ThemeView from '../components/ThemeView';

const Home = () => {
  return (
    <ThemeView style={styles.container}>
      <Image source={Logo} style={styles.img}/>
      <Text style={[styles.title, { color: 'purple' }]}>
        The Number 1
      </Text>
    </ThemeView>
  )
}
```
