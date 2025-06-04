---
title: 表單驗證 API、Syncfusion 簽名元件，以及 Chat 表單改版
date: 2025-01-15
authors: [rich]
tags: [fyro, 表單驗證, Chat, Syncfusion, 產品更新]
---

新的一年開始，我們針對 fyro.ai 的表單功能做了三大升級：

---

## ✅ 1. Validator 結構自動產生

現在 fyro.ai 支援將表單 JSON 結構直接轉換成前端使用的 **Validator JS 格式**，你可以：

- 將欄位的 Required 自動轉為 `presence: true`
- 透過 `/Converter/ConvertJsonToValidateJS` 這個 API 一鍵轉換
- 搭配 UI 工具即時編輯、產出驗證邏輯

> 非常適合與前端框架（如 Vue、React）進行整合！

---

## ✍️ 2. 加入 Syncfusion 的 Signature 元件

我們新增了一個互動式「簽名欄位」，使用者可直接在畫面上簽名，並有顏色選擇器：

- 使用 `Syncfusion.Blazor.Inputs` 的 `SfSignature`
- 除了畫面操作，元件屬性也支援讀寫狀態（readonly）
- 已整合進 fyro 的 JSON 結構，與其他欄位一致

---

## 💬 3. Chat 表單與資料同步

fyro.ai 的表單搭配右側 Chat 模組時，現在會自動依據 `FormId` 帶入 RoomId，這讓聊天紀錄可以與某張表單綁定，不再只是孤立對話！

---

以上這些更新，是為了讓表單使用更靈活，驗證更清晰，互動更自然。未來我們也會持續將這些技術擴展到外部應用整合與更多表單類型的支援，敬請期待！
