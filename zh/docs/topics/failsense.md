# FailSense

面向 regression failure intelligence 的高支撑方向。

## 问题定义

大规模 regression 失败之后，真正难的往往不是“失败发生了”，而是：

- 哪些失败其实是同一类问题
- 哪些失败是新的
- 哪些只是噪声或重复
- 谁最适合先看
- 哪个 failure 最有优先级

人工 triage 很费时间，而且容易不一致。

## 为什么 AI 有帮助

Failure triage 是 AI 很强的应用场景，因为它天然包含：

- 大量文本 / log 信息
- 可聚类的相似模式
- 可以排序的 novelty 与严重性
- 重复性很高的人工判断

## 核心思路

**FailSense** 是一个 regression failure intelligence 层，它可以：

- 聚类相似失败
- 识别新型失败
- 给出 owner hint
- 汇总 triage 摘要
- 把 failure 与历史记录、波形、断言失败点连接起来

## 典型输入

- regression log
- error message / stack / assertion fail 文本
- test metadata
- 历史 failure cluster
- owner / module mapping
- bug database 线索

## 典型输出

- failure cluster 列表
- novelty / duplicate 标记
- owner / block hint
- triage summary
- 建议优先处理顺序

## 例子：AI 可辅助的能力

- “这 37 个失败可归为同一 cluster，核心特征是 AXI write timeout。”
- “这次出现了一个之前回归中没出现的新型 failure signature。”
- “这些失败最可能归属到 DMA scheduler block。”
- “建议先看 cluster-2，因为它影响面最广且最像真实功能回退。”

## 工程挑战

- 相似失败不一定是同一根因
- log 质量差时聚类效果会受影响
- novelty 检测需要历史基线
- 输出必须帮助 triage，而不是制造更多噪声

## 评估指标

- triage 时间是否下降
- cluster 质量是否足够被工程师接受
- 是否更快识别真正的新问题
- 是否减少重复 debug

## References

### 学术参考

- RTL regression failure triage / clustering 相关论文
- semantic similarity / defect clustering 邻近研究

### 工程 / 工具参考

- UVM methodology artifacts
- regression log processing pipelines
- bug triage / clustering workflows

## 为什么这个方向值得做

FailSense 是 8 个 topic 里学术支撑最直接、最扎实的方向之一，也很适合作为最早期就能给团队看到价值的项目。