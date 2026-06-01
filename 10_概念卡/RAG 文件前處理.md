---
title: RAG 文件前處理：解析品質決定召回天花板
type: 概念卡
topics:
  - rag
  - 工具框架
status: 待驗證
difficulty: 入門
created: 2026-06-01
---

> [!summary] TL;DR
> RAG 的召回品質，從「文件被解析成什麼樣」就決定了。爛解析（亂排版、表格散架、漏字）餵進向量庫，後面再強的 chunking、reranking 都救不回來——**解析是整條 pipeline 的天花板**。

## 是什麼 (What)

大家談 RAG 多半從 chunking、embedding、reranking 開始，但這些都建立在一個前提上：**文件已經被乾淨地轉成文字了**。

實務上資料常是 PDF、掃描檔、簡報、Excel、甚至手寫表單。把它們轉成文字的這一步叫 **文件解析 / 前處理（parsing / ingestion）**，它在 pipeline 的最前端：

```
原始文件 → [解析/OCR] → 純文字+結構 → chunking → embedding → 向量庫 → 檢索
              ↑ 這一步爛掉，後面全部白做
```

> [!warning] Garbage in, garbage out
> 雙欄論文被解析成左右交錯、表格被拉成一行、公式變亂碼、漏字錯字——這些爛資料進了向量庫，模型檢索到後只會**更容易產生幻覺**，而且你很難從下游發現問題其實出在最上游。

## 何時用 (When)

- ✅ 適合（需要認真做解析）：
  - 來源是 PDF / 掃描檔 / 簡報 / 含表格的文件
  - 含手寫、表單、勾選框、數學公式的資料
  - 知識庫品質要求高、不能容忍幻覺
- ❌ 不適合（解析不是瓶頸）：
  - 來源本來就是乾淨的純文字 / Markdown / HTML
  - 資料量小、可人工清洗

## 怎麼做 (How)

解析工具大致分兩派，依「文件長相」選：

> [!check] 規則 / 版面型解析（快、本機、結構化檔案）
> 直接讀文件的結構與版面，速度快、可離線。適合**數位原生**的 PDF / Office 檔。
> → 代表：[[LiteParse]]（LlamaIndex，Rust，本機）

> [!check] 模型 / OCR 型解析（慢、吃算力、掃描/手寫）
> 用視覺模型「看懂」整頁，能處理掃描、手寫、複雜版面，並保留表格 / 公式結構。
> → 代表：[[Chandra]]（datalab，OCR 模型）

選法心法：
- 檔案是**數位 PDF / Office** → 先用規則型（LiteParse），快又省。
- 檔案是**掃描 / 拍照 / 手寫 / 雙欄複雜版面** → 用模型型（Chandra）。
- 要極致精準且能接受雲端 → 雲端服務（如 LlamaParse）。

## Trade-offs

- ✅ 把工夫花在最上游，下游 chunking / 檢索的效果上限直接被拉高
- ✅ 結構（表格、標題層級）保留得好，chunking 才切得準
- ❌ 模型型解析吃 GPU / 時間成本
- ❌ 沒有一招通吃：得依文件類型搭配工具

## 我的實測

（還沒實測，跑過再回來補）
- 測試文件類型：
- 解析品質 / 表格還原：
- 對下游召回的影響：

## 相關

- [[LiteParse]] ← 規則/版面型，本機快速
- [[Chandra]] ← 模型/OCR 型，掃描手寫
- [[MOC-Context-RAG]]

## 來源

- [LiteParse - @0xspeter](https://www.threads.com/@0xspeter/post/DZAWoJdk7HX)
- [Chandra - @bing_sunzhi](https://www.threads.com/@bing_sunzhi/post/DXmIUFeEsiJ)
