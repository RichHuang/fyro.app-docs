---
title: AI 輔助輸入上線！讓表單填寫更輕鬆自然
date: 2025-01-17
authors: [rich]
tags: [fyro, AI 輔助, 表單輸入, 使用者體驗, GPT]
---

我們在 fyro.ai 表單系統中正式導入 **AI 輔助輸入功能**，協助使用者以更自然的方式填寫表單欄位！

---

## 🧠 AIInput 輔助模式

每個欄位現在都支援一個 **AI 建議值 (AIValue)**：

- 透過 ChatGPT 分析整體上下文或圖片內容，推薦最合適的填寫值
- 系統會以視覺動畫高亮顯示推薦值（如 animate-glow）
- 使用者可以一鍵「✔ 套用」或「✘ 取消」

適用元件包含：Textbox、Textarea、Select、Checkbox、Radio 等各種欄位。

---

## ✨ AI 建議疊層 (Overlay) UI

當滑鼠移入時，若該欄位有 AI 建議值：

- 會浮現一層比較框：顯示目前值 vs. AI 推薦值
- 提供兩個圖示按鈕：✅ 套用建議 / ❌ 忽略建議

這個設計讓使用者「保持掌控」同時獲得 AI 幫助，使用上直覺也不會干擾原本流程。

---

## 🖼️ 支援圖片辨識

如果你的表單來源是一張圖片，例如收據、名片或手寫表單：

- 使用者只要貼上圖片，AI 就會根據內容自動分析，填寫相應欄位
- 所有建議都會以 AIValue 呈現，仍由使用者確認是否採用

> 我們整合了 GPT-4o 的圖片理解能力，讓 fyro.ai 更聰明、更貼心！

---

## 🔧 技術亮點

- 使用 `AIInputComponentBase` 作為元件基類
- 引入 `AIInputResultOverlay.razor` 做為通用疊層元件
- 可微調 AI 行為與 UX 展現，例如滑鼠延遲取消、淡入動畫、建議訊息…

---

這不只是一個「智慧欄位」，而是我們邁向 **智慧表單平台** 的重要一步！

未來也會支援語音輸入、多欄位聯想填寫與自動錯誤修正。🎯

