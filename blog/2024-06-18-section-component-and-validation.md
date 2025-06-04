---
slug: june-update
title: 分離與驗證：讓每一段表單都更獨立也更可靠
date: 2024-06-18
authors: [rich]
tags: [產品更新, fyro, 表單驗證, 動態元件]
---

這幾週，我們替 fyro.ai 的表單系統做了幾個核心升級，讓它更模組化、更可靠，也更容易整合到現有的流程中。

---

## 🧩 Section 元件獨立化

原本所有欄位都是寫在一個大的畫面元件裡，這樣很難維護，也不利於重用。這次我們將 **每一段表單（Section）抽出成獨立元件**，用 JSON 描述內容，fyro 自動組成畫面。

這樣做有幾個好處：

- ✅ 每段表單可以重複使用
- ✅ 新增欄位不用動整頁程式
- ✅ 支援 iframe/webview 動態載入片段

---

## 📡 SignalR 同步穩定化

之前多使用者編輯同一份表單時，checkbox 常常不同步，這次我們：

- 對 checkbox 增加 `IsCheckedWithoutInvokeChange`
- 對一般欄位新增 `ValueWithoutInvokeChange`

這讓訊息同步更穩定，也不會產生重複事件。

---

## 🧪 HTML ➜ JSON ➜ 驗證，自動轉換！

fyro.ai 現在支援一件超方便的事：

> ✨ 只要貼上一段 HTML 表單，我們就能：
>
> - 轉成 fyro 格式的 JSON 表單
> - 抽出欄位驗證條件（required, type）轉成 validate.js 語法

這大幅減少從現有系統搬資料進 fyro 的難度，未來你甚至可以從 WordPress、Google Form 轉換過來。

---

## 🧹 刪掉早期測試檔案

把舊的測試用 Section1/2/3 都刪除了，現在 repo 更乾淨，只保留實際會用到的正式元件與頁面。

---

## 🗓 下一步

- 整合多段式流程表單（Wizard 模式）
- 支援條件邏輯：欄位顯示/隱藏/必填依據其他值
- 接 webhook/postMessage 擴充資料回寫能力

---

> fyro.ai 的目標是：讓**每個表單都可以像積木一樣拼出來，像函數一樣重複用**。

下一篇，我們會分享一個實際案例：「一份 PDF 同意書表單怎麼轉成 fyro 畫面 + 結果存進 ElasticSearch」。敬請期待！

