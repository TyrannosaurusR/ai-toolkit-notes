---
title: blender-mcp
type: 工具卡
topics:
  - 工具框架
  - agent
status: 待驗證
difficulty: 入門
created: 2026-05-14
source: https://github.com/ahujasid/blender-mcp
---

## TL;DR

透過 MCP 把 Claude 接上 Blender，用自然語言指揮它建模、上材質、佈場景，並能直接調用 Poly Haven、Sketchfab、Hyper3D Rodin 等外部素材/AI 模型來源。

## 是什麼 (What)

BlenderMCP 是一個 MCP（Model Context Protocol）伺服器，在 Claude Desktop 與 Blender 之間建一條對話通道。Claude 可以：

- 建立 / 修改 / 刪除 3D 物件
- 套用、修改材質與顏色
- 讀取場景狀態（含 viewport 截圖）
- 執行任意 Python（透過 `execute_blender_code` 工具）
- 從 Poly Haven 抓 model / texture / HDRI
- 從 Sketchfab 搜尋並下載模型
- 用 Hyper3D Rodin 生成 AI 3D 模型

換句話說，它把 Blender 變成「Claude 可以伸手進去操作的 3D 場景」。

## 何時用 (When)

- ✅ **適合**：
  - 概念草圖 → 3D 場景的快速原型（dungeon、海灘、室內擺設）
  - 不熟 Blender 操作但會描述視覺結果的人
  - 從參考圖反推場景（Claude 看圖描述 → 同時動手建）
  - 重複性高的場景組裝（批次套材質、批次擺物件）

- ❌ **不適合**：
  - 精細建模（拓樸、雕刻、UV 展開）—— Claude 對細節幾何沒手感
  - 已有完整 production pipeline 的專案（突然冒出個會跑任意 Python 的 agent 很危險）
  - 需要可重現流程的工作（同樣 prompt 不保證同樣結果）

## 怎麼做 (How)

### 安裝

1. 安裝 `uv` 套件管理器（前置）
2. 從 repo 下載 `addon.py`，在 Blender → Edit → Preferences → Add-ons 裝起來
3. 編輯 Claude Desktop 的 `claude_desktop_config.json`，加入 MCP server 設定
4. 在 Blender 啟用 addon，點「Connect to Claude」

### 使用

啟用後直接在 Claude Desktop 對話即可，例如：

```
幫我做一個低多邊形地牢場景，要有石牆、火把、跟一隻骷髏怪。
```

Claude 會自動分解步驟、呼叫對應工具。複雜場景建議**拆成小步驟**指揮（連續對話），不要一句話塞滿。

## Trade-offs

- ✅ 跨過 Blender 學習曲線最高的那段（介面熟悉度）
- ✅ 內建串接幾個素材庫（Poly Haven / Sketchfab / Hyper3D），不用自己找
- ✅ 場景理解可看截圖，回饋迴圈完整
- ❌ **安全風險高**：`execute_blender_code` 是任意 Python，prompt injection 或誤指令可能爆檔。**動手前一定要存檔。**
- ❌ 複雜操作要拆步驟，不能一句話搞定
- ❌ 初次連線常出問題，第一個指令發完才會穩

## 我的實測

（還沒實測，跑過再回來補）
- 場景複雜度：
- 出圖品質：
- 踩到的坑：

## 相關

- [[MOC-工具框架]]
- [[MOC-Agent模式]]
- [[Fusion-Claude整合]] ← 同類：Claude 操控 CAD 軟體（待開卡）

## 來源

- [ahujasid/blender-mcp - GitHub](https://github.com/ahujasid/blender-mcp)
