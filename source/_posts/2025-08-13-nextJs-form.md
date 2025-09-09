---
title: NextJs (17) Form 元件
date: 2025-08-13 11:38:13
categories: NextJs
tags: NextJs
description: "Next 中使用 Form 元件"
---



`<Form>` 元件是在 HTML `<Form>` 基礎上的延伸，提供 載入 UI 的預取（prefetching）、表單提交時的 客戶端導覽（client-side navigation），以及 漸進式增強（progressive enhancement） 的能力。
解釋：
使用`<Form>` 可以讓表單提交時更順暢：會提前加載相關 UI（例如 layout 或 loading），避免頁面整體跳轉，也能保留部分共用視圖與狀態。

## 基本用法範例

```js
import Form from 'next/form'

export default function Page() {
  return (
    <Form action="/search">
      {/* 提交後，輸入值會被附加至 URL，例如 /search?query=abc */}
      <input name="query" />
      <button type="submit">Submit</button>
    </Form>
  )
}
```

這段程式碼說明了當你使用 `<Form action="/search">` 時，表單輸入會以 GET 參數附加到 URL 上，並進行客戶端導覽。

## 主要參數與行為差異

A. action 為字串（string）時
這是用來像原生表單那樣透過 GET 方法傳參，但具備 Next.js 的優化機制。

- 預取（prefetch）：當 `<Form>` 進入使用者視窗時，Next.js 會預先抓取相關 UI，例如 layout 或 loading 元件，加快後續導覽速度。
- 客戶端導覽：提交表單時不會重新載入整頁，而是維持客戶端狀態。


支援的 Props：

- action（字串）：提交目標 URL 或路徑，必填。
- replace（布林）：若為 true，會替換當前歷史紀錄，否則新增一筆。預設為 false。
- scroll（布林）：是否在跳轉後滾動到頂部，預設為 true。
- prefetch（布林）：是否預取，預設為 true。


B. action 為函式（function / Server Action）時
可用於處理表單提交但不更新 URL 的情況，類似 React 的 submit handler：

action={someServerAction}：提交表單時呼叫指定的 Server Action。
在這個模式下，replace 和 scroll 會被忽略。
