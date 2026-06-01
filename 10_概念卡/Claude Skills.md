---
title: Claude Skills
type: 概念卡
topics:
  - agent
  - prompt工程
status: 待驗證
difficulty: 入門
created: 2026-06-01
source: https://www.anthropic.com/news/skills
---

> [!summary] TL;DR
> Skills 是把一段「重複的工作流程 / SOP」封裝成 **一個 markdown 檔（SKILL.md）**，讓 Claude 在需要時自動載入、照著做。等於幫 AI 養一批「客製化員工」，不用每次重打一長串 prompt。

## 是什麼 (What)

Agent Skills 是 Anthropic 官方機制：把你反覆在用的指令、步驟、範例、甚至附帶腳本，收進一個資料夾，核心是一份 `SKILL.md`。Claude 看到任務符合時，會自動把對應 skill 載進 context 來用。

- 幾乎不用寫程式——主體就是 markdown
- 可重用、可分享、可版本控制（放進 repo）
- 官方有 skill generator，約 30 分鐘能生一個
- 跨環境通用（Claude Code、Claude Desktop 等）

> [!note] 跟「寫一個好 prompt」差在哪
> 一次性 prompt 用完即丟；skill 是**沉澱下來的能力**——寫一次，之後每次自動套用，並且能跟團隊共享同一套標準。

## 何時用 (When)

- ✅ 適合：
  - 一個流程你已經重複下了很多次 prompt（簡報、圖卡、研究摘要、發文）
  - 想讓產出風格 / 格式**穩定一致**
  - 想把個人 / 團隊的 SOP 變成 AI 能直接執行的能力
- ❌ 不適合：
  - 一次性、不會再用的任務（直接下 prompt 就好）
  - 流程還沒定型、每次都在變

## 怎麼做 (How)

1. 找出你重複在做的流程（例：把文章轉成小紅書圖卡）。
2. 寫一份 `SKILL.md`：說明這個 skill 做什麼、何時觸發、步驟與範例（必要時附腳本 / 資源檔）。
3. 放進 skills 目錄 / repo，Claude 偵測到相符任務就自動載入。
4. 可直接拿現成的 skill 合輯來改（見下方相關卡）。

> [!example] 現成 skill 來源
> - [[baoyu-skills]]：20+ 個內容創作 / 發文 skills（漫畫、圖卡、資訊圖、簡報…）
> - [[last30days-skill]]：跨平台熱門議題研究 skill

## Trade-offs

- ✅ 重用 + 一致性：寫一次，之後自動套用
- ✅ 可分享 / 版本控制，團隊共用同一套標準
- ✅ 進入門檻低（markdown 為主）
- ❌ 要先「流程定型」才值得封裝
- ❌ skill 太多 / 描述不清，可能誤觸發或互相打架

## 我的實測

（還沒實測，跑過再回來補）
- 自建的第一個 skill：
- 觸發準不準：
- 比直接下 prompt 省多少事：

## 相關

- [[baoyu-skills]] ← 範例合輯：內容創作類
- [[last30days-skill]] ← 範例：研究摘要類
- [[MOC-Agent模式]]
- [[MOC-Prompt工程]]

## 來源

- [Claude Skills - Anthropic](https://www.anthropic.com/news/skills)
- [Skills 介紹 reel - @harryleemedia (IG)](https://www.instagram.com/reel/DXeaYN9COpf/)
