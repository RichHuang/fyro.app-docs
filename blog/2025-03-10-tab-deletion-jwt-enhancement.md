---
title: 表單頁籤刪除功能與權控強化
date: 2025-03-10
authors: [rich]
tags: [fyro, jwt, 權限控管, 表單編輯, eForm2]
---

這週針對 fyro.ai 的 eForm2 表單平台進行多項優化，重點包括登入 Token 權限機制的強化、各表單元件整合 JWT，以及頁籤與區段刪除功能的加入，全面提升使用者體驗與開發彈性。

---

## 🔐 JWT 權控機制全面導入元件

- 每個表單元件（如 Textbox, Checkbox, Radio）皆新增支援 `JwtSecurityToken` 的參數
- 當使用者載入表單頁面時，系統會自動從 `localStorage` 讀取 Token 並解析，提取：
  - `sub`（使用者 ID）
  - `role`（例如 admin, user）
  - `group`, `jobRole` 等自定義欄位

這些資訊可用來在元件內判斷是否顯示、是否可編輯等，讓欄位行為更彈性。

---

## 🗂️ 加入頁籤與刪除頁籤功能

- 在 Form 設計畫面中，每個 Tab 現在支援「刪除」與「新增」操作按鈕
- 權限驗證為 `form-editor` 才能進行操作
- 所有操作皆即時同步後端 schema，保持資料一致性

---

## 🧱 區段也能刪除了

- 各 section 加入刪除按鈕（需具備 `form-editor` 權限）
- 使用者介面透過浮動按鈕方式呈現，避免誤操作
- 刪除時同步移除前端記憶體中的 sectionRefs 映射

---

## 💡 小更新補充

- 修正 Copy 貼上元件時 ID 重複的問題，透過遞迴重新產生新 ID
- Textbox 元件微調邊界樣式
- 更新 Token 權控設計文件，明確說明 `localStorage` 的存取流程與 JWT Payload 結構

---

這次更新讓 fyro 的表單編輯流程更加穩定、安全，也更貼近實際應用時的權限與角色控制需求。
