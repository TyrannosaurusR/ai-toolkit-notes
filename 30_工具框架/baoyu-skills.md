---
title: baoyu-skills
type: 工具卡
topics:
  - agent
  - prompt工程
status: 待驗證
difficulty: 入門
created: 2026-06-01
source: https://github.com/JimLiu/baoyu-skills
---

> [!summary] TL;DR
> 寶玉（JimLiu）開源的 **Claude / Codex Skills 合輯**，20+ 個現成 skill，偏「內容創作與發布」——知識漫畫、小紅書圖卡、資訊圖、簡報、文章配圖、發文到 X/微信/微博 等。約 20k★，拿來即用或當寫 skill 的範本。

## 是什麼 (What)

一個 skill 合輯 repo，把常見的內容生產流程封裝成可重用 [[Claude Skills]]。主要分幾類：

- **視覺內容**：`baoyu-comic`（知識漫畫）、`baoyu-xhs-images`（小紅書圖卡）、`baoyu-infographic`（21 版型資訊圖）、`baoyu-slide-deck`（簡報）、`baoyu-cover-image`（封面圖）、`baoyu-article-illustrator`（文章配圖）、`baoyu-diagram`（SVG 流程/結構圖）
- **發布**：`post-to-x`、`post-to-wechat`、`post-to-weibo`
- **AI 生成**：`baoyu-image-gen`（多供應商）
- **工具**：`youtube-transcript`、`url-to-markdown`、`translate`、`compress-image` 等

> [!note] FB 那則「萬物皆可漫畫化」
> 一人公司研究所分享的漫畫化美編 reel，指的就是這套裡的 `baoyu-comic`。

## 何時用 (When)

- ✅ 適合：
  - 常做圖文內容（圖卡、簡報、資訊圖、配圖）想一鍵生
  - 想要現成、設計感不錯的 skill 直接用或改
  - 學別人怎麼寫一份結構良好的 SKILL.md
- ❌ 不適合：
  - 需求很特殊、和內容創作無關（自己寫 skill 更貼）

## 怎麼做 (How)

（待補實際安裝步驟——以官方 repo / README.zh 為準）

- Repo：`JimLiu/baoyu-skills`（README.zh.md 有中文說明）
- 用法：把要的 skill 放進你的 skills 目錄，Claude 偵測相符任務時載入；或拆解它的 SKILL.md 當範本改寫。

## Trade-offs

- ✅ 量多、覆蓋內容創作全流程，設計系統彈性（多版型/風格）
- ✅ 是學「skill 怎麼寫」的好教材
- ❌ 偏中文 / 中國平台場景（小紅書、微信、微博）
- ❌ skill 一次裝太多可能誤觸發，挑需要的就好

## 我的實測

（還沒實測，跑過再回來補）
- 用過的 skill：
- 產出品質：
- 踩到的坑：

## 相關

- [[Claude Skills]] ← 母概念：什麼是 Skills
- [[last30days-skill]] ← 另一類 skill（研究摘要）
- [[MOC-Agent模式]]
- [[MOC-Prompt工程]]

## 來源

- [JimLiu/baoyu-skills - GitHub (README.zh)](https://github.com/JimLiu/baoyu-skills/blob/main/README.zh.md)
