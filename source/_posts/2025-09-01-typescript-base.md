---
title: Typescript (1) 基本介紹與安裝
date: 2025-09-01 13:51:17
categories: Typescript
description: "Typescript 基本介紹"
---

## 什麼是 TypeScript？

TypeScript（TS）是 JavaScript 的「型別化超集」：它在 JS 的語法上加入了靜態型別系統與開發期工具，最後會編譯transpile）成純 JavaScript 在任何支援 JS 的環境。

- 靜態型別檢查
在編譯階段就能發現錯誤，而不是等到執行才報錯。

- 更好的自動完成與提示
IDE（如 VS Code）能根據型別提供更完整的智能提示。

- 可維護性
對於大型專案，型別標註能讓程式碼更清晰，減少 bug。

- 兼容性
可以使用現代 JavaScript 特性，編譯後輸出支援舊版瀏覽器的 JS。

## 安裝

在電腦上用 npm 安裝全域 typescript

```
npm install -g typescript
```

開一個新的資料夾，並新增 index.ts 檔案

```ts
// index.ts
let age = 30;
console.log(age);
```

寫完 ts 的程式碼後，在終端機輸入 tsc index.ts 可以將 index.ts 編譯成 index.js

## 建立 tsconfig.json

tsconfig.json 可以設定 ts 編譯方式，建立方式

```
tsc --init
```

- 常見設定項目：

``` json
{
  "compilerOptions": {
    "target": "ES2020",       // 編譯輸出的 JS 版本
    "module": "CommonJS",     // 模組系統 (Node 常用 CommonJS，前端常用 ESNext)
    "strict": true,           // 開啟嚴格模式
    "esModuleInterop": true,  // 允許匯入 CommonJS 模組
    "skipLibCheck": true,     // 跳過型別檢查 .d.ts，讓編譯更快
    "outDir": "./dist",       // 編譯後輸出目錄
    "rootDir": "./src"        // 原始碼根目錄
  }
}
```

建立好 tsconfig 檔後，可以調整專案結構如下

```
- src
  - index.ts
- dist
tsconfig.json
```

因為在 tsconfig 中有設定 "rootDir" 跟 "outDir" ，所以 src 資料夾內的 ts 被編譯後會自動輸出到 dist 資料夾。

- 自動編譯

```
tsc --watch
```

指令後方加入 --watch ，會開啟自動編譯功能，當 ts 檔案有更新就自動編譯。











