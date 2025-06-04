---
title: 強化登入體驗與 JWT 驗證流程
date: 2024-07-24
authors: [rich]
tags: [authentication, jwt, token, login]
---

我們這次進行了一連串與登入與授權機制相關的更新，將 fyro.ai 的使用者體驗推向更完整的安全模型。

---

#### ✅ 實作 JWT 驗證流程

我們整合了 JWT（JSON Web Token）技術，實作包含：

- Token 發行與簽章
- JWT 驗證 API
- Token 過期自動刷新
- 支援 ElasticSearch 驗證用戶

每當使用者登入後，系統會產生 JWT 與 Refresh Token，儲存在 localStorage，並於過期時自動重新取得新的 access token。

---

#### 🔐 登入流程改善

建立了獨立的登入畫面，設計風格現代，支援多種登入選項預留（如 Google、Apple ID、Azure AD）。登入成功後會將 Token 寫入 localStorage 並進行導頁，未登入或 Token 無效時則會導向 login 頁面，確保使用者狀態一致。

---

#### 🛡️ Refresh Token 管理

登入時我們會自動：

- 建立新的 RefreshToken
- 記錄過期時間（預設七天）
- 儲存至 ElasticSearch `users` index

並在前端加入自動刷新邏輯，當 Access Token 過期時會自動呼叫 `/Auth/RefreshToken` 重新取得 Token，而不需中斷使用者操作。

---

#### 🔄 SignalR 鎖定與同步持續進化

這次也同步調整了前端鎖定邏輯，後續將再與 JWT 整合做更完整的使用者識別與追蹤控制。

---

這些機制的加入，使得整體登入驗證流程不但更符合業界安全標準，也讓使用者操作更加順暢而不中斷。未來我們也會持續強化跨瀏覽器與多工同步的能力，讓 fyro.ai 更加穩定可靠。
