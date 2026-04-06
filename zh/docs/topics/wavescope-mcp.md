# WaveScope MCP

面向 waveform-aware debug intelligence 的长期高价值方向。

## 问题定义

Waveform debug 是验证里最值钱、也最难被自动化的环节之一：

- 数据量巨大
- 时间相关性复杂
- 根因往往隐藏在很多 event chain 之后
- 高度依赖资深工程师经验

## 为什么 AI 有帮助

AI 不一定要“自动看懂整个波形”，但它可以在很多地方显著提速：

- 提取关键信号变化与异常 event
- 识别 divergence window
- 总结 suspicious path
- 把长波形转成更适合工程师理解的结构化摘要

## 核心思路

**WaveScope MCP** 是一个 waveform-aware debug intelligence 层，重点不是替代 debug，而是：

- 从波形中提取高价值线索
- 缩小工程师真正需要看的时间窗口
- 把 debug 过程结构化
- 让波形分析能和其他 artifact（log、assertion、spec）联动

## 典型输入

- waveform trace
- signal list / hierarchy
- expected protocol behavior
- assertion failure location
- test metadata
- 相关 log / report

## 典型输出

- divergence 时间窗口
- 可疑信号列表
- event sequence 摘要
- 可能的根因路径候选
- 与 assertion / spec / failure cluster 的关联说明

## 例子：AI 可辅助的能力

- “在 12.43us 到 12.58us 之间，req/ack 时序开始偏离预期。”
- “第一次异常传播出现在 FIFO full 与 backpressure handshake 的组合场景。”
- “建议优先查看这 6 个信号，而不是整个 block 的全部波形。”
- “该异常和前一轮 regression 中的 cluster-3 很相似。”

## 工程挑战

- 波形理解是高难度问题，不能过度承诺
- 信号语义和上下文不足时，误判风险高
- 数据体量大，对预处理和索引有要求
- 最稳的表达应是 debug acceleration，而不是全自动 root cause engine

## 评估指标

- 工程师定位问题所花时间是否下降
- 是否能更快缩小可疑时间窗口与信号集
- AI 摘要对真实 debug 是否有帮助
- 与 assertion / failure triage 结合后是否更实用

## References

### 学术参考

- waveform analysis / temporal pattern mining 邻近研究
- trace-aware debug 辅助相关工作

### 工程 / 工具参考

- waveform viewers / trace databases
- debug scripts / event extraction pipelines
- protocol checker outputs

## 为什么这个方向值得做

WaveScope MCP 不一定是最先落地的项目，但它是长期战略价值最高的方向之一，因为资深工程师时间大量消耗在 waveform debug 上。