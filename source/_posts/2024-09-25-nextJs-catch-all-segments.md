---
title: NextJs (4) catch-all-segments 路由
date: 2024-09-25 14:18:00
categories: NextJs
tags: NextJs
description: "NextJs catch-all-segments 路由解說"
---

在 Next.js 中，"Catch all segments" 是一個路由模式，允許你捕獲 URL 中任意數量的路由參數。它可以處理路由中的動態段落，並且還能捕捉多個段落或剩餘的段落。這在構建動態頁面或 API 時非常有用。

## 基本用法

要實現 "Catch all segments" 的路由，你需要使用方括號 [] 包含三個點號 ...，例如：

```
pages/post/[...slug].js
```

這樣一來，任何匹配 /post/ 路徑的 URL 都會被捕捉到，並將 URL 的段落以陣列形式傳遞給頁面。

例子：
假設你有一個路徑 /post/[...slug].js，當你訪問 /post/hello/world 時，slug 會是一個包含 URL 剩餘部分的陣列：

```js
export default function Post({ params }) {
  return <div>Slug: {params.slug.join("/")}</div>;
}

export async function getStaticPaths() {
  return {
    paths: [{ params: { slug: ["hello", "world"] } }],
    fallback: false,
  };
}

export async function getStaticProps({ params }) {
  return {
    props: {
      params,
    },
  };
}
```

在這個例子中，如果你訪問 /post/hello/world，params.slug 會是一個 ['hello', 'world'] 的陣列。

## 可選的 "Catch all segments"

你也可以讓 "Catch all segments" 成為可選項，這樣如果 URL 中沒有匹配的部分，頁面仍然會被渲染。這可以通過方括號 [] 和 ... 的結合來實現：

```
pages/post/[[...slug]].js
```

在這個情況下，如果你訪問 /post，slug 會是 undefined。而如果你訪問 /post/hello/world，slug 會是 ['hello', 'world']。

```js
export default function Post({ params }) {
  const slug = params.slug ? params.slug.join("/") : "default";
  return <div>Slug: {slug}</div>;
}

export async function getStaticProps({ params }) {
  return {
    props: {
      params,
    },
  };
}
```
