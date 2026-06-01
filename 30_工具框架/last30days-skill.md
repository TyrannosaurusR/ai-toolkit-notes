---
title: last30days-skill
type: 工具卡
topics:
  - agent
  - prompt工程
status: 待驗證
difficulty: 入門
created: 2026-06-01
source: https://github.com/mvanhorn/last30days-skill
---

> [!summary] TL;DR
> 一個 Claude Code **研究型 skill**：給它一個主題，它跨 Reddit、X、YouTube、Hacker News、Polymarket、GitHub 等平台抓「最近 30 天」大家在討論什麼，合成一份**附引用**的摘要簡報。專門賺「資訊差紅利」。

## 是什麼 (What)

mvanhorn 開源的 [[Claude Skills|skill]]，定位是「即時趨勢研究」：

- 跨 10+ 來源（Reddit / X / YouTube / HN / Polymarket / GitHub / Digg…）抓近 30 天討論
- v3 引擎會**先判斷該去哪些平台搜**，再開始搜
- 主題是「人」時切換成 author-scoped 查詢（這人最近 ship 了什麼、反應如何）
- 產出 chat 內摘要 + 一份 HTML brief 存到指定目錄
- 重點：**附真實引用**，不是空口摘要

2026/3 釋出後爆紅，單日 +2,800★。

## 何時用 (When)

- ✅ 適合：
  - 想快速掌握某主題 / 某人最近的真實討論與動態
  - 做內容、選題、市場觀察前的情報蒐集
  - 要「有出處」的摘要而非模型瞎掰
- ❌ 不適合：
  - 需要深度長期研究（這是「近 30 天」快照）
  - 冷門主題（各平台討論量不足時效果有限）

## 怎麼做 (How)

（待補實際安裝步驟——以官方 repo 為準）

- Repo：`mvanhorn/last30days-skill`（Claude Code marketplace 也找得到）
- 用法：裝進 skills 目錄後，直接叫 Claude「研究 X 最近 30 天」即可。

## Trade-offs

- ✅ 多平台一次掃，省下手動爬各站
- ✅ 附引用、可追溯
- ✅ 有 person-focused 模式
- ❌ 只看近 30 天，非長期深度
- ❌ 依賴各平台可抓性，冷門題材會稀疏

## 我的實測

（還沒實測，跑過再回來補）
- 測試主題：
- 來源覆蓋 / 引用品質：
- 和自己手動查的差距：

## 相關

- [[Claude Skills]] ← 母概念
- [[baoyu-skills]] ← 另一類 skill（內容創作）
- [[MOC-Agent模式]]

## 來源

- [mvanhorn/last30days-skill - GitHub](https://github.com/mvanhorn/last30days-skill)
- [介紹 reel - 一人公司研究所 (FB)](https://www.facebook.com/reel/2945926219071712)
