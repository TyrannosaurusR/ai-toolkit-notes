---
title: MOC - Agent 設計模式
type: MOC
topics: [agent]
created: 2026-05-11
---

# MOC - Agent 設計模式

> 單一 / 多 Agent 怎麼協作。2026 業界共識的 6 大基礎模式 + 多 Agent 編排。

## 六大基礎模式

業界（Microsoft、Databricks、Anthropic）大致共識的最小工具箱：

### 1. Reflection（反思）
讓模型批評自己的答案再改寫。
- [[Reflection模式]]
- [[Self-Critique-vs-外部評審]]

### 2. Tool Use（工具使用）
模型呼叫外部 API、執行程式、查資料。
- [[Tool-Use基礎]]
- [[Function-Calling-vs-MCP]]

### 3. Planning（規劃）
先列任務清單，再逐步執行。
- [[Plan-and-Execute模式]]
- [[ReAct-Reason+Act]]

### 4. Multi-Agent Collaboration（多 Agent 協作）
不同角色的 Agent 合作完成任務。
- [[Manager-Worker模式]]
- [[Debate-多Agent辯論]]

### 5. Orchestrator-Worker（編排者-工人）
一個 Agent 分派任務，多個 Agent 平行執行。
- [[Orchestrator-Worker模式]]

### 6. Evaluator-Optimizer（評估-優化）
一個產出、一個評分、迴圈到達標。
- [[Evaluator-Optimizer模式]]

## 編排策略

- [[Sequential順序執行]]
- [[Parallel平行執行]]
- [[Handoff-Agent間交棒]]
- [[Group-Collaboration群組協作]]

## 生產環境要點

- [[Human-in-the-loop檢查點設計]]
- [[Agent輸出驗證-避免錯誤傳染]]
- [[Checkpointing-Time-travel]]

## 重要原則

- **能不用 Agent 就別用 Agent**：簡單任務一個 LLM call 解決，別硬上 Agent。
- **多 Agent 不一定更好**：協調成本可能高過收益。
- **關鍵動作要 Human-in-the-loop**：發 email、付款、改 DB 都該停一下等人確認。

## 待開卡

- [ ] LangGraph 的 Graph-based 編排
- [ ] Swarm（OpenAI）vs CrewAI vs AutoGen 比較

## 參考資料

- [Agentic Design Patterns 2026 - SitePoint](https://www.sitepoint.com/the-definitive-guide-to-agentic-design-patterns-in-2026/)
- [AI Agent Orchestration Patterns - Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/ai-agent-design-patterns)
- [Agent System Design Patterns - Databricks](https://docs.databricks.com/aws/en/generative-ai/guide/agent-system-design-patterns)
- [Agentic Workflows 2026 - Vellum](https://www.vellum.ai/blog/agentic-workflows-emerging-architectures-and-design-patterns)
