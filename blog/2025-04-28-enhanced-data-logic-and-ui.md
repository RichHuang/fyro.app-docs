---
title: 使用體驗再升級！自動欄位、自動跳過提醒、更清爽的表單
date: 2025-04-28
authors: [rich]
tags: [fyro, 表單優化, UI改進, metadata, 體驗設計]
---

在這一波更新中，我們針對資料結構、表單載入邏輯，以及使用者體驗進行了一系列細節調整，讓整個 fyro 使用流程更自然、更省心。

---

## 🧠 metadata 自動補齊，設計表單更直覺

每筆資料現在會根據 DataKey 自動生成 metadata：

- `metadata_DataKey1` 到 `metadata_DataKey3` 自動拆解 DataKey 結構
- 自動填入 Store 與 Department
- 自動附上建立時間 `metadata_CreateTime`

你再也不需要手動輸入這些欄位，系統會幫你處理好，讓搜尋與彙整更容易！

---

## 🧩 搜尋體驗：支援 Elasticsearch 與 MongoDB

不管你的資料儲存在哪裡，搜尋邏輯都一致：

- 支援 term / range / bool 等多種查詢條件
- keyword 欄位自動轉換
- bool 查詢 now 支援 must, must_not, filter 三種方式

---

## ✅ 自動判斷資料來源，不再多問一次

當你打開一張表單，若該資料已經存在，就不會再跳出「是否要帶入整合資料」的提示。這讓整個填寫流程更加流暢，不再被重複詢問打斷。

---

## 🧼 Select 元件去除多餘邊界，介面更簡潔

我們移除了 Select 欄位左側的固定空白，讓整體表單在行動裝置上也更對齊、更好看！

---

## 🍪 Token 儲存更聰明

登入後的 cookies 現在會自動設定為 7 天有效期，不用每次重新登入，也能保持適當的安全性。

---

這些看起來像是小改動，卻大大提升了設計者與填寫者的體驗。fyro 持續在細節處打磨，只為了讓你「做得少，用得多」。

