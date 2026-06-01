---
title: LiteParse
type: 工具卡
topics:
  - 工具框架
  - rag
status: 待驗證
difficulty: 入門
created: 2026-06-01
source: https://github.com/run-llama/liteparse
---

> [!summary] TL;DR
> LlamaIndex 開源的**輕量本機文件解析器**：用 Rust 寫、不需雲端/API key，把 PDF、Word、PPT、Excel、圖片轉成 AI 好讀的結構化資料，內建 OCR、保留表格與版面。是 RAG / Agent 前處理的省錢利器。

## 是什麼 (What)

LiteParse 是 LlamaIndex 團隊開源的文件解析器，定位是「輕量版」：

- **Rust 寫成**，完全在本機跑——無雲端、無 LLM 呼叫、無 API key
- 支援 PDF、DOCX、PPTX、XLSX、圖片
- 解析時**保留表格與圖表的空間 / 版面結構**
- 內建 OCR
- 專為「餵給 AI Agent / RAG 前處理」設計

它與雲端版的 **LlamaParse** 是互補關係（見下方 Trade-offs）。

## 何時用 (When)

- ✅ 適合：
  - 數位原生的 PDF / Office 檔批次解析
  - 要離線 / 不想付費 / 不想把文件送上雲端
  - RAG ingestion 的第一道前處理
- ❌ 不適合：
  - 高難度掃描 / 手寫 / 極複雜版面（交給模型型解析如 [[Chandra]]）
  - 要求極致精準、可接受雲端成本（用 LlamaParse）

## 怎麼做 (How)

（待補實際安裝指令——以官方 repo / 文件為準）

- Repo：`run-llama/liteparse`
- 文件：developers.llamaindex.ai/liteparse
- 典型用途：在建向量庫前，先用 LiteParse 把一批文件轉成結構化文字 → 再 chunking → embedding。

## Trade-offs

- ✅ 本機、免費、免 API key，資料不外流
- ✅ 速度快（Rust），適合大量文件批次
- ✅ 保留版面 / 表格結構，下游 chunking 切得準
- ❌ 對掃描 / 手寫的辨識力不如專門 OCR 模型
- ❌ 要「極致精準」時不如雲端 LlamaParse

## 我的實測

（還沒實測，跑過再回來補）
- 解析速度：
- 表格 / 版面還原品質：
- 與 LlamaParse 對比：

## 相關

- [[RAG 文件前處理]] ← 母概念
- [[Chandra]] ← 對照：模型 / OCR 型解析
- [[MOC-Context-RAG]]
- [[MOC-工具框架]]

## 來源

- [run-llama/liteparse - GitHub](https://github.com/run-llama/liteparse)
- [LiteParse 介紹 - @0xspeter](https://www.threads.com/@0xspeter/post/DZAWoJdk7HX)
