# DVCore

AI-native DV 的 agent foundation 与 orchestration layer。

## 问题定义

如果没有统一基础设施，AI 在 DV 里很容易变成一堆彼此断开的 demo：

- 一个工具看 log
- 一个工具看 coverage
- 一个工具看 spec
- 一个工具能调脚本
- 但它们之间没有统一记忆、上下文、任务路由和可观测性

这样做出来的不是“平台”，只是“很多小工具”。

## 为什么 AI 需要这一层

DV 不只是需要单个 AI 模型，它更需要一个系统去完成：

- 工具调用
- 上下文记忆
- artifact 传递
- 任务拆分与子代理协作
- 多步骤推理与结果汇总
- 工程师可见的执行轨迹

## 核心思路

**DVCore** 是验证场景下的 agent foundation，也就是“verification brain”。它负责：

- 连接不同 DV artifact 与工具
- 保存任务上下文与历史结论
- 路由子任务到合适的 agent / tool
- 统一对工程师的交互入口
- 把其他 topic 组织成同一套工作流

## 典型输入

- regression log / report
- coverage 数据
- spec / requirement 文档
- waveform / trace 信息
- bug history / debug note
- 用户任务请求

## 典型输出

- 分步骤执行计划
- 子任务结果整合摘要
- 带引用的工程结论
- 下一步建议
- 可追踪的工作流记录

## 例子：AI 可辅助的能力

- “我先把失败分类，再让另一个 agent 做 coverage gap 分析，最后汇总成 debug 建议。”
- “从 spec 中抽取限制条件，并传给测试生成子流程。”
- “记录这个 failure cluster 的历史归因，供下次回归复用。”
- “把 logs、coverage、requirements 和 owner 信息串成一个 engineer-facing summary。”

## 工程挑战

- 多工具编排容易失控
- 上下文和记忆需要精简而不是无限膨胀
- 子代理结果需要统一格式与可追踪性
- 需要把它表达成 orchestration layer，而不是夸成业界已成熟的 multi-agent DV 标准架构

## 评估指标

- 多步骤任务完成时间是否下降
- 工程师是否更快从“原始 artifact”走到“可执行结论”
- 子代理协作是否稳定
- 不同 topic 能否在同一平台里自然联动

## References

### 学术参考

- data-centric verification pipeline 相关研究
- AI workflow orchestration / agent systems 邻近研究

### 工程 / 工具参考

- LangChain / graph-style orchestration frameworks
- OpenTelemetry / observability pipelines
- artifact pipeline / execution trace workflows

## 为什么这个方向值得做

DVCore 是基础设施层。它让其他 topic 不再像五个分散实验，而更像一个真正连得起来的 AI-assisted DV 系统。