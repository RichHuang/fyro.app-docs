---
title: Chat 與 Form 的整合：真正會「對話」的表單體驗
date: 2025-02-17
authors: [rich]
tags: [fyro, ChatForm, iframe, AI互動, 表單整合]
---

這次 fyro.ai 團隊完成了一項重要的整合更新 —— **讓 Chat 與 Form 真正「會對話」！**

---

## 🤝 表單與 Chat 同步互動

我們打造了全新的 `/ChatForm/{FormId}/{DataKey}` 介面，左側是填寫中的表單，右側是 AI 聊天視窗，透過 iframe 雙向溝通，實現：

- 🔄 Chat 可以取得目前表單中填寫的資料
- 🧠 ChatBot 回應可以根據內容更加精準、上下文更完整
- 👀 開發者不用額外串接即可享有這種跨模組的體驗

---

## 🔌 技術亮點

- 利用 `window.postMessage` 進行 **跨 iframe 資料交換**
- 增加 `/FormForChatForm` 與 `/ChatForChatForm` 雙頁支援不同渲染邏輯
- Form 傳遞 section input model 給 Chat
- Chat 可向 parent 要求 sections 欄位值

---

## 🧪 開發者福利

只要在你的頁面中嵌入：

```html
<iframe src="/ChatForm/{FormId}/{DataKey}" />
```

就能直接享受一頁式的互動式填寫與 AI 輔助，不需額外串接 Chat API 或寫前端橋接邏輯。

---

這樣的設計讓 fyro.ai 更接近「智慧化互動表單平台」，幫助使用者邊寫邊問，邊問邊修，節省溝通與反覆修改的成本。
