# AI 生產力工具筆記

收集 AI 領域的各種技巧、模式、工具——從省 Token 到架 Agent。

## 結構

```
00_MOC/        ← 各主題的導覽地圖（先看這裡）
token優化/     ← 主題資料夾：省 token / 輸出加速
prompt工程/    ← 主題資料夾：指令設計、推理引導、模板
rag/           ← 主題資料夾：文件解析、向量庫、Context Engineering
agent/         ← 主題資料夾：Agent 模式、Skills、記憶
pipeline/      ← 主題資料夾：固定流程編排（有第一張卡時建立）
工具框架/      ← 主題資料夾：無更尖銳主題的通用基礎設施工具（有需要時建立）
99_Inbox/      ← 還沒整理的資源連結丟這
_模板-卡片.md   ← 寫新卡時複製這份
```

## 歸檔規則（新卡放哪個資料夾？）

- 問自己：**這張卡最主要是關於哪個核心主題？** → 放進對應主題資料夾。
- 核心六大：`token優化` / `prompt工程` / `rag` / `agent` / `pipeline` / `工具框架`
- **`工具框架` 是 catch-all**，只放沒有更尖銳主題的通用基礎設施（vLLM、Pinecone…）。有更尖銳的主題時絕對不選它（LiteParse → rag/；baoyu-skills → agent/）。
- 卡片的**類型**（概念卡/實作卡/工具卡/設定檔）填在 frontmatter `type:` 裡，不反映在資料夾上。

## 使用規則

1. **新看到的東西** → 先丟 `99_Inbox/Inbox.md`，加一句話「為什麼留」。
2. **每週/雙週** → 從 Inbox 挑值得寫的，複製 `_模板-卡片.md`，放進對應**主題資料夾**，寫成正式卡，frontmatter 填好 `type` / `topics` / `status` / `difficulty`。
3. **整理完** → 回 Inbox 把該連結打勾 `[x]`，連到新卡。
4. **MOC** → 每寫完一張卡，回對應主題 MOC 的 `## 索引（已開卡）` 加一條連結。

## MOC 兩區段規則

每個 MOC 固定分兩區：
- **`## 索引（已開卡）`** — 只有 [[真實存在的卡]]，你可以信任
- **`## 待開卡`** — phantom 連結 + 未來想寫的 topic，是 backlog 不是謊言

## 三個標籤軸

- **主題**：
  - 核心六大：`#token優化` `#prompt工程` `#rag` `#agent` `#pipeline` `#工具框架`
  - 周邊輔助：`#心法`（開發者心態與決策） `#基礎知識`（硬體/模型科普） `#資源`（素材庫、目錄類連結）
- **狀態**：`已實測` / `使用中` / `待驗證` / `理論`
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
- 完整套用範例見 `prompt工程/90趴提示詞迷信.md`

## 起步建議

不要一次寫滿。先挑一個最有感的主題（例如 Token 優化），寫 3-5 張實作卡跑通流程，兩週後再回來調結構。
