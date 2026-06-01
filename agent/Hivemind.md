---
title: Hivemind
type: 工具卡
topics:
  - agent
  - token優化
status: 待驗證
difficulty: 進階
created: 2026-06-02
source: https://github.com/activeloopai/hivemind
---

> [!summary] TL;DR
> AI coding agent 的**共享記憶系統**：把每次 session 的成功操作路徑自動錄下來、分析出重複模式、codify 成 `SKILL.md`，讓下一個 session（甚至整個團隊）直接載入這些「沉澱的能力」——不用每次重新教。實測省 25% 成本、token 少 1.7 倍、對話輪次少 31%。

## 是什麼 (What)

Hivemind 是 Activeloop 開源的 Agent 記憶框架，核心概念是「**讓 AI 越用越聰明**」，靠四個環節閉環：

```
捕捉 → 編碼 → 傳播 → 複利
```

1. **捕捉 (Capture)**：每次 agent 交互（prompt、工具呼叫、回應）都被記錄成結構化 trace，存進 Deeplake。
2. **編碼 (Codify)**：背景 worker 定期（預設每 20 輪）挖掘 trace 裡的重複模式，用 Claude Haiku 判斷是否值得留，自動生成 `SKILL.md`。
3. **傳播 (Propagate)**：生成的 skill 自動注入每個連接的 agent context，跨 session 與跨團隊共享。
4. **複利 (Compound)**：每個 agent 都站在所有過去的成功經驗上作業。

> [!note] LoCoMo 基準驗證
> 公開長上下文記憶基準（100 個 QA 對），Hivemind 實測：
> - 成本降低 **25%**
> - Token 減少 **1.7 倍**（每題）
> - 對話輪次減少 **31%**
> 原因：已學會的操作直接載入 context，不用每次從零推導。

## 何時用 (When)

- ✅ 適合：
  - 重度使用 Claude Code / Cursor，每次都要重新解釋同樣的東西
  - 團隊共用 agent，想讓好的操作方式自動傳播
  - 想把「token 吃掉」的重複探索過程省掉
- ❌ 不適合：
  - 一次性任務（沒有重複使用的記憶紅利）
  - 不想資料離開本機（Hivemind 預設用 Deeplake cloud，BYOC 選項需另設）

## 怎麼做 (How)

```bash
npm install -g @deeplake/hivemind && hivemind install
```

安裝後 Claude Code 裡會多出：
- `/hivemind:login` — 登入帳號
- `/hivemind:capture` — 手動觸發記憶捕捉

技能自動注入，無需手動管理。

**支援的 agent**：Claude Code、Codex、Cursor、Hermes Agent、OpenClaw、pi

## Trade-offs

- ✅ 越用越省（複利效應）
- ✅ 跨 session / 跨團隊共享知識，不用靠個人記憶
- ✅ Apache 2.0，免費開源
- ❌ 資料預設存 Deeplake cloud（BYOC 需設定 GCS/Azure/S3）
- ❌ 星數少（366★），社群相對小
- ❌ 要先累積足夠 trace 才有效果（cold start 無紅利）

## 我的實測

（還沒實測，跑過再回來補）
- 安裝體驗：
- 第一個自動生成的 SKILL.md 是什麼：
- Token 省下來多少：

## 相關

- [[Claude Skills]] ← Hivemind 自動生成的 `SKILL.md` 就是這個格式
- [[axton-obsidian-visual-skills]] ← 另一個 skill 應用
- [[MOC-Agent模式]]
- [[MOC-Token優化]]

## 來源

- [activeloopai/hivemind - GitHub](https://github.com/activeloopai/hivemind)
