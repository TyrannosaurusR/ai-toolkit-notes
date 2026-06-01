---
title: CC Workflow Studio
type: 工具卡
topics:
  - agent
  - 工具框架
status: 待驗證
difficulty: 入門
created: 2026-06-02
source: https://github.com/breaking-brake/cc-wf-studio
---

> [!summary] TL;DR
> 視覺化的 **AI agent 工作流編輯器**：在拖拉畫布上設計多 agent 流程 → 一鍵匯出成 Claude Code / Copilot / Cursor / Gemini CLI 等都能直接讀的 Markdown 檔。核心理念：「你在視覺層思考，AI 在 Markdown 層思考，這工具橋接兩者。」5.1k★，v3.34.3。

## 是什麼 (What)

一份 `workflow.json` 驅動三個介面：

**1. VSCode 擴充（主介面）**
- React Flow 拖拉畫布，設計 sub-agent / skills / MCP 工具的編排
- 「Edit with AI」：用自然語言口述要改哪裡，即時更新畫布

**2. CLI 工具** (`ccwf`)
- `render`、`validate`、`preview`、`export`、`run`
- 適合 CI 或終端機作業

**3. MCP Server** (`ccwf-mcp`)
- 外部 AI agent 透過 MCP 讀取 / 編輯工作流
- 每次編輯即時反映回 VSCode 畫布

匯出後的目錄依 agent 不同：

| Agent | 匯出路徑 |
|---|---|
| Claude Code | `.claude/agents/`、`.claude/commands/` |
| GitHub Copilot Chat | `.github/prompts/` |
| Cursor | `.cursor/agents/`、`.cursor/skills/` |
| Gemini CLI | `.gemini/` |
| OpenAI Codex | `.codex/` |

## 何時用 (When)

- ✅ 適合：
  - 要設計複雜的多 agent 流程，文字描述容易亂
  - 想讓同一套工作流跑在多個 agent 環境（Claude + Cursor + Copilot）
  - 用「Edit with AI」口述修改，比手動改 Markdown 快
- ❌ 不適合：
  - 簡單的單一 prompt 任務（直接下 prompt 就好）
  - 不用 VSCode 的環境（CLI 可用，但主介面是 VSCode 擴充）

## 怎麼做 (How)

三選一安裝：

```bash
# VSCode 擴充（推薦）
code --install-extension breaking-brake.cc-wf-studio

# CLI
npx @cc-wf-studio/cli

# MCP server（配合 MCP 客戶端使用）
# 依官方文件設定
```

使用流程：
1. 開 VSCode，在畫布拖拉設計工作流
2. 「Edit with AI」口述調整
3. 點匯出 → 選目標 agent → Markdown 自動寫進對應目錄
4. Claude Code 裡用 `/workflow-name` 呼叫

## Trade-offs

- ✅ 一套設計、多 agent 複用
- ✅ 視覺設計 + AI 口述修改，降低「寫 SKILL.md」的認知負擔
- ✅ MCP server 讓外部工具也能讀寫工作流
- ❌ AGPL-3.0（網路部署需公開源碼，商業用途注意授權）
- ❌ 以 VSCode 為核心，非 VSCode 用戶體驗較差

## 我的實測

（還沒實測，跑過再回來補）
- 設計一個工作流的體驗：
- 匯出到 Claude Code 的效果：
- Edit with AI 的準確度：

## 相關

- [[Claude Skills]] ← 匯出的 Markdown 工作流就是 skill 格式
- [[Hivemind]] ← 另一個角度解決 agent 知識積累問題
- [[MOC-Agent模式]]
- [[MOC-工具框架]]

## 來源

- [breaking-brake/cc-wf-studio - GitHub](https://github.com/breaking-brake/cc-wf-studio)
