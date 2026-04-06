# CoverPilot

用于设计验证的 coverage intelligence。

## 问题定义

Coverage closure 是验证流程里最耗时的工作之一。团队通常会遇到：

- 大量未覆盖的 bin 和场景
- 很难判断某个 hole 为什么一直存在
- 很难把 coverage hole 映射回 RTL 结构或功能意图
- 不确定下一步应该补测试、改约束、改 monitor，还是改 coverage model

传统 coverage report 能告诉工程师“缺了什么”，但通常不能可靠地告诉你“下一步该做什么”。

## 为什么 AI 有帮助

Coverage 分析很适合作为 AI 辅助目标，因为它天然结合了：

- 结构化数据（coverage report、层级、test metadata）
- 半结构语义（feature 名称、RTL block、coverage model）
- 大量重复性的工程判断

AI 的价值在于把原始 coverage 输出整理成更可解释、更可排序、更可行动的建议。

## 核心思路

**CoverPilot** 是一个 coverage intelligence agent，它可以：

- 分析 coverage hole
- 把 hole 映射到 RTL hierarchy 和 feature context
- 区分 black-box / white-box 的 coverage reasoning
- 优先排序最有意义的 gap
- 给出更可能有效的 closure 建议

## 典型输入

- line / toggle / branch / FSM coverage
- functional coverage report
- test metadata 与 pass/fail 历史
- RTL hierarchy 与 module owner 信息
- feature mapping 或 requirement tag
- 历史 closure 备注与 known exclusions

## 典型输出

- 按优先级排序的 coverage-hole 列表
- 每个 hole 可能关联的 RTL block
- hole 持续存在的可能原因
- 建议的下一步动作
- closure 进展摘要

## 例子：AI 可辅助的能力

- “这 5 个未覆盖 bin 很可能都和 DMA descriptor 的 burst mode corner case 有关。”
- “缺失 hit 主要集中在 AXI write-response path 下方的逻辑。”
- “这个 hole 更像是 stimulus 约束过严，而不是 checker 缺失。”
- “下一组最值得试的实验是 test A、C、F，并放宽 constraint X。”

## 工程挑战

- coverage point 和 feature intent 之间的映射经常不完整
- 有些 coverage hole 本身噪声很大、价值很低
- 很难区分 unreachable hole 和 simply under-tested hole
- coverage report 到验证动作之间常常缺少中间推理层

## 评估指标

- closure 时间是否缩短
- 工程师采纳了多少 AI 建议
- hole 到 RTL / feature 的映射是否足够准确
- 手工 coverage triage 的工作量是否下降

## References

### 学术参考

- Y.-T. Ho, S.-Y. Huang, and J.-Y. Jou, “Acceleration of coverage closure using machine learning techniques in functional verification,” *IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems*, 2022.
- T. B. Preußer, “Functional coverage closure using reinforcement learning,” *arXiv*, 2024.

### 工程 / 工具参考

- Verification Academy – Coverage — <https://verificationacademy.com/topics/coverage/>
- UCIS / coverage reporting workflows in mainstream simulators

## 为什么这个方向值得做

CoverPilot 是最适合近期落地的方向之一，因为 coverage 数据本来就在大多数 DV 环境里存在，而“更快 closure”这件事也最容易向团队解释价值。