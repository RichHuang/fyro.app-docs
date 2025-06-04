---
title: 強化表單資料的結構與安全性：Metadata 儲存與型別還原
authors: [rich]
date: 2024-07-16
---

在持續開發 fyro.ai 的表單模組時，這一階段我聚焦在「資料結構的彈性」與「還原資料時的型別一致性」上，進行了一系列架構調整與修正。

## 📌 Metadata 儲存與還原

使用者填寫表單的過程中，除了內容本身，很多額外資訊也具有價值，例如：

- **建立時間**（CreateTime）
- **最後修改時間**（ModifiedTime）
- **儲存時間**（DocumentTime）

我在 Section 開頭加入一個 `MetadataModel` 控制項，它是一個隱藏欄位，儲存這些系統資訊。每次存檔前，ModifiedTime 會更新為目前時間，方便後續分析與查詢。

## 🧩 還原時型別一致性的挑戰

儲存時，我們用 `Dictionary<string, Input>` 的方式 serialize 各欄位。但在還原時，如果每個欄位都只是 Input 的 base class，就無法使用像是 `CheckboxModel.IsChecked` 或 `RadioModel.Options` 等屬性。

為了解決這個問題，我實作了一個 `InputJsonConverter`，在反序列化時依據 `Type` 屬性動態還原正確的子類別，確保像 `CheckboxModel`, `RadioModel`, `TextBoxModel` 等都能準確復原。

```csharp
switch (type)
{
    case "input.radio": input = new RadioModel(); break;
    case "input.checkbox": input = new CheckboxModel(); break;
    ...
}
