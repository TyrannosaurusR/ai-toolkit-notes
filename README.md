# AI 生產力工具筆記

收集 AI 領域的各種技巧、模式、工具——從省 Token 到架 Agent。

## 結構

```
00_MOC/        ← 各大類的總覽地圖（先看這裡）
10_概念卡/      ← What / Why 層：解釋一個概念
20_實作卡/      ← How 層：具體一招怎麼用
30_工具框架/    ← 具體產品（LangGraph、MCP、Cursor…）
99_Inbox/      ← 還沒整理的資源連結丟這
_模板-卡片.md   ← 寫新卡時複製這份
```

## 使用規則

1. **新看到的東西** → 先丟 `99_Inbox/Inbox.md`，加一句話「為什麼留」。
2. **每週/雙週** → 從 Inbox 挑值得寫的，複製 `_模板-卡片.md`，寫成正式卡。
3. **寫卡時** → 在卡的 frontmatter 標 `topics`、`status`、`difficulty`。
4. **整理完** → 回 Inbox 把該連結打勾 `[x]`，連到新卡。
5. **MOC** → 每寫完一張卡，回到對應 MOC 加一條連結。

## 三個標籤軸

- **主題**：
  - 核心六大：`#token優化` `#prompt工程` `#rag` `#agent` `#pipeline` `#工具框架`
  - 周邊輔助：`#心法`（開發者心態與決策） `#基礎知識`（硬體/模型科普） `#資源`（素材庫、目錄類連結）
- **狀態**：`已實測` / `待驗證` / `理論`
- **難度**：`入門` / `進階`

## 卡片視覺：Callout 用法

用 Obsidian 內建 callout 給 8 段模板上視覺層 — 不裝 plugin、不寫 CSS、不換主題。

### 對應到模板段落

| 模板段落 / 內容性質 | Callout 寫法 | 顏色 |
|---|---|---|
| TL;DR | `> [!summary]` | 藍綠 |
| Trade-offs、我的實測（空白待補） | `> [!todo]` | 藍 |
| 警示、被證偽的內容 | `> [!warning]` | 橘 |
| 對比 — 正確 / 有效用法 | `> [!check]` | 綠 |
| 對比 — 錯誤 / 無效用法 | `> [!failure]` | 紅 |
| 補充說明、原文元資訊 | `> [!note]` 或 `[!info]` | 藍 |
| 待驗證的論點（`status: 待驗證`） | `> [!question]` | 黃 |
| Prompt / 程式碼範例 | `> [!example]` | 紫 |
| 原文引用 | `> [!quote]` | 灰 |

### 13 個類型備查（含別名）

`note` ／ `abstract`(`summary`, `tldr`) ／ `info` ／ `todo` ／ `tip`(`hint`, `important`) ／ `success`(`check`, `done`) ／ `question`(`help`, `faq`) ／ `warning`(`caution`, `attention`) ／ `failure`(`fail`, `missing`) ／ `danger`(`error`) ／ `bug` ／ `example` ／ `quote`(`cite`)

### 語法修飾符

```markdown
> [!note]              基本框，永遠展開
> [!note]+             可摺疊，預設「展開」
> [!note]-             可摺疊，預設「摺疊」（適合「來源」「相關」這種輔助段）
> [!warning] 自訂標題   覆蓋預設標題
```

### 嵌套

```markdown
> [!example] 多次實測
> > [!failure] 第一次：偏離太遠
> > [!success] 第二次：加 role 後穩定
```

### 規則

- **H2 標題保持純文字**，不加 emoji — 視覺層全部由 callout 承載
- 視覺裝飾要綁在「有內容的卡」上，不對空白模板預先美化
- 完整套用範例見 `10_概念卡/90% 的「提示詞技巧」都是迷信.md`

## 起步建議

不要一次寫滿。先挑一個最有感的主題（例如 Token 優化），寫 3-5 張實作卡跑通流程，兩週後再回來調結構。
