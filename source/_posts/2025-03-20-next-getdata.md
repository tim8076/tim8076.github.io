---
title:  NextJs (10) 取得遠端資料
date: 2025-03-20 16:14:52
categories: NextJs
tags: NextJs
description: "Next中取得遠端資料"
---

## SSR 元件 (Server-Side Rendering)

*是指在伺服器上預先處理並生成 HTML，然後將完整的 HTML 發送到用戶端。
在 ssr 元件中取得遠端資料方法

```js
const { API, API_PATH } = process.env;
export default async function Products() {
  const res = await fetch(`${API}/v2/api/${API_PATH}/products/all`);
  const json = await res.json();
  const data = json.products;
  return (
    <>
      <div>
        產品列表
      </div>
      { data.map(product => {
        return (
          <div key={product.id}>
            <Link href={`/products/${product.id}`}>
              { product.title }
            </Link>
          </div>
        )
      })}
    </>   
  )
}
```


