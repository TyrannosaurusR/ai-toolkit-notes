---
title: MOC - Pipeline / Workflow
type: MOC
topics: [pipeline]
created: 2026-05-11
---

# MOC - Pipeline / Workflow

> 怎麼把多步驟串起來。和 Agent 模式的差別：Pipeline 偏「固定流程」，Agent 偏「動態決策」。

## 主要方向

### 1. 基礎流程模式
- [[Sequential-Pipeline順序管線]]
- [[Parallel-Fan-out平行扇出]]
- [[Conditional-Branching條件分支]]
- [[Map-Reduce模式]]

### 2. 可靠性
- [[Retry與Backoff策略]]
- [[Idempotency冪等性]]
- [[Dead-Letter-Queue失敗訊息存放]]

### 3. 觀測性
- [[LLM-Tracing-LangSmith-Langfuse]]
- [[Token-成本追蹤]]
- [[Quality-Eval評測管線]]

### 4. 人機協作
- [[Human-in-the-loop檢查點]]
- [[Approval-Gate關鍵動作確認]]

### 5. 部署模式
- [[Batch批次vs-Streaming串流]]
- [[Async非同步處理]]

## Pipeline vs Agent 該選哪個？

| 場景 | 用 Pipeline | 用 Agent |
|---|---|---|
| 步驟固定、輸入可預期 | ✅ | ❌（多餘） |
| 步驟取決於中間結果 | ⚠️ 加條件分支 | ✅ |
| 需要工具動態組合 | ❌ | ✅ |
| 重視可靠性與可預測 | ✅ | ⚠️ |
| 探索性、開放式任務 | ❌ | ✅ |

## 重要原則

- **先 Pipeline 再 Agent**：能用固定流程就別開放決策權。
- **每一步都要有 fallback**：LLM 會失敗，沒設計失敗路徑 = 線上事故。
- **Tracing 從第一天就要有**：沒有觀測就等於黑盒。

## 待開卡

- [ ] DSPy 的 pipeline 編譯
- [ ] Temporal / Inngest 等工作流引擎
- [ ] LangGraph 當 pipeline 用

## 參考資料

- [Agentic Workflows 2026 - Vellum](https://www.vellum.ai/blog/agentic-workflows-emerging-architectures-and-design-patterns)
- [What are Agentic Workflows - Orkes](https://orkes.io/blog/what-are-agentic-workflows/)
