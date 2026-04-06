# TestForge RL

面向 regression optimization 的强化学习 / 自适应测试选择方向。

## 问题定义

回归资源永远有限，但测试集合通常越来越大：

- 不是所有 test 都同样有价值
- 很多 test 重复覆盖类似区域
- 计算预算、回归窗口、license、farm 资源都有限
- 团队希望更快看到“最重要的失败”和“最有效的 coverage 增长”

## 为什么 AI 有帮助

测试选择与调度本质上就是优化问题：

- 在预算受限下最大化 coverage 增长
- 尽快暴露新的失败类型
- 减少重复性的低价值运行

这类问题天然适合 RL 或更广义的 adaptive selection 策略。

## 核心思路

**TestForge RL** 不一定执着于“必须是强化学习”，更准确地说，它是一个预算感知的 regression intelligence 层，用来：

- 评估各类 test 的历史价值
- 根据当前 coverage / failure 状态选择更值得运行的 test
- 动态调整 test 优先级
- 在有限预算下提升验证效率

## 典型输入

- regression 历史
- test metadata
- pass/fail 历史与 novelty 信息
- coverage 变化趋势
- runtime / farm cost / queue pressure
- 当前 release / debug 阶段的策略偏好

## 典型输出

- test 优先级列表
- 推荐先跑 / 后跑 / 暂缓运行的测试组
- 预算内的最优或近似最优回归组合
- 对收益与风险的解释说明

## 例子：AI 可辅助的能力

- “在当前预算下，这 20 个测试最可能带来新的 coverage 增量。”
- “这组 test 在过去 10 次回归中高度重复，短期可以降权。”
- “若目标是尽快暴露失败，建议优先运行历史 novelty 较高的测试子集。”
- “当前 smoke + directed + 3 个 stress test 的组合性价比最高。”

## 工程挑战

- 奖励函数怎么定义才合理
- 历史数据分布可能偏斜
- coverage 增益与 debug 价值不总是同一个目标
- 需要避免宣称 RL 已是 DV 标准答案

## 评估指标

- 相同预算下 coverage 是否更高
- 是否更快发现关键失败
- 平均回归成本是否下降
- 工程师是否能理解并信任调度建议

## References

### 学术参考

- regression test selection / prioritization 相关研究
- RL for coverage closure 或测试调度的邻近工作

### 工程 / 工具参考

- RLlib / Ray 等 RL 框架
- 现有 regression manager / scheduler 工作流
- test history analytics pipelines

## 为什么这个方向值得做

TestForge RL 是一个中期很有吸引力的方向，尤其适合拥有大规模回归、明确 coverage 目标、且强烈关注 compute efficiency 的团队。