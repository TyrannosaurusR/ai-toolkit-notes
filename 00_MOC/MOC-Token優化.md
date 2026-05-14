---
title: MOC - Token 優化
type: MOC
topics: [token優化]
created: 2026-05-11
---

# MOC - Token 優化

> 怎麼讓同樣的事更便宜更快。涵蓋 prompt 壓縮、快取、輸出加速。

## 主要方向

### 1. Prompt 壓縮
減少進入模型的 token 數，同時保留意圖。
- [[Prompt壓縮的5種寫法]]
- [[簡潔指令-Summarize比一段話更好]]

### 2. 快取策略
重複內容不要重打。
- [[Semantic-Caching降73%成本]]
- [[Prompt-Caching靜態前綴重用]]

### 3. 輸出加速
讓模型「寫得快」。
- [[Skeleton-of-Thought加速2.39x]]

### 4. 上下文管理
避免上下文爆炸後反而劣化。
- [[3000-token-是推理劣化的門檻]]
- [[150-300字是甜蜜點]]

## 重要原則

- **Token = 成本 + 延遲**：每個多餘字都在花錢。
- **3000 token 後推理品質開始劣化**：不是塞越多越好。
- **指令越短效果可能越好**：「Summarize:」常常 = 一整段解釋。

## 待開卡（從 Inbox 撈）

- [ ] Adaptive prompting（自動優化 prompt）
- [ ] Instruction tuning vs system message 取捨

## 參考資料

- [LLM Token Optimization - Redis](https://redis.io/blog/llm-token-optimization-speed-up-apps/)
- [Token Optimization Strategies - dasroot.net](https://dasroot.net/posts/2026/04/token-optimization-llm-costs-prompt-engineering/)
- [How to Optimize Token Efficiency - Portkey](https://portkey.ai/blog/optimize-token-efficiency-in-prompts/)
