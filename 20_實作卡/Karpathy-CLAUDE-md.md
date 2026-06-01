---
title: Karpathy 版 CLAUDE.md — 四條行為準則
type: 實作卡
topics:
  - prompt工程
  - agent
status: 待驗證
difficulty: 入門
created: 2026-06-02
source: https://github.com/forrestchang/andrej-karpathy-skills
---

> [!summary] TL;DR
> 依 Andrej Karpathy 對 LLM 寫程式常見失誤的觀察，整理成一份單一 `CLAUDE.md`（四條行為準則），放進專案根目錄即可改善 Claude Code 的寫程式行為。不用裝套件，複製貼上就能用。GitHub 爆紅（165k★）。

## 是什麼 (What)

Forrest Chang（multica-ai 組織）根據 Karpathy 的觀察，把「LLM 寫程式最常出錯的模式」提煉成四條可以直接寫進 `CLAUDE.md` 的行為準則。

> [!note] 為什麼是 Karpathy？
> Andrej Karpathy 是 OpenAI 共同創辦人之一，現加入 Anthropic。他對 LLM 寫程式行為的觀察（假設太快、改太多、目標不明確）具有代表性。這份 CLAUDE.md 把這些觀察轉成 AI 可執行的指令。

### 四條準則

> [!check] 1. Think Before Coding（先想清楚再動手）
> 不要假設、不要隱瞞困惑。明確陳述假設，呈現多種解釋，不確定時**要求澄清**，不要自己猜然後動手。

> [!check] 2. Simplicity First（最小解法優先）
> 用最少的改動解決問題，避免過度工程化，禁止「順手」加進沒被要求的功能。

> [!check] 3. Surgical Changes（精準修改）
> 只改必要的部分，只清理**自己製造的**混亂，不要因為看不順眼就重構旁邊的東西。

> [!check] 4. Goal-Driven Execution（目標驅動執行）
> 把任務轉成**可驗證的目標**，定義成功標準，每次迭代都驗證是否達標。

## 何時用 (When)

- ✅ 適合：
  - 用 Claude Code 做正式專案（防止 AI 亂改、過度假設）
  - 任何有 `CLAUDE.md` 機制的專案根目錄
  - 不想每次都在 prompt 重複說「不要過度工程化」
- ❌ 不適合：
  - 快速一次性的探索（規則反而卡流程）

## 怎麼做 (How)

**方法 A：直接複製 CLAUDE.md（最快）**

```bash
# 下載 CLAUDE.md 到你的專案根目錄
curl -O https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md
```

**方法 B：Claude Code Plugin Marketplace**

```
/plugin marketplace add forrestchang/andrej-karpathy-skills
```

放好之後，Claude Code 每次在這個目錄啟動，都會自動讀進這四條準則。

> [!example] 可以自己改
> CLAUDE.md 就是純文字，可以直接在上面追加你自己的規則（例如：「用繁體中文回應」「不要寫任何測試檔案」）。四條是基礎，不是上限。

## Trade-offs

- ✅ 零成本：複製一個文字檔就能用
- ✅ 改善的問題很具體（過度假設、改太多、目標不清）
- ✅ 可自訂：直接在文件上追加規則
- ❌ 每個專案都要手動放（或用 plugin 全域安裝）
- ❌ 並不是萬靈丹：Claude Code 偶爾還是會「犯規」，要搭配實際使用觀察

## 我的實測

（還沒實測，跑過再回來補）
- 感受最明顯的是哪條準則：
- 有沒有加自己的規則：
- 對輸出品質的影響：

## 相關

- [[Claude Skills]] ← CLAUDE.md 本身就是一種 skill 設定
- [[MOC-Prompt工程]]
- [[MOC-Agent模式]]

## 來源

- [forrestchang/andrej-karpathy-skills - GitHub](https://github.com/forrestchang/andrej-karpathy-skills)（org 版：multica-ai/andrej-karpathy-skills）
