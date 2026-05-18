---
title: MOC - Prompt 工程
type: MOC
topics: [prompt工程]
created: 2026-05-11
---

# MOC - Prompt 工程

> 怎麼讓模型「答得準」。涵蓋指令設計、推理引導、輸出控制。

## 主要方向

### 1. 推理引導
讓模型「想清楚再答」。
- [[Chain-of-Thought-CoT]]
- [[Tree-of-Thought-ToT]]
- [[Self-Consistency-多次採樣投票]]

### 2. 範例引導
給模型看例子比解釋更有效。
- [[Few-shot的選例策略]]
- [[Zero-shot vs Few-shot 何時切換]]

### 3. 角色與結構
- [[System-Prompt角色設定]]
- [[結構化輸出-JSON-Schema]]
- [[XML-Tag切分Prompt區段]]

### 4. 元提示
讓模型自己優化 prompt。
- [[Adaptive-Prompting自我優化]]
- [[Meta-Prompting]]

## 重要原則

- **明確 > 客氣**：「列出 3 個」比「請列出一些」效果好。
- **位置很重要**：重要指令放開頭與結尾，中間容易被忽略。
- **正面指令 > 負面指令**：「用繁體中文」比「不要用英文」可靠。
- **結構化輸入 → 結構化輸出**：用 XML/Markdown 區隔。

## 心法 / 破迷思

- [[10_概念卡/90% 的「提示詞技巧」都是迷信]]

## 場景模板

- [[萬能Mega-Prompt 模板]]
- [[ChatGPT-ADHD模式]]
- [[Prompt-腦清空與排程]] — 整合應用版（個人化、覆蓋全天時段）
- [[Prompt-臨時重排]] — 臨時插入事件的輕量重排版
- [[個人基線檔]] — 上述兩張 prompt 引用的個人基線設定
- [[Prompt-設計時間規劃軟體]] — 把上述工作流自動化成 web app 的設計 prompt

## 待開卡

- [ ] Constitutional AI 自我批評
- [ ] ReAct（Reason + Act）

## 參考資料

- [Prompt Engineering Guide 2026 - Lakera](https://www.lakera.ai/blog/prompt-engineering-guide)
- [Prompt Engineering Best Practices - DigitalOcean](https://www.digitalocean.com/resources/articles/prompt-engineering-best-practices)
