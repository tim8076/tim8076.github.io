---
title: React (9) 專案資料夾分類
date: 2024-12-25 16:37:22
categories: React
tags: React
description: '介紹 React 專案資料夾分類方法'
---

在 React 專案中，清晰且有組織地管理資料夾有助於提高可維護性和開發效率。以下是一些常見且推薦的資料夾結構：

```
src/
├── assets/            # 靜態資源，如圖片、音檔、css
├── components/        # 可重用的元件
├── pages/             # 頁面元件，通常與路由對應
├── hooks/             # 自定義的 React Hooks
├── contexts/          # React Context API 的資料夾
├── utils/             # 工具函數或輔助功能
├── services/          # API 請求或與後端交互的代碼
├── constants/         # 全域常量，如配置、選項等
├── store/             # 狀態管理 (如果使用 Redux 或其他狀態管理工具)
├── tests/             # 測試檔案（也可放在各自的模組中）
├── App.js             # 主應用入口元件
├── index.js           # 應用程序的入口
```