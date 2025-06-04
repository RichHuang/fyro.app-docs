---
title: "eForm2 與 ZetaFrame 新功能簡介：更自由的表單操作體驗！"
date: 2025-05-15
authors: [rich]
---

## 🌟 讓表單自由嵌入！支援 iFrame 並加強安全性

ZetaFrame 現在可透過 `iframe` 嵌入 eForm2 表單頁面，只要在 `appsettings.json` 中設定 `eForm2.Url` 與 `eForm2Api.Url`，系統就能自動連接並取得表單結構，動態產生導覽選單，還能透過路由 `/form/{formId}` 嵌入指定表單，讓你可以自由整合不同系統或嵌入至其他平台使用。

> ✅ 同時支援設定 `AllowedIframeOrigins`，避免不明網域嵌入，強化嵌入安全性。

---

## 🧩 功能設定超細緻，自由控制 UI 行為

你可以透過 `FormSetting` 設定各種 UI 行為，依需求開關：

- `EnableSubmitButton`: 顯示或隱藏「送出」按鈕。
- `EnableDeleteButton`: 是否允許使用者刪除表單。
- `IsToolbarAtTop`: 底部工具列是否移至頂部。

另外在 `FormFrame`（iframe 表單主頁）也能控制：

- `EnableBackButton`: 顯示返回上一頁按鈕。
- `EnableFormSwitcher`: 開啟下拉選單切換其他表單。
- `EnableColumnsButton`: 控制顯示幾個子表單欄位。
- `EnablePrintMainFormButton`: 是否提供主表單列印功能。

這些細節都可以 per form 自訂，非常適合企業內部不同部門或使用情境彈性設定！

---

## 🚀 全新 submitForm 訊息監聽！支援跨窗控制送出

現在，只要在外部系統透過 JavaScript `postMessage` 傳送以下訊息：

```js
window.postMessage({ action: "submitForm" }, "*");
```

內嵌的表單頁面就會自動送出！無需使用者點擊按鈕，非常適合自動化流程、複合操作流程中使用。

---

## 🛠 開發者友善，介接簡單

在 ZetaFrame 的 `Program.cs` 裡已預設將 `ApiSecretKey` 設為 HTTP 標頭，無需手動每次設定；此外也透過 `.csproj` 引用共用的 `eForm2Lib` 和 `eForm2Common`，減少耦合與重複撰寫。

---

## 🧪 還有更多：

- UI 圖示加入動畫效果，例如 tab 被 AI 修改過時閃爍提醒。
- 提供每個 tab 編輯、刪除功能（限擁有 editor 權限的使用者）。
- 提供 json 檢視與 tab 新增／刪除功能（編輯模式限定）。

---

你還沒用過 eForm2 嗎？或許現在就是導入自動化表單的最佳時機！  
整合性強、擴充彈性高、開箱就能用。

---

如需更進階客製需求，歡迎聯絡我們！👨‍💻
