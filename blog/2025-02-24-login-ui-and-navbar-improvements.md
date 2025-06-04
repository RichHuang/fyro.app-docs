---
title: 登入頁面樣式與 App 導覽列優化
date: 2025-02-24
authors: [rich]
tags: [fyro, eForm2App, LoginUI, Tailwind, Navbar]
---

本週的更新重點放在「登入體驗」與「App 導覽結構」的優化，讓 fyro 的前端互動介面更貼近日常使用者的需求。

---

## 🎨 登入頁面樣式強化

我們替 Login.razor 頁面導入了完整的 Tailwind CSS 自訂樣式：

- 支援 **RWD 響應式設計**，在小螢幕與桌面都能一致呈現
- 使用者登入畫面風格現代簡潔，並加上第三方登入按鈕樣式（Google / Apple / Azure AD）
- 修改背景與 padding 設定，使樣式更貼合實際 App 頁面

這些改動不只強化視覺一致性，也為未來登入行為自動化與測試鋪路。

---

## 🧭 新版 App 導覽列與底部導覽

我們同步完成了 eForm2App 的導航列設計：

- 建立底部固定導覽列（Footer Navigation）
- 五個主要分頁：首頁、我的珍藏、購物車、搜尋、會員專區
- 搭配 SVG 圖示與文字說明，符合 App 常見 UI 慣例

讓 fyro 的行動端操作體驗更直覺、易用。

---

## 🧱 eForm2Common 專案建立

為了整合登入與使用者模型邏輯，我們新建了 `eForm2Common` 專案，統一放置：

- UserLoginModel 等常用模型
- 共用的元件與介面依賴，減少跨專案重複定義

這樣一來，不論是在 Server、App 或 API 都能共享一致的登入資料結構。

---

這些更新代表 fyro 正一步步從「開發者工具」走向「產品級使用者體驗」，朝跨平台與視覺一致性邁進！
