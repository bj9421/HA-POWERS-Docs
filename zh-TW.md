# HA-POWERS — 全棧開發管線

> **HA-POWERS** 靈感來自 [obra 的 Superpowers](https://github.com/obra/superpowers)。
>
> 🇹🇼 [English Version](README.md)
>
> **HA-POWERS = Hermes Agent Superpowers。**
> 從原始構想到合併 PR 的完整開發管線，專為 Hermes Agent 設計，但也適用於任何 AI 輔助的工作流程。

---

## 🚀 快速開始

在任何 Hermes 對話中輸入：

```
@skill:ha-powers
```

這會載入完整的 7 階段管線，附帶可見的進度追蹤器與引導式流程。

> **自動偵測模式：** 載入 skill 後，說「建構 X」或「實作一個功能」，Hermes 會自動決定要跑完整管線還是跳過到快速修復。

## 📦 安裝

HA-POWERS 以 **Hermes Agent skill** 形式提供。無需額外安裝 — 將 skill 放入 `skills/` 目錄即可使用。

> 🤖 **給 Agent 使用：** [下載 SKILL.md](SKILL.md) + [references/](references/) — 將**整個目錄**（`SKILL.md` + `references/`）複製到 `skills/software-development/ha-powers/` 目錄即可部署完整的 skill 定義。

### 前置條件

- 已安裝並運行 Hermes Agent
- 已連接至提供者（Anthropic、OpenRouter 等）

### 選配：Kanban 看板

如需跨會話的多功能追蹤，也載入 kanban skill：

```
@skill:kanban
```

## 📋 管線總覽

HA-POWERS 引導你完成 **7 個帶門控的階段**：

| 階段 | 做什麼 |
|------|--------|
| 1. 腦力激盪 | 撰寫規格書，獲得使用者核准 |
| 2. 撰寫計畫 | 拆解為 2–5 分鐘的小任務，附精確檔案路徑 |
| 3. Git Worktrees | 在 `feat/<name>` 建立隔離工作區 |
| 4. 子代理開發 | 開發者 + 選配審查者子代理（TDD） |
| 5. 程式碼審查 | 正確性、可維護性、安全性、效能 |
| 6. PR + CI | 推送、建立 PR、自動修復 CI、合併 |
| 7. 清理 | 移除 worktree，清理分支 |

**完整設計理念、進度追蹤器與架構圖，請參閱 [ARCHITECTURE.zh-TW.md](ARCHITECTURE.zh-TW.md)。**

## 🔧 使用時機

> **每個階段都是獨立工具。需要什麼就拿什麼，不需要就跳過。**

**完整管線（第 0–7 階段）— 用於大型、高風險工作：**
- 使用者說「建構一個 [功能/元件/應用程式]」
- 多步驟程式碼任務，涉及 >2 個檔案
- 任務涉及難以逆轉的架構決策
- 任務有測試影響
- 任何你想要 PR 軌跡的專案

**部分管線（第 0–2 階段，然後直接寫程式）：**
- 單一檔案變更，但有一些設計選擇
- 修改現有腳本（加 flag、重構函式）
- 自己會審查的任務（不需團隊 PR）
- 原型 / 驗證性實驗，可能用完就丟

**最小管線（僅第 0 階段，然後直接寫程式）：**
- 範圍明確但需要對齊 2-3 個細節（API 選擇、輸出格式）
- 使用者有偏好但需要幫忙在選項間做決定
- 快速 grill-me 會談（3-5 問題）後直接寫程式

**完全跳過管線（直接修復）：**
- 修復單行錯字
- 更改設定值
- 執行腳本
- 微不足道的重新命名 / 格式化
- 使用者明確說「直接做就好，不需要計畫」

## 📁 專案結構

```
project-root/
├── docs/
│   ├── specs/          # 第 1 階段輸出
│   └── plans/          # 第 2 階段輸出
├── .worktrees/
│   └── feat/           # 第 3 階段輸出
├── KANBAN.json         # 選配 Kanban 看板
└── src/                # 實作
```

## ⚡ 重點整理

1. **每個階段都有門控** — 必須通過才能進入下一個
2. **進度追蹤器始終可見** — 你永遠知道自己在哪裡
3. **Kanban 持久存在** — 跨會話追蹤所有功能
4. **Git 友好** — 所有輸出都是檔案，版本控制
5. **零相依性** — 純 Python stdlib，無需伺服器或資料庫
6. **工具箱而非組裝線** — 根據風險選擇合適的深度

---

> 💡 命名致敬 [obra 的 Superpowers](https://github.com/obra/superpowers) — 一切始於 progressive disclosure 模式。
> *為 Hermes Agent 打造 · MIT 授權 · 2026*
