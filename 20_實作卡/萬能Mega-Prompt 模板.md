---
title: 萬能 Mega-Prompt 模板
type: 實作卡
topics:
  - prompt工程
  - 工具框架
status: 待驗證
difficulty: 入門
created: 2026-05-17
source: https://www.threads.com/@buildthink.ai/post/DYSIIZeD1vh
---

> [!summary] TL;DR
> 把 prompt 當**軟體需求文檔**寫 — 9 段 XML 結構 + 5 種場景套用，跨 Claude / GPT / Gemini 都有效。

## 是什麼 (What)

[buildthink.ai](https://www.threads.com/@buildthink.ai) 整理 **2025 年新加坡 Prompt Royale 第三屆四位冠軍**及 **Wharton Prompting Science Report 3** 後提出的共通框架：用 9 個 XML tag 區段把任務拆乾淨，等同於寫一份小型需求規格。

> [!note] 與姊妹卡的關係
> 本卡涵蓋原文第 4-6 項（模板 + 場景 + 心法）。前 3 項「被證偽的咒語 / Role-play / CoT / 示例數量」見 [[10_概念卡/90% 的「提示詞技巧」都是迷信]]。

## 何時用 (When)

- 適合：重要任務、需要可重複可靠輸出、跨團隊共享的 prompt
- 不適合：一次性閒聊、探索性提問（過度結構化反而綁手綁腳）

## 怎麼做 (How)

### 1. 萬能模板 — 9 段 XML 結構

| 段落 | 寫什麼 |
| ---- | ---- |
| `<role>` | 具體專家角色 + 資歷 |
| `<context>` | 背景、受眾、品牌聲音 |
| `<objective>` | 單一目標 + 成功標準 |
| `<rules>` | 硬規則（用肯定式） |
| `<methodology>` | 分步方法論 |
| `<examples>` | 2-3 個高質量示例 |
| `<input_data>` | 實際內容 |
| `<output_format>` | 精確格式要求 |
| `<self_check>` | 完成前自我驗證 |

可直接複製的骨架：

```xml
<role>
  （具體專家角色 + 資歷，例：資深 SaaS 文案，10 年 B2B 經驗）
</role>

<context>
  （背景、受眾、品牌聲音）
</context>

<objective>
  （單一目標 + 成功標準，例：產出 3 個版本，每版 80 字內，CTR 預期 > X%）
</objective>

<rules>
  - （用肯定式：要做什麼，而不是不要做什麼）
  - 
</rules>

<methodology>
  1. （分步驟說明怎麼做）
  2. 
</methodology>

<examples>
  <example>
    <input>...</input>
    <output>...</output>
  </example>
  （2-3 個高質量示例）
</examples>

<input_data>
  （實際要處理的內容貼這裡）
</input_data>

<output_format>
  （精確格式：欄位、長度、語氣、是否含標題等）
</output_format>

<self_check>
  完成前自我驗證：
  - [ ] 符合 <objective> 的成功標準？
  - [ ] 遵守所有 <rules>？
  - [ ] 格式符合 <output_format>？
</self_check>
```

> [!note] 設計直覺
> 本質 = 把 prompt 當**軟體需求文檔**寫。角色與目的分開、規則與方法分開、輸入與輸出分開 — 模型不用猜，自然不會幻覺。

### 2. 五種日常場景直接套用

> [!example] 寫作 — 強制引用降幻覺
> 先讓模型**逐字引用文檔段落並編號**，再寫答案時用 `[1]` 引用對應段落 → 顯著降低幻覺率。

> [!example] 編程 — Review 矩陣
> 用 `<review_criteria>` 嵌套 `<security>` `<performance>` `<maintainability>` 三個子標籤 → 要求每個發現給**嚴重等級 + 修復代碼**。

> [!example] 分析 — 變量鏈式技巧
> 每步輸出用**大寫命名**（例如 `CLUSTERS`）→ 後續步驟用 `[CLUSTERS]` 引用前一步結果 → 避免上下文遺漏。

> [!example] 頭腦風暴 — 強制多變體
> 結尾加上 `Give me 2 different prioritizations` → 強制產出多個排序方案，而不是收斂到單一答案。

> [!example] 學習 — 蘇格拉底模式
> 加上 `Your goal is to ask probing questions` → 防止模型直接講課，改成不斷反問引導思考。

### 3. 心法

> [!quote] 一個好的 prompt
> 不只是「問問題」，而是**設計模型的工作流程**。

## Trade-offs

> [!todo] 跑過再補
> - ✅ 優點：
> - ❌ 代價：

## 我的實測

> [!todo] 待補
> 挑一個場景跑過後再寫：哪幾段最有效、哪幾段可以省、與直接問的差距。

## 相關

- [[10_概念卡/90% 的「提示詞技巧」都是迷信]]
- [[MOC-Prompt工程]]

## 來源

- [90% 的「提示詞技巧」都是迷信 - @buildthink.ai](https://www.threads.com/@buildthink.ai/post/DYSIIZeD1vh)
