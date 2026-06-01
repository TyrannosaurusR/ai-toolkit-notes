---
title: axton-obsidian-visual-skills
type: 工具卡
topics:
  - 工具框架
  - agent
status: 待驗證
difficulty: 入門
created: 2026-06-02
source: https://github.com/axtonliu/axton-obsidian-visual-skills
---

> [!summary] TL;DR
> 作者 Axton Liu 為 Obsidian 量身打造的 **Claude Code Skills 套件**：說一句話，Claude 直接在你的 vault 裡生成 Excalidraw 手繪圖、Mermaid 圖、或 Obsidian Canvas 互動檔。把純文字筆記加上「視覺輔助層」，完整中文支援，MIT 授權。

## 是什麼 (What)

這套 Skills 讓 Claude Code 讀懂你的筆記內容，再用 Obsidian 原生格式輸出視覺化圖表——不需要你手動畫，也不需要離開 vault。

包含 **3 個 skill**：

> [!example] Skill 1：Excalidraw 圖表產生器
> 生成 `.excalidraw` 檔，在 Obsidian 裡直接渲染為可拖拉的手繪風格圖。
> - 支援 7 種圖型：流程圖、心智圖、層級圖、關係圖、比較圖、時間軸、矩陣
> - 完整中文支援、有動畫能力
> - 範例：「把 RAG 文件前處理的步驟畫成流程圖」

> [!example] Skill 2：Mermaid 視覺化工具
> 在 `.md` 裡直接插入 Mermaid code block，Obsidian 直接渲染，不開新檔。
> - 支援 6 種圖型：流程圖、環形流、比較圖、心智圖、序列圖、狀態圖
> - 內建語法錯誤防護（不生出 Obsidian 渲染不了的壞語法）
> - 範例：「把 Claude Skills 的觸發邏輯畫成序列圖」

> [!example] Skill 3：Obsidian Canvas 製作器
> 生成 `.canvas` 互動檔，Obsidian Canvas 頁面裡可直接拖拉節點。
> - 支援心智圖或自由版面
> - 自動計算節點位置、建立邊、色彩分組
> - 範例：「把這幾張卡片之間的關係畫成 Canvas」

## 何時用 (When)

- ✅ 適合：
  - 想把概念卡 / MOC 的結構可視化（一眼看清各卡關係）
  - 解釋複雜流程（RAG pipeline、Agent 架構）時要視覺輔助
  - 把現有的純文字筆記「加一層圖」，讓複習更快
- ❌ 不適合：
  - 精細的、需要精確排版的正式簡報（用 [[html-ppt-skill]] 或 [[open-slide]]）
  - 還不確定內容要寫什麼的情況（先把卡片內容填好，再圖像化）

## 怎麼做 (How)

（待補實際安裝步驟——以官方 repo 為準）

1. 把 repo clone 到本機，或直接下載 skill 資料夾。
2. 放進 Claude Code 的 skills 目錄（依官方文件指定路徑）。
3. 在 Claude Code 裡說：「用 Excalidraw 把 X 畫成 Y 圖」，skill 自動觸發，在 vault 生成圖檔。

> [!note] 實驗狀態
> repo 標示為 experimental，功能可用但邊角案例可能有粗糙之處。有問題可回 repo 開 issue 給作者 Axton Liu（YouTube + X 均可聯繫）。

## Trade-offs

- ✅ Obsidian 原生格式（.excalidraw / .canvas / Mermaid），不依賴外部服務
- ✅ 完整中文支援
- ✅ 把重複的手動畫圖動作自動化
- ❌ 實驗狀態，複雜圖可能需要手動微調
- ❌ 需要 Claude Code 環境（非 Claude Desktop 的 Projects）

## 我的實測

（還沒實測，跑過再回來補）
- 測試圖型：
- 中文渲染品質：
- 和手動畫相比的落差：

## 相關

- [[Claude Skills]] ← 這套就是 Claude Skills 的具體應用
- [[blender-mcp]] ← 同樣是「Claude 直接操控創意工具」的模式
- [[MOC-工具框架]]
- [[MOC-Agent模式]]

## 來源

- [axtonliu/axton-obsidian-visual-skills - GitHub](https://github.com/axtonliu/axton-obsidian-visual-skills)
