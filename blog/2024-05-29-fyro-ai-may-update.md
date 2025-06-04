---
slug: may-update
title: fyro.ai 五月開發亮點：從靜態表單，到動態畫面自動生成
authors: [rich]
date: 2024-05-29
tags: [產品更新, 表單工具, fyro]
---

在這個月，我們替 fyro.ai 打下了非常重要的基礎：  
**讓表單和畫面的產生，從「人工撰寫」進化成「自動組合」。**

---

## ✨ fyro.ai 是什麼？

如果你還不熟悉 fyro.ai，它是一個讓開發者快速產出系統畫面的工具，  
你只需要定義一份 JSON，就能在 WebView 或 iframe 中嵌入你要的互動表單、畫面組件，  
並支援資料庫儲存、API 呼叫、MQTT 傳送等邏輯整合。

---

## 🚀 我們在五月完成了什麼？

### 🧱 建立可重用的畫面組件

我們花了不少時間把常見的畫面元素做成「元件」：

- ✅ 單行輸入欄位（Textbox）
- ✅ 多行文字（Textarea）
- ✅ 下拉選單（Select）
- ✅ 核取方塊（Checkbox）
- ✅ 單選選項（Radio）
- ✅ 純文字說明（Text）
- ✅ 表單區塊容器（Block）

這些元件支援樣式設定、事件觸發、綁定輸入值，並整合成統一的輸入模型（Input）。

---

### 🔄 JSON 設計語法完成

我們設計了一份簡潔的 JSON Schema，能描述整個畫面的排版與邏輯：

```json
{
  "Section": {
    "Title": "會員註冊",
    "Content": [
      {
        "block": {
          "start": 1,
          "span": 6,
          "controls": [
            {
              "type": "input.textbox",
              "name": "email",
              "labelText": "Email"
            }
          ]
        }
      }
    ]
  }
}
