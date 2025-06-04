---
title: FormDesigner Block 元件點擊加入功能
date: 2024-08-23
authors: [rich]
---

這次的更新為 fyro.ai 的表單設計工具加入了一個非常實用的互動功能 —— 使用者可以直接點擊畫面中的「區塊 Block」，即時在該區塊內插入一個新的元件。

---

### ✅ 功能概覽

過去元件的加入僅限於整體結構邏輯中，使用者必須額外挑選插入位置。本次更新讓互動更直覺，只要**點擊任一 Block**，即可插入預設元件（目前為 `TextBox`），省去額外操作。

---

### 🔧 技術重點

1. **前端 Block 元件新增 `@onclick` 處理函式**
   - 每個區塊都能接收點擊事件，並傳回自身 `Id`
   - 呼叫 Blazor `EventCallback<string>` 將 ID 傳遞給父元件

2. **Section.razor 接收事件並組裝 API 請求**
   - 包含目前元件 ID、新增元件 JSON 字串、整份表單結構
   - 呼叫後端 `/FormDesigner/InsertIntoBlock` API，進行 JSON 插入

3. **後端 API 插入邏輯**
   - 找到 `CurrentComponentId` 對應的 Block
   - 反序列化 `ComponentToInsertJson` 並加進其 Controls 中
   - 回傳更新後的 JSON 結構，直接更新 UI

---

### 🧪 實作範例

```json
{
  "SectionStructureJson": "...",
  "CurrentComponentId": "block-1234",
  "ComponentToInsertJson": "{ \"Id\": \"new-id\", \"Name\": \"newTextBox\" ... }"
}
```

這使得元件的操作邏輯與呈現結構更加緊密，未來也能改成插入使用者挑選的元件類型。

---

### 🌱 下一步

接下來可以朝下列方向擴展：

- 元件類型選擇視覺化（彈出小視窗）
- 拖曳排序 / 拖曳插入
- 插入後自動 focus 或編輯名稱

這樣的互動，會讓非工程背景的使用者更容易理解與操作畫面邏輯。

---

fyro.ai 讓複雜的表單設計變得直覺、快速，而且一致。
