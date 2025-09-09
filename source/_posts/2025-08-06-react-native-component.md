---
title: React Native (2) 元件介紹
date: 2025-08-06 20:18:19
categories: React Native
description: "React Native 元件介紹"
---

## 常用內建元件

React Native 提供了一整套內建元件來協助你構建手機 UI，以下是最常見

元件名稱	用途簡介

- View:	排版容器，像是 HTML 的 <div>
- Text	顯示文字內容，像是 <span>、<p>
- ScrollView	可捲動的畫面容器（垂直或水平）
- TextInput	可輸入文字的欄位（輸入框）
- TouchableOpacity	可按的區塊，點擊時有透明動畫效果
- Pressable	更進階的可按元件，支援更多互動控制（新推薦）
- Button	快速建立一個按鈕（但樣式難客製）
- Image	顯示圖片

## View 元件

View 是 React Native 中的基本容器元件，類似於 HTML 裡的 <div>，常用來：

- 排版（flexbox）
- 包裹其他元件
- 加上背景色、邊框、間距、padding 等
- 建構畫面結構層級

React Native 裡所有 `<View>`、`<Text>` 等容器，預設都會以 Flexbox 來排版，並且預設的 flexDirection 是 column（垂直方向）。

```js
export default function App() {
  return (
    <View style={styles.container}>
      <Text>Item 1</Text>
      <Text>Item 2</Text>
    </View>
  );
}
```

## Text 元件

Text 是用來顯示文字的元件，類似於 HTML 的 `<span>` 或 `<p>`，在 React Native 中，所有文字都必須寫在 `<Text>` 裡面，不能直接寫在 `<View>` 內

要注意Text只能包文字，不能包 View

```js
<Text>這是 <Text>粗體</Text> 文字</Text> ✅
<Text><View /></Text> ❌（不能包 View）
```

## Image 元件

載入圖片可以用 Image 元件，使用  source 屬性載入圖片

- 本地圖片: import 後載入
- 遠端圖片: { uri: 'https://...' }

```js
import Logo from '../assets/image/logo.png';
export default function App() {
  return (
    <View style={styles.container}>
      {/* 顯示遠端圖片 */}
      <Image
        source={{ uri: 'https://reactnative.dev/img/tiny_logo.png' }}
      />
      {/* 顯示本地圖片 */}
      <Image
        source={Logo}
      />
    </View>
  );
}
```

## 簡易樣式套用範例

在 react native 中樣式可以寫在 StyleSheet 物件內，物件內的屬性就是 class 名稱，值是 class 內容。
在元件上可以用 style={styles.container} 的方式套用。

```js
import { StyleSheet, Text, View } from 'react-native'

const Home = () => {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>The Number 1</Text>
      <Text style={{
        marginTop: 10,
        marginBottom: 30,
      }}>
        Reading list app
      </Text>
      <View style={styles.card}>
        <Text>Hello this is a card</Text>
      </View>
    </View>
  )
}

export default Home;

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
  },
  title: {
    fontWeight: 'bold',
    fontSize: 18,
  },
  card: {
    backgroundColor: '#eee',
    padding: 20,
    borderRadius: 5,
    boxShadow: '4px 4px rgba(0, 0, 0, .5)',
  }
})
```

如果有除了 class 以外的樣式要加入，可以轉為陣列後再加入新的物件。

```js
<Text style={[styles.title, { color: 'purple' }]}>
  The Number 1
</Text>
```