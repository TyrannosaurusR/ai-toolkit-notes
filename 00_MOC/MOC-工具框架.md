---
title: MOC - 工具與框架
type: MOC
topics: [工具框架]
created: 2026-05-11
---

# MOC - 工具與框架

> 具體可用的產品、框架、SDK。和上面四張 MOC 的差別：這裡放「東西」，那邊放「方法」。

## Agent / 編排框架

- [[LangChain]] - 老牌、生態大、有點重
- [[LangGraph]] - 圖式編排、Stateful、是 LangChain 的進階版
- [[Microsoft-Agent-Framework]] - MS 開源的多 Agent 編排
- [[CrewAI]] - 角色化多 Agent
- [[AutoGen]] - MS Research 的多 Agent 對話
- [[Swarm-OpenAI]] - 輕量、教學取向
- [[DSPy]] - 把 prompt 當程式編譯

## 開發環境 / Coding Agent

- [[Claude-Code-CLI]]
- [[Cursor]]
- [[Windsurf]]
- [[Aider]]
- [[Continue]]

## 領域應用 / Claude + 創意軟體

- [[blender-mcp]] - Claude 操控 Blender 做 3D 建模與場景
- [[axton-obsidian-visual-skills]] - Claude Code Skills：在 Obsidian vault 生成 Excalidraw/Mermaid/Canvas 圖
- [[Fusion-Claude整合]] - Claude 操控 Autodesk Fusion 360（待開卡）

## 協定 / 標準

- [[MCP-Model-Context-Protocol]] - Anthropic 推的工具協定，2026 已成事實標準
- [[OpenAI-Function-Calling]]
- [[A2A-Agent-to-Agent協定]]

## RAG / Vector

- [[Pinecone]]
- [[Weaviate]]
- [[Qdrant]]
- [[Chroma]]
- [[LlamaIndex]]

## 觀測 / 評測

- [[LangSmith]]
- [[Langfuse]]
- [[Phoenix-Arize]]
- [[Braintrust]]
- [[Weights-Biases-Weave]]

## 推論加速 / 部署

- [[vLLM]]
- [[Ollama]] - 本地跑開源模型
- [[Together-AI]] - 推論服務
- [[Groq]] - 極速推論

## 模型 API

- [[Claude-API]]
- [[OpenAI-API]]
- [[Gemini-API]]
- [[OpenRouter]] - 統一介面切換模型

## 選用原則

- **越大的生態不一定越適合你**：LangChain 功能多但抽象層厚，小專案可能直接寫 SDK 更快。
- **MCP 優先**：能用 MCP 接的工具就用，避免綁特定框架。
- **觀測工具至少裝一個**：免費的 Langfuse 自架就夠用。

## 待開卡

- [ ] Modal / Replicate（部署）
- [ ] Letta（Memory 框架）
- [ ] Mastra（TypeScript Agent 框架）
