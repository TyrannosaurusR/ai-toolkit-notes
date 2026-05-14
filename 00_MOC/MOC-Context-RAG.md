---
title: MOC - Context 工程 / RAG
type: MOC
topics: [rag, context工程]
created: 2026-05-11
---

# MOC - Context 工程 / RAG

> 怎麼餵對的資料給模型。2026 趨勢：RAG 正在被「Context Engineering」這個更大的概念吸收。

## 主要方向

### 1. 基礎 RAG
- [[什麼是RAG]]
- [[Embedding模型怎麼選]]
- [[Vector-DB比較-Pinecone-Weaviate-Qdrant]]

### 2. Chunking 策略
切資料的方式直接決定召回品質。
- [[固定長度vs語意切分]]
- [[Parent-Child-Chunk]]
- [[Late-Chunking]]

### 3. 檢索增強
- [[Hybrid-Search-向量+關鍵字]]
- [[Reranking-Cross-Encoder]]
- [[Query-Rewriting查詢改寫]]

### 4. Agentic RAG（2026 主流）
讓 Agent 自己決定要不要查、查什麼、查得對不對。
- [[什麼是Agentic-RAG]]
- [[Self-RAG自我驗證]]
- [[Corrective-RAG-CRAG]]

### 5. Context Engineering
比 RAG 更大的命題：模型看到的「所有東西」都該設計。
- [[Context-Engineering總覽]]
- [[Memory系統-短期vs長期]]
- [[Context-Window預算規劃]]

## 重要原則

- **RAG ≠ 把文件塞進去就好**：召回品質 > 召回數量。
- **Context Engineering = RAG + Memory + 工具回傳 + 系統指令 的總和設計**。
- **能不查就別查**：Agentic RAG 的核心是判斷「這題需不需要外部知識」。

## 待開卡

- [ ] GraphRAG
- [ ] 多模態 RAG
- [ ] Long-context vs RAG 取捨

## 參考資料

- [RAG to Context Engineering - Callstack](https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems)
- [Context Engineering Guide 2026 - Meta Intelligence](https://www.meta-intelligence.tech/en/insight-context-engineering)
- [From RAG to Context - RAGFlow](https://ragflow.io/blog/rag-review-2025-from-rag-to-context)
- [Building Production RAG Systems 2026 - brlikhon](https://brlikhon.engineer/blog/building-production-rag-systems-in-2026-complete-tutorial-with-langchain-pinecone)
