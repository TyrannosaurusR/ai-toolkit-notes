---
title: Chandra
type: 工具卡
topics:
  - 工具框架
  - rag
status: 待驗證
difficulty: 進階
created: 2026-06-01
source: https://github.com/datalab-to/chandra
---

> [!summary] TL;DR
> datalab 開源的**模型型 OCR / 文件解析器**：把複雜 PDF、掃描檔、圖片（雙欄、表格、數學公式、手寫、勾選框）原封不動轉成乾淨的 Markdown / HTML / JSON，並保留版面與 bounding box。專治「傳統 OCR 抓出一團亂、餵 AI 就幻覺」的痛點。

## 是什麼 (What)

Chandra 是 datalab（datalab-to）開源的文件解析模型。和規則型解析器（如 [[LiteParse]]）不同，它用**視覺模型**理解整頁內容，主打「**完美保留結構**」：

- 不只辨識文字，還能還原**表格、數學公式、手寫表單、打勾的勾選框**
- 輸出乾淨的 **Markdown / HTML / JSON**，保留版面與 bounding box
- 手寫辨識能力強，連草寫 / 舊手稿都能處理

> [!question] 待驗證的數字
> 來源稱 Chandra（OCR 2）約 **4B 參數**、在 olmOCR 基準達 **85.9%（SOTA）**。數字待我自己跑過或查官方 repo 再確認。

## 何時用 (When)

- ✅ 適合：
  - 掃描檔、拍照文件、手寫表單數位化
  - 雙欄 / 含表格 / 含公式的複雜版面
  - 要把大量紙本餵給 Agent / 建 RAG 知識庫
- ❌ 不適合：
  - 來源本來就是乾淨數位 PDF / Office（用 [[LiteParse]] 更快更省）
  - 沒有 GPU / 不想吃模型推論成本

## 怎麼做 (How)

（待補實際指令——以官方 repo / HF 為準）

- Repo：`datalab-to/chandra`
- 模型：huggingface.co/datalab-to/chandra
- 典型用途：掃描 / 手寫文件 → Chandra 轉成結構化 Markdown → 進 RAG ingestion。

## Trade-offs

- ✅ 結構保真度高（表格 / 公式 / 手寫 / 勾選框）
- ✅ 直接省下大量「清洗髒資料」的時間
- ✅ 開源、可本機掌控資料
- ❌ 吃 GPU / 推論時間，比規則型解析慢
- ❌ 數位原生檔上是殺雞用牛刀

## 我的實測

（還沒實測，跑過再回來補）
- 測試文件（掃描 / 手寫 / 表格）：
- 結構還原品質：
- 推論速度 / 資源：

## 相關

- [[RAG 文件前處理]] ← 母概念
- [[LiteParse]] ← 對照：規則 / 版面型解析
- [[MOC-Context-RAG]]
- [[MOC-工具框架]]

## 來源

- [datalab-to/chandra - GitHub](https://github.com/datalab-to/chandra)
- [Chandra 介紹 - @bing_sunzhi](https://www.threads.com/@bing_sunzhi/post/DXmIUFeEsiJ)
