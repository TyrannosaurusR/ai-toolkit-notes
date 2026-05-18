---
title: Prompt - 設計時間規劃軟體
type: 實作卡
topics:
  - prompt工程
  - 場景模板
  - 軟體設計
status: 使用中
difficulty: 中階
created: 2026-05-18
source: 萬能Mega-Prompt 模板的應用案例
---

> [!summary] TL;DR
> 用萬能 Mega-Prompt 9 段格式寫的「請 AI 幫我設計一個自動化時間規劃軟體」prompt。輸入既有的 3 份 md（主規劃／臨時重排／個人基線檔），AI 會分階段輸出：A 架構設計 → B 完整 codebase → C 部署 checklist。

## 是什麼 (What)

這是一份「**設計軟體用的 prompt**」 — 把現有的手動工作流（[[Prompt-腦清空與排程]] + [[Prompt-臨時重排]] + [[個人基線檔]]）打包成需求文件，請 AI 設計成一個本地 Python web app。

> [!note] 整體系統願景
> 本地 web app（Python + gentelella）
> ↓ 內部封裝
> baseline.yaml（11 節）+ prompt 模板（主規劃+臨時）+ LLM 抽象層（Gemini/Ollama）
> ↓
> 分類表 + 行事曆視圖 + 餅圖 + 進度條 + PDF

## 何時用 (When)

- 適合：對齊好功能需求後，請 AI 一次設計完整 web app
- 不適合：
  - 需求還不清楚 → 先跟自己對齊（用 [[萬能Mega-Prompt 模板]] 的 input_data 段做需求清單）
  - 想自己練功寫 code → 這份會給太多現成 code，會剝奪你思考機會
  - 小模型（< Sonnet 4.6 / Gemini 1.5 Pro 等級）→ 容易吐不完整 codebase

## 怎麼做 (How)

### 1. 對齊功能規格（已完成）

依 2026-05-18 對話結果，本 prompt 已固化以下決定：

| 區塊 | 結論 |
| ---- | ---- |
| 軟體形式 | Flask web app + localhost 自動開瀏覽器 |
| UI 主題 | gentelella admin template |
| LLM 主用 | Gemini Pro API |
| LLM 備援 | Ollama (Qwen2.5-14B 推薦) |
| 抽象層 | LLMClient interface，未來可擴 OpenAI/Claude |
| Refine | Chat-style 多輪對話 |
| 視覺化 | 行事曆 + 餅圖 + 進度條 |
| 設定編輯 | UI 表單欄位（非 YAML 編輯器）|
| 歷史紀錄 | SQLite 或 JSON（AI 選）|
| 通知 | 無 |
| 進度追蹤 | 規劃分配時數，非實際完成 |

### 2. 使用流程

1. 開新對話，選用大模型（Claude Opus 4.7 / Gemini 2.0 Pro / GPT-4o）
2. 複製本卡第 3 節整個 xml block
3. 把 `<input_data>` 內的 3 個 `[貼上 ...]` 替換成：
   - [[Prompt-腦清空與排程]] 全文
   - [[Prompt-臨時重排]] 全文
   - [[個人基線檔]] 全文
4. 送出 → 先收到「階段 A 架構設計」
5. 看完 architecture，回「請繼續階段 B」即可拿到 code
6. 收到 code 後跑 `python app.py`，根據 README 安裝環境
7. 第一次跑必有 bug，貼錯誤訊息回對話框讓模型修

### 3. 完整 Mega-Prompt

