---
title: 表單設計器支援拖曳操作與更新元件屬性
date: 2024-12-12
authors: [rich]
tags: [產品更新, 表單設計, fyro, 拖曳互動]
---

我們在 fyro.ai 的表單設計器中加入了**拖曳編輯功能**，現在你可以直接拖動元件調整順序、插入新元件或更新屬性，畫面邏輯會即時反應，讓設計過程變得更像在排版。

---

## 🧲 拖曳元件操作：所見即所得

你可以：

- 拖動元件重新排序
- 將元件拖到其他區塊中
- 將新元件從工具列拉入畫面
- 每個元件支援 `@ondragstart` / `@ondrop`

這些行為背後都有搭配的 API 可處理：

| 操作 | API Route |
|------|-----------|
| 插入在前 | `/FormDesigner/InsertBefore` |
| 插入在後 | `/FormDesigner/InsertAfter` |
| 插入在最後 | `/FormDesigner/InsertAtEnd` |
| 移動元件 | `/FormDesigner/MoveAfter` |
| 插入到區塊中 | `/FormDesigner/InsertIntoBlock` |
| 置換元件 | `/FormDesigner/ReplaceComponent` |
| 刪除元件 | `/FormDesigner/DeleteComponent` |
| 更新元件屬性 | `/FormDesigner/UpdateComponentProperty` |

---

## ✨ 體驗提升細節

- 設計畫面在點選或滑鼠移動時會出現「紅色框線」或「虛線提示」
- 支援 iframe 當中的 iframe 點擊事件回傳（via `iFramePostMessageClick`）
- 調整後資料會即時送出到 SignalR，同步其他使用者視角

---

## 📌 技術備註

- `.razor.cs` 檔案中的元件都支援拖曳事件（用 `EventCallback<(DragEventArgs, FormPartModel)>`）
- 每個元件都自動注入拖曳事件到 DOM 中

---

這項更新讓 fyro.ai 的表單設計工具從「資料設計工具」躍升為「互動式畫面建構器」，只要動動滑鼠，就能把想法變成畫面 🎨

