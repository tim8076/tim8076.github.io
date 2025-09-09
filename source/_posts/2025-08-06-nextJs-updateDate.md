---
title: NextJs (12) 更新資料
date: 2025-08-06 11:25:18
categories: NextJs
tags: NextJs
description: "Next 更新資料"
---

## 更新資料

Next.js 鼓勵你搭配 Server Actions （即 React Server Functions）進行資料更新。你可以在 server component 中定義這些函式，然後從 client component 呼叫它們，以進行資料的新增、修改或刪除。

## 建立 Server Function

- 方法一: 另外開一個 action.js 檔案來管理 Server Actions。建立方法使用 Async Function 並在內部加上 'use server';

```js
// app/lib/actions.js
export async function createPost(formData) {
  'use server'
  const title = formData.get('title')
  const content = formData.get('content')
  // Update data
  // Revalidate cache
}
```

- 方法二: 直接在 Server Component 內加入 Server Function

```js
export default function Page() {
  // Server Action
  async function createPost(formData: FormData) {
    'use server'
  }
  return <></>
}
```

## 在 Client Component 內呼叫 Server Function

在 Client Component 中 通過 `<form action={myAction}>` 或 `<button onClick={...}>` 呼叫這個 server action。
更新資料後，由於 server component 會被重新執行，所以畫面會重新渲染最新資料。

```js
// app/ui/button.js
'use client'
import { createPost } from '@/app/actions'
export function Button() {
  return <button formAction={createPost}>Create</button>
}
```

也可將 Server Function 透過 props 傳入 Client Component

```html
<ClientComponent updateItemAction={updateItem} />
```

```js
'use client'
export default function ClientComponent({ updateItemAction }) {
  return <form action={updateItemAction}>{/* ... */}</form>
}
```

## 呼叫 Server Function

有兩種方式可以呼叫 Server Function。

- Form: 在 Server 或 Client Components 使用 Form

```js
import { createPost } from '@/app/actions'
 
export function Form() {
  return (
    <form action={createPost}>
      <input type="text" name="title" />
      <input type="text" name="content" />
      <button type="submit">Create</button>
    </form>
  )
}
```

- Event Handlers: 在 Client Components 內透過事件觸發

```js
'use client'
 
import { incrementLike } from './actions'
import { useState } from 'react'
export default function LikeButton({ initialLikes }) {
  const [likes, setLikes] = useState(initialLikes)
  return (
    <>
      <p>Total Likes: {likes}</p>
      <button
        onClick={async () => {
          const updatedLikes = await incrementLike()
          setLikes(updatedLikes)
        }}
      >
        Like
      </button>
    </>
  )
}
```

## Pending State

可以透過 useActionState 取得 Pending 狀態

```js
'use client'
 
import { useActionState, startTransition } from 'react'
import { createPost } from '@/app/actions'
import { LoadingSpinner } from '@/app/ui/loading-spinner'
export function Button() {
  const [state, action, pending] = useActionState(createPost, false)
  return (
    <button onClick={() => startTransition(action)}>
      {pending ? <LoadingSpinner /> : 'Create Post'}
    </button>
  )
}
```

## 錯誤捕捉

可以在 server function 裡回傳錯誤狀態

```js
export async function createProduct(preState, formData) {
  const title = formData.get('title');
  const price = formData.get('price');
  const description = formData.get('description');
  const errors = {};
  if (!title) {
    errors.title = 'title is required'
  }
  if (!price) {
    errors.price = 'price is required'
  }
  if (!description) {
    errors.description = 'description is required'
  }
  if (Object.keys(errors).length > 0) {
    return { errors }
  }

  await addProduct(title, parseInt(price), description);
  redirect('/products-db')
}
```

前端 useActionState 的 state 中取得 error

```js
const [state, formAction, isPending] = useActionState(createProduct, {});
return (
  <form action={formAction} className="p-4 space-y-4 max-w-96">
    <div>
      <label>
        Title
        <input
          type="text"
          className="block w-full p-2 text-black border rounded"
          name="title"
        />
      </label>
      { state.errors?.title &&
        <p className="text-red-500">{state.errors?.title}</p>}
    </div>
    <button
      type="submit"
      className="block w-full p-2 text-white bg-blue-500 rounded disabled:bg-gray-500"
      disabled={isPending}
    >
      Add Product
    </button>
  </form>
  );
```

## 畫面刷新

畫面何時會自動更新、何時不會

| 情境 | 資料會自動更新嗎？ | 說明 |
|------|------------------|------|
| ✅ Server Action + 使用 Server Component 顯示資料 | ✅ 會自動更新 | 提交表單後頁面會重新 render，資料自動更新 |
| ❌ Server Action + 使用 Client Component 顯示資料（透過 fetch） | ❌ 不會自動更新 | 你要手動呼叫 `router.refresh()` 或 `revalidatePath()` |
| ❌ Server Component 使用 fetch 且設有 cache（預設） | ❌ 不會自動更新 | 必須在 Server Action 裡手動 `revalidatePath()` 才會讓 Next.js 抓新資料 |
| ✅ 使用 `cache: 'no-store'` | ✅ 每次都抓新資料 | 但會失去快取效能，通常不推薦 |

revalidatePath 用法

```js
import { revalidatePath } from 'next/cache'
export async function createPost(formData) {
  'use server'
  // Update data
  // ...
  revalidatePath('/posts')
}
```