```xml
<role>
你是一位資深全端工程師兼產品設計師，專長：
- Python web app（Flask / FastAPI、Jinja2、Bootstrap）
- LLM API 串接（Google Gemini、OpenAI、Anthropic、本地 Ollama）
- 前端視覺化（FullCalendar.js、Chart.js）
- PDF 生成（WeasyPrint、ReportLab）

你的輸出風格：架構先說、code 後給；
重要設計決策附「為什麼」一行；
trade-off 直接列出選項與推薦，不裝懂、不討好。
</role>

<context>
這份 prompt 的使用者是台灣學生（工工系二年級，Windows 11 + Python 3.11+）。
他用 Obsidian 維護 Zettelkasten 知識庫。

目前痛點：每週花約 140 分鐘把腦中事務手動貼進 ChatGPT 跑規劃 prompt。
他想把這個流程自動化成一個本地 web app。

他已有三份 markdown（會作為軟體的內部模板與設定）：
1. 主規劃 prompt 模板：Prompt-腦清空與排程.md
2. 臨時重排 prompt 模板：Prompt-臨時重排.md
3. 個人基線檔：個人基線檔.md（共 11 節，含主科週目標）

請用繁體中文輸出所有說明文字；code 內註解可用繁中或英文皆可。
</context>

<objective>
設計並交付一份**完整可執行**的 Python web app codebase，
讓使用者執行 `python app.py` 後瀏覽器自動打開 localhost:port，
看到 gentelella 風格首頁，能完成以下使用流程：

主流程（≤ 5 分鐘完成）：
1. 「主規劃頁」填寫腦袋大清空 + 能量偏差 + 核心目標 + 規劃範圍
2. 軟體載入 baseline YAML、套主規劃 prompt 模板、呼叫 LLM
3. 「結果頁」渲染分類表、完整時段表、被砍清單
4. 結果頁含 chat-style refine 框，可多輪請模型微調（如：「把週三午後換成線代」）
5. 滿意後點「匯出 PDF」
6. 結果自動進歷史紀錄

次要功能：
- 「臨時重排頁」獨立流程，套用 Prompt-臨時重排 模板
- 「設定頁」UI 表單欄位編輯 baseline 全 11 節（不手改 YAML）
- 「歷史紀錄頁」列出過往規劃、可重看、可重匯 PDF
- 視覺化：
  - 行事曆視圖（FullCalendar.js，週/日方塊呈現時段表）
  - 統計圖（Chart.js 餅圖：本週各活動時間佔比）
  - 進度追蹤圖（條狀：本週主科分配時數 vs baseline 第 11 節設定目標）
- LLM provider 切換：主 Gemini Pro，backup Ollama（推薦 qwen2.5:14b）

成功標準：
1. python app.py → 自動開瀏覽器、不卡關
2. 切換 LLM provider 只需改 .env，主邏輯不動
3. baseline YAML schema 對應 個人基線檔.md 全 11 節
4. PDF 版面整齊可印
5. README 第一次跑不卡（含 Gemini API key 取得、Ollama 安裝）
</objective>

<rules>
- 技術棧：Flask + Jinja2 + Bootstrap（gentelella 主題）+ FullCalendar.js v6 + Chart.js v4
- LLM SDK：
  - Gemini: google-generativeai 官方 SDK
  - Ollama: HTTP API（預設 http://localhost:11434）
- API key 從 .env 讀（環境變數 GEMINI_API_KEY）；provider 切換用 LLM_PROVIDER（gemini 或 ollama）
- 架構強制 LLM provider 抽象層：LLMClient interface + GeminiClient + OllamaClient 實作；未來加 OpenAI/Claude 只新增一個檔案
- Prompt 模板放獨立 .md 檔（從 <input_data> 接收），不寫死 Python 程式碼
- Baseline 用 YAML 儲存（人類可讀、Git 友善），不用資料庫
- 歷史紀錄用 SQLite 單檔（推薦）或 JSON（AI 二選一並說明理由）
- Refine 對話歷史只存當次規劃 session 內；session 結束時把「最終版本」存進歷史紀錄
- 進度追蹤資料源 = 規劃中分配的時數（不追蹤實際完成）
- 主科週目標時數來自 baseline 第 11 節
- 所有路徑用相對路徑，相容 Windows（注意 UTF-8 編碼、路徑分隔符）
- 程式碼用 type hints；函式 < 50 行；module 分層清楚
- README 必含：環境需求、安裝步驟、Gemini API key 取得方式、Ollama 安裝指令（ollama pull qwen2.5:14b）、第一次啟動指令、常見錯誤排除
- PDF 工具：WeasyPrint 或 ReportLab 二選一並說明理由
- Refine 多輪對話 token 節流：自動 summarize 舊輪次避免 context 爆炸
- gentelella template 整合方式必須明確（CDN / 下載哪些檔放 static/）
</rules>

<methodology>
強制分階段輸出，先架構後 code。

階段 A：架構設計（先給，等使用者確認再進 B）

A1. 系統架構圖（文字描述：modules、資料流、外部依賴）
A2. 檔案結構樹（完整 directory tree）
A3. 資料模型
   - baseline YAML schema（對應 個人基線檔.md 全 11 節）
   - 歷史紀錄 schema（SQLite 或 JSON）
   - Refine 對話 schema
A4. LLM provider 抽象層
   - LLMClient interface 定義
   - GeminiClient、OllamaClient class 設計
   - Factory + .env 設定機制
A5. 主要頁面流程圖（4 頁）
   - 主規劃頁（含 refine chat 流程）
   - 臨時重排頁
   - 設定頁（baseline 編輯 UI）
   - 歷史紀錄頁
A6. 視覺化資料流（FullCalendar、Chart.js 餅圖、進度條 各餵什麼資料）

階段 A 結尾必須加：「以上為架構設計，請確認後我再交付完整 codebase。」

階段 B：完整 codebase（待 A 確認）

B1. 所有 .py 檔（含 type hints、必要 docstring）
B2. 所有 templates/*.html（Jinja2 + gentelella class）
B3. static/ 必要 css / js
B4. prompt 模板檔（從 <input_data> 接收的使用者三份 md 內容）
B5. requirements.txt
B6. .env.example
B7. README.md（完整安裝與第一次使用流程，含 Ollama 章節）
B8. baseline 範例 YAML（含註解、對應使用者提供的個人基線檔）

階段 C：部署 checklist + 擴充建議

- 第一次啟動可能踩到的坑與解決方式
- Ollama 切換步驟（含模型下載 + .env 改值）
- 後續擴充方向（手機 PWA、Google Calendar 同步、自動排程觸發）
</methodology>

<examples>
LLM provider 抽象層設計風格參考（以下為 Python 程式碼示意）：

# llm/base.py
from abc import ABC, abstractmethod
from typing import Iterator

class LLMClient(ABC):
    @abstractmethod
    def complete(self, prompt: str, **kwargs) -> str:
        """單次補完"""
        ...

    @abstractmethod
    def chat(self, messages: list[dict], **kwargs) -> str:
        """多輪對話 refine 用"""
        ...

# llm/gemini.py
class GeminiClient(LLMClient):
    def __init__(self, api_key: str, model: str = "gemini-1.5-pro"):
        ...

# llm/ollama.py
class OllamaClient(LLMClient):
    def __init__(self,
                 base_url: str = "http://localhost:11434",
                 model: str = "qwen2.5:14b"):
        ...

# llm/factory.py
def get_client() -> LLMClient:
    """從 .env LLM_PROVIDER 讀對應 client"""
    ...

軟體 entry point 風格示意：

# app.py
if __name__ == "__main__":
    import webbrowser, threading
    threading.Timer(1.0, lambda: webbrowser.open("http://127.0.0.1:5000")).start()
    app.run(host="127.0.0.1", port=5000, debug=False)

讓使用者執行 python app.py 直接跑起來、自動開瀏覽器。
</examples>

<input_data>
三份模板來源（請使用者於正式跑這份 prompt 時，把以下三檔完整內容貼進來）：

1. 主規劃 prompt 模板：[貼上 Prompt-腦清空與排程.md 全文]
2. 臨時重排 prompt 模板：[貼上 Prompt-臨時重排.md 全文]
3. 個人基線檔結構參考：[貼上 個人基線檔.md 全文，包含第 11 節 主科週目標]

LLM 設定：
- 主要 provider：Google Gemini Pro（gemini-1.5-pro 或 gemini-2.0-pro）
- 備援 provider：Ollama（推薦模型 qwen2.5:14b）
- 環境變數：
  - GEMINI_API_KEY
  - LLM_PROVIDER（gemini 或 ollama）

視覺風格參考：
- gentelella admin template: https://github.com/ColorlibHQ/gentelella
- FullCalendar v6
- Chart.js v4

執行環境：
- Windows 11
- Python 3.11+
- 不需要 docker；venv + pip install -r requirements.txt
- Ollama 安裝（可選）：https://ollama.com/download
</input_data>

<output_format>
請依下列結構輸出 Markdown：

# 階段 A：架構設計

## A1. 系統架構圖
（文字描述）

## A2. 檔案結構樹
（用 markdown 程式碼區塊呈現完整目錄樹）

## A3. 資料模型
- baseline YAML schema（11 節）
- 歷史紀錄 schema（含 SQLite vs JSON 選擇理由）
- Refine 對話 schema

## A4. LLM Provider 抽象層
- class 定義
- 設計理由

## A5. 主要頁面流程
- 主規劃頁（含 refine chat 流程）
- 臨時重排頁
- 設定頁
- 歷史紀錄頁

## A6. 視覺化資料流
- 行事曆視圖
- 餅圖
- 進度追蹤圖

結尾必加：以上為架構設計，請確認後我再交付完整 codebase。

# 階段 B：完整 codebase（待使用者確認 A 後輸出）

# 階段 C：部署 checklist + 擴充建議（待 A 確認後輸出）
</output_format>

<self_check>
階段 A 完成前自我驗證：
- [ ] LLM provider 抽象支援 Gemini + Ollama 切換，沒有寫死？
- [ ] baseline YAML schema 對應 個人基線檔.md 全 11 節（含第 11 主科週目標）？
- [ ] 主規劃流程涵蓋：填表 → load baseline → 組 prompt → 呼叫 LLM → 渲染 → refine chat → PDF？
- [ ] Refine 對話歷史只存當次 session，最終版本進歷史紀錄？
- [ ] 視覺化三個視圖的資料來源都有明確說明？
- [ ] 設定頁 UI 表單欄位對應 baseline 11 節，無需手改 YAML？
- [ ] 進度追蹤資料源 = 規劃分配時數（非實際完成）？
- [ ] 檔案結構在 Windows 上跑得起來（路徑、UTF-8）？
- [ ] Ollama 切換指引有寫進 README？
- [ ] gentelella template 整合方式有寫明？
- [ ] PDF 工具選擇有附理由？
- [ ] Token 節流策略對應 refine 多輪場景？
</self_check>
```

