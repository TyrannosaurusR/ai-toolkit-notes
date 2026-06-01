---
title: Skeleton-of-Thought 加速 2.39x
type: 實作卡
topics: [token優化, prompt工程]
status: 待驗證
difficulty: 入門
created: 2026-05-11
---

## TL;DR

先讓模型生「大綱骨架」，再**平行**展開每一點，最後拼起來——可加速到 **2.39x**。

## 是什麼 (What)

Skeleton-of-Thought（SoT）是一種**改變生成方式**的 prompt 技巧。傳統 LLM 是 token-by-token 串行生成，整段文字寫完才能回給你。SoT 把過程拆成兩階段：

1. **Skeleton 階段**：模型先列出 3-7 個重點骨架（每點 5-15 字）
2. **Expansion 階段**：對每個骨架點**同時**發出獨立的 API call 展開

因為展開階段是平行的，總時間 ≈ 「最慢那一段」而不是「全部加起來」，所以快。

## 何時用 (When)

- ✅ **適合**：
  - 長文生成（報告、文章、教學）
  - 結構化內容（FAQ、條列說明、多面向比較）
  - 對「整體吐出時間」敏感的場景（使用者等回應）

- ❌ **不適合**：
  - 短回答（骨架成本 > 收益）
  - 強推理任務（拆開後失去脈絡，答案會變差）
  - 段落間有強連貫依賴（每段都要接前一段語意）

## 怎麼做 (How)

### Step 1：取得骨架

```
請列出回答以下問題的 3-7 個重點骨架，每點 5-15 字，用編號列出，不要展開：

問題：[使用者的問題]
```

### Step 2：平行展開每點

對骨架的每一點，**同時**送出：

```
你正在回答這個問題：[原問題]
完整骨架是：[Step 1 全文]

請只展開第 [N] 點：「[該點骨架]」
寫 2-3 段，與骨架其他點不重複。
```

### Step 3：組裝

把每點展開結果按骨架順序拼起來。可選：再用一個 LLM call 做「平滑潤飾」（會犧牲一些加速）。

### Code 概念（Python pseudo）

```python
import asyncio

async def sot(question):
    skeleton = await llm(f"列出骨架：{question}")
    points = parse_points(skeleton)

    expansions = await asyncio.gather(*[
        llm(f"展開第{i}點：{p}，骨架={skeleton}")
        for i, p in enumerate(points)
    ])

    return "\n\n".join(expansions)
```

## Trade-offs

- ✅ 延遲降低（論文最高 2.39x）
- ✅ 結構天然清晰（骨架先行）
- ✅ 可以邊展開邊串流給使用者（漸進顯示）
- ❌ **總 token 反而增加**（每次展開都要重貼骨架當 context）→ 省時間但**不省錢**
- ❌ 段落間連貫性變差
- ❌ 需要平行 API call 的基礎建設（async / threading）

## 我的實測

（還沒實測，跑過再回來補）
- 問題類型：
- 加速倍數：
- 品質變化：
- 踩到的坑：

## 相關

- [[MOC-Token優化]]
- [[MOC-Prompt工程]]
- [[Prompt壓縮的5種寫法]]
- [[Chain-of-Thought-CoT]] ← 對照組：CoT 是讓模型「慢但想得清楚」，SoT 是「快但拆開想」

## 來源

- 原論文：Ning et al., "Skeleton-of-Thought: Large Language Models Can Do Parallel Decoding" (ICLR 2024)
- [Prompt Engineering Guide 2026 - Lakera](https://www.lakera.ai/blog/prompt-engineering-guide)
