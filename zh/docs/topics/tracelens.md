# TraceLens

面向 spec-to-test traceability intelligence 的连接层方向。

## 问题定义

没有强 traceability 时，DV 知识很容易散落在：

- requirement 文档
- spec 章节
- 测试列表
- coverage report
- bug / debug note
- 工程师脑子里

这会导致：

- 很难回答“这个 requirement 被谁验证了？”
- 很难知道 coverage gap 是否对应真实 requirement gap
- 很难做 planning / audit / handoff

## 为什么 AI 有帮助

Traceability 的问题非常适合 AI 做“连接层”：

- 在 requirement、spec、test、coverage、debug 之间建立弱关联
- 把零散信息整理成可读结构
- 帮助发现缺失链路

## 核心思路

**TraceLens** 是一个 traceability intelligence 层，用来：

- 连接 requirements 与 tests
- 把 coverage 和 feature intent 对齐
- 追踪 debug evidence 与验证结论
- 输出更适合 planning / review 的 traceability 视图

## 典型输入

- requirement 文档
- spec / feature 描述
- test plan / test metadata
- coverage report
- bug history / debug notes

## 典型输出

- requirement-to-test 映射候选
- 缺失链接提示
- feature coverage 摘要
- traceability matrix
- 更适合评审的验证状态图

## 例子：AI 可辅助的能力

- “这个 requirement 在测试计划中有映射，但 coverage 证据不足。”
- “这组测试看起来都指向同一个 feature，而另一个 feature 没有明显验证证据。”
- “该 bug 修复后，建议补一条 traceability link 到 regression suite X。”
- “当前 spec 第 4 节与 test plan 第 7 项之间存在明显缺口。”

## 工程挑战

- requirement 与 test 之间经常不是严格一一对应
- 文档语言模糊，容易造成误匹配
- 最稳妥的方式是把它当作 linkage assistant，而不是 fully automatic requirement mining system

## 评估指标

- requirement 缺口发现是否更快
- planning / review 是否更高效
- traceability matrix 的维护成本是否下降
- 工程师是否愿意使用建议映射作为起点

## References

### 学术参考

- requirements traceability / test selection / software traceability 邻近研究
- data-centric verification workflow 相关工作

### 工程 / 工具参考

- UVM / test planning / coverage workflows
- requirement management and traceability tooling patterns

## 为什么这个方向值得做

TraceLens 的学术匹配相对间接，但工程故事很强。它最适合被描述成 requirements、tests、coverage、debug evidence 之间的 traceability intelligence layer。