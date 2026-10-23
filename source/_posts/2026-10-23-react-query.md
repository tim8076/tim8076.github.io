---
title: React Query
date: 2026-10-23 14:40:13
tags: React Query 用法
description: "CReact Query教學"
---

## 什麼是 React Query

React Query（現已更名為 TanStack Query）是一個專門用來管理「伺服器狀態（Server State）」的 React Hook 函式庫。它能幫你自動處理 API 資料快取、背景更新、失敗重試、Loading/Error 狀態，大幅減少傳統使用 useEffect 搭配 useState 的冗長程式

## 安裝與環境設定

```
npm install @tanstack/react-query
```

假設你使用 React + Vite，在 main.jsx 使用 QueryClientProvider 包住整個應用程式。

```jsx
// main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import {
  QueryClient,
  QueryClientProvider,
} from '@tanstack/react-query'
import App from './App.jsx'

const queryClient = new QueryClient()

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <QueryClientProvider client={queryClient}>
      <App />
    </QueryClientProvider>
  </StrictMode>,
)
```

- QueryClient：管理快取、資料更新與查詢設定。
- QueryClientProvider：讓子元件可以使用 React Query 的 Hooks。

## useQuery：取得 API 資料

1. 先撰寫 API 函式

```js
// api/products.js
import axios from 'axios'
export async function getProducts() {
  const response = await axios.get(
    'https://fakestoreapi.com/products'
  )
  return response.data
}
```
2. 使用 useQuery
```jsx
// Products.jsx
import { useQuery } from '@tanstack/react-query'
import { getProducts } from './api/products'

function Products() {
  const {
    data,
    isPending,
    isError,
    error,
  } = useQuery({
    queryKey: ['products'],
    queryFn: getProducts,
  })
  if (isPending) return <p>載入中...</p>
  if (isError) {
    return <p>發生錯誤：{error.message}</p>
  }
  return (
    <ul>
      {data.map((product) => (
        <li key={product.id}>
          {product.title} - ${product.price}
        </li>
      ))}
    </ul>
  )
}
export default Products
```
- queryKey: 用來識別這份查詢資料，也會影響快取的存取與更新。
例如：商品列表使用 ['products']，單一商品則可使用 ['products', productId]。

- queryFn: 負責實際取得資料的非同步函式，必須回傳 Promise，成功時取得資料，失敗時應拋出錯誤。

- 常用回傳狀態: 
data:	API 回傳的資料
isPending:	目前沒有可用資料，查詢尚未完成
isError:	查詢發生錯誤
error:	錯誤資訊
isFetching:	目前正在執行請求，包含背景重新取得資料
refetch:	手動觸發重新查詢

- enabled: 用來控制 useQuery 是否可以自動執行查詢。

常見情境：取得 id 後才查詢

```jsx
import { useQuery } from '@tanstack/react-query'

function ProductDetail({ productId }) {
  const { data, isPending, isError } = useQuery({
    queryKey: ['product', productId],
    queryFn: () => getProduct(productId),
    enabled: !!productId,
  })
  if (!productId) return <p>尚未取得商品 ID</p>
  if (isPending) return <p>載入中...</p>
  if (isError) return <p>取得商品失敗</p>
  return <h1>{data.title}</h1>
}
```

## useMutation：新增、修改、刪除資料

```jsx
import {
  useMutation,
  useQueryClient,
} from '@tanstack/react-query'
import axios from 'axios'

function AddProduct() {
  const queryClient = useQueryClient()
  const mutation = useMutation({
    mutationFn: (newProduct) =>
      axios.post('/api/products', newProduct),
    onSuccess: () => {
      // 新增成功後，讓商品列表快取失效
      queryClient.invalidateQueries({
        queryKey: ['products'],
      })
    },
  })
  return (
    <button
      onClick={() =>
        mutation.mutate({
          title: '草莓蛋糕',
          price: 120,
        })
      }
      disabled={mutation.isPending}
    >
      {mutation.isPending ? '新增中...' : '新增商品'}
    </button>
  )
}
```

這裡最重要的是三個步驟：
- mutation.mutate(data)
執行新增、修改或刪除操作。
- onSuccess: 伺服器成功處理請求後執行。
- invalidateQueries: 將相關查詢標記為過期，讓正在使用該查詢的元件可以重新取得最新資料。