### 4. 使用 Tips

> [!tip]
> - 用最強的模型跑（Opus 4.7 / Gemini 2.0 Pro / GPT-4o），小模型會吐不完整 codebase
> - **強制分階段**是 prompt 內建的；不要急著按「請繼續」，先 review 階段 A 架構
> - 階段 B 收到 code 後第一次跑必有 bug — 把錯誤訊息原文貼回對話框，模型會修
> - 想加新功能（如行事曆 Google 同步）→ 跑完整版穩定後，開新對話請 AI 在現有 codebase 上擴充，不要在這份 prompt 加

## Trade-offs

> [!warning] 雷與成本
> - **代碼量大**：完整版含 calendar / chart / chat refine / 設定 UI / PDF / 歷史，AI 一次吐約 2500-4000 行；分階段 review 仍是大工程
> - **Refine 多輪會疊 token**：Gemini 1.5 Pro 免費額度有 rate limit，refine 多了可能撞牆 → prompt 內已要 AI 加 summarize 節流
> - **第一次跑必 debug**：依賴庫版本、Windows 路徑、UTF-8 編碼問題；預留 1-3 小時 debug 時間
> - **gentelella 不是 pip 套件**：需要從 GitHub clone 或 download，把 static assets 放到 Flask static 路徑

## 我的實測

> [!todo] 待補
> （第一次跑完之後回來寫：階段 A 架構是否合理、階段 B code 缺什麼、第一次啟動踩到哪些坑、Ollama 切換是否真的順）

## 相關

- [[萬能Mega-Prompt 模板]] — 本卡的格式來源
- [[Prompt-腦清空與排程]] — 軟體要實作的主規劃模板
- [[Prompt-臨時重排]] — 軟體要實作的臨時重排模板
- [[個人基線檔]] — 軟體要讀寫的資料源
- [[MOC-Prompt工程]]

## 來源

- 2026-05-18 對話：把手動 prompt 工作流升級為自動化軟體的設計階段
- 格式參考：[[萬能Mega-Prompt 模板]] 9 段結構 + [[10_概念卡/90% 的「提示詞技巧」都是迷信]] 用語稽核
