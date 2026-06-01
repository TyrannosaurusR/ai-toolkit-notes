---
title: AI 生成簡報工具對照：html-ppt-skill vs open-slide
type: 概念卡
topics:
  - agent
  - 工具框架
status: 待驗證
difficulty: 入門
created: 2026-06-02
---

> [!summary] TL;DR
> 兩個都能讓 AI 用自然語言生成簡報，但本質不同：**html-ppt-skill 追求速度**（說完就有靜態 HTML，直接用），**open-slide 追求可維護性**（React 源碼，可重複迭代）。選哪個取決於你要「一次性快速輸出」還是「長期維護的模板」。

## 是什麼 (What)

### html-ppt-skill（lewislulu）

`AgentSkill` 格式，接一句話就生出一份純靜態 HTML/CSS/JS 簡報，**無編譯步驟**，直接在瀏覽器打開。

- 36 主題、31 版型、47 動畫效果（含 Canvas 粒子特效）
- 15 個完整 Deck 模板可套用
- 演講者模式（按 S）：獨立窗口含備注、計時器、與主畫面同步
- 5.3k★，積極開發中

> [!example] 觸發範例
> 「做一份 8 頁技術分享 slides，用 cyberpunk 主題，包含流程圖版型」

### open-slide（1weiho）

`框架 + CLI` 的組合，自然語言描述 → **React 元件**，需要 Node 環境。

- 固定 1920×1080 畫布（消除 AI 的版面不確定性）
- 頁面是任意 React 元件，無受限 DSL，定制力無上限
- 瀏覽器編輯器可點選元素後加文字評論，再 `/apply-comments` 套用
- 可匯出靜態 HTML、PDF、或部署到 Vercel/Cloudflare Pages
- 4.2k★，最新 v1.2.6（2026-05-30）

> [!example] 觸發範例
> `npx @open-slide/cli init my-deck` → 進入 React 工作區 → 用 `/create-slide` skill 生成內容

## 何時用 (When)

> [!check] 選 html-ppt-skill 的情境
> - 要快：今天要用，現在就要有檔案
> - 一次性演講、不需要日後迭代
> - 非技術背景，不想碰 Node/React
> - 想要漂亮動畫效果（47 種）

> [!check] 選 open-slide 的情境
> - 要做公司品牌簡報模板，以後每季都用
> - 需要完全自訂（html-ppt-skill 的 36 主題都不對味）
> - 本來就用 React 技術棧
> - 需要 PDF 輸出或部署到網頁

> [!warning] 都不適合的情境
> - 需要複雜圖表 / 資料視覺化（用 Mermaid、D3 等專門工具）
> - 精細的品牌設計要求（AI 生成的 layout 有隨機性）

## 怎麼做 (How)

**html-ppt-skill**：安裝 skill 後，對 Claude 說你要什麼，它輸出 HTML 檔案，存下來就能用。

**open-slide**：
```bash
npx @open-slide/cli init my-slide
# 回答 4 個設定問題後進入工作區
# 再用 /create-slide skill 生成內容
```

## Trade-offs

| | html-ppt-skill | open-slide |
|---|---|---|
| 速度 | ⚡ 即生即用 | 需初始化環境 |
| 定制力 | 固定主題 / 版型組合 | React 無上限 |
| 輸出 | 靜態 HTML | HTML / PDF / 部署 |
| 技術門檻 | 零（不需 npm） | 需 Node + React |
| 可維護性 | 靜態檔，難迭代 | 源碼，可長期維護 |
| 動畫 | 47 種（Canvas 特效） | 靠 React 元件實作 |

## 相關

- [[html-ppt-skill]] ← 工具卡（待開，或與本卡合併）
- [[Claude Skills]] ← 這兩個都算 skill 生態
- [[MOC-工具框架]]
- [[MOC-Agent模式]]

## 來源

- [lewislulu/html-ppt-skill - GitHub](https://github.com/lewislulu/html-ppt-skill)
- [1weiho/open-slide - GitHub](https://github.com/1weiho/open-slide)
