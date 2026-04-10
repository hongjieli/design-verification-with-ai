# RegCleanse

基于 regression 历史，识别那些长期几乎总是通过、贡献很低、但持续占用回归资源的 testcase。

## 问题定义
大型 regression 会不断累积历史 testcase。部分 testcase 曾经有价值，但现在几乎不 fail、几乎不带来新的 coverage 或 bug 信息，却仍然占用大量算力与排队时间。

## AI 能做什么
AI 可以结合 pass/fail 历史、coverage 贡献、bug 关联、feature 重叠度和运行成本，识别长期 low-yield 的 testcase，并为“降级执行、降低频率、仅在特定改动后运行、甚至移除”提供证据。

## 核心思路
**RegCleanse** 可以：
- 找出长期稳定通过且 bug yield 很低的 tests
- 分析 testcase 之间在 feature、coverage、failure profile 上的重叠度
- 推荐 retire / demote / weekly-only / on-change 等执行策略
- 标出虽然不常 fail、但仍然有独特保护价值的 tests
- 在 regression 精简前给出可解释的证据
