---
title: MOC - 工具與框架
type: MOC
topics: [工具框架]
created: 2026-05-11
---

# MOC - 工具與框架

> 具體可用的產品、框架、SDK。注意：每個工具的**主題家**是它的對應主題 MOC（RAG 工具見 [[MOC-Context-RAG]]；Agent/Skills 工具見 [[MOC-Agent模式]]）。本 MOC 收錄**無更尖銳主題歸屬**的通用基礎設施工具。

## 索引（已開卡）

### Claude + 創意軟體（詳見 MOC-Agent模式）
- [[blender-mcp]] — Claude 操控 Blender 做 3D 建模與場景
- [[axton-obsidian-visual-skills]] — Claude Code Skills 在 Obsidian 生成 Excalidraw/Mermaid/Canvas

（其他 Agent/Skills 工具見 [[MOC-Agent模式]] 的索引）

## 選用原則

- **工具框架是 catch-all**：能歸到 rag / agent / pipeline 的工具，回到那個主題 MOC 看。
- **MCP 優先**：能用 MCP 接的工具就用，避免綁特定框架。
- **觀測工具至少裝一個**：免費的 Langfuse 自架就夠用。

## 待開卡

### Agent / 編排框架
- [ ] [[LangChain]] — 老牌、生態大、有點重
- [ ] [[LangGraph]] — 圖式編排、Stateful
- [ ] [[Microsoft-Agent-Framework]]
- [ ] [[CrewAI]] — 角色化多 Agent
- [ ] [[AutoGen]] — MS Research 多 Agent 對話
- [ ] [[Swarm-OpenAI]] — 輕量、教學取向
- [ ] [[DSPy]] — 把 prompt 當程式編譯
- [ ] Mastra（TypeScript Agent 框架）

### 開發環境 / Coding Agent
- [ ] [[Claude-Code-CLI]]
- [ ] [[Cursor]]
- [ ] [[Windsurf]]
- [ ] [[Aider]]
- [ ] [[Continue]]

### 協定 / 標準
- [ ] [[MCP-Model-Context-Protocol]] — 2026 已成事實標準
- [ ] [[OpenAI-Function-Calling]]
- [ ] [[A2A-Agent-to-Agent協定]]

### RAG / Vector DB
- [ ] [[Pinecone]]
- [ ] [[Weaviate]]
- [ ] [[Qdrant]]
- [ ] [[Chroma]]
- [ ] [[LlamaIndex]]

### 觀測 / 評測
- [ ] [[LangSmith]]
- [ ] [[Langfuse]]
- [ ] [[Phoenix-Arize]]
- [ ] [[Braintrust]]
- [ ] [[Weights-Biases-Weave]]

### 推論加速 / 部署
- [ ] [[vLLM]]
- [ ] [[Ollama]] — 本地跑開源模型
- [ ] [[Together-AI]] — 推論服務
- [ ] [[Groq]] — 極速推論
- [ ] Modal / Replicate
- [ ] Letta（Memory 框架）

### 模型 API
- [ ] [[Claude-API]]
- [ ] [[OpenAI-API]]
- [ ] [[Gemini-API]]
- [ ] [[OpenRouter]] — 統一介面切換模型

## 資源清單

- [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) — 所有軟體的開源替代品
- [cal.diy](https://github.com/calcom/cal.diy) — Cal.com MIT 開源版排程系統，可自架免月費
- [itsHover](https://github.com/itshover/itshover) — React+Motion 動畫 icon 函式庫，shadcn CLI 一行安裝
- [Bumblebee (Perplexity)](https://github.com/perplexityai/bumblebee) — 開源供應鏈掃描器，MCP 設定當攻擊面掃描
- [FreeDomain (DigitalPlat)](https://github.com/DigitalPlatDev/FreeDomain) — 免費網域（173k★）
- [MiroFish](https://github.com/666ghj/MiroFish) — 多代理 AI 模擬預測引擎（63k★）
- [SANA (NVlabs)](https://github.com/NVlabs/Sana) — 高效圖像/影片生成，含相機控制（8k★）
- [MindVideo](https://www.mindvideo.ai/) — 免費 AI 影像/影片/音訊生成平台，內建 GPT Image 2
- [TrendRadar](https://github.com/sansan0/TrendRadar) — AI 輿情/熱點監控，35 平台聚合+MCP 分析
- [Mano-P (Mininglamp-AI)](https://github.com/Mininglamp-AI/Mano-P) — 本機 GUI-VLA Agent，OSWorld 第一（58.2%）
- [Video2X](https://github.com/k4yt3x/video2x) — ML 影片/圖片放大補幀（20k★）
- [Anthropic Academy](https://anthropic.skilljar.com/claude-101) — 官方免費 13 門課，附證書
- [AI Engineering from Scratch](https://github.com/rohitg00/ai-engineering-from-scratch) — MIT 免費，從基礎數學到 production（400+ 課）
- [awesome-agentic-ai-zh](https://github.com/WenyuChiou/awesome-agentic-ai-zh) — 繁中 Agentic AI 學習地圖（145+ 精選）
