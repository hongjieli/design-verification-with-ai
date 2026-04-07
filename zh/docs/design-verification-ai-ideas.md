# AI 辅助设计验证：主题化工程思路

本文尝试以更结构化的方式看待 **AI-assisted design verification (DV)**。

与其把“AI for DV”理解成一个单一、笼统、无所不能的智能助手，不如把它拆成一组彼此相关、但可以独立成立的工程方向。每个方向都对应验证流程中的真实痛点，因此既可以单独作为项目、原型或产品方向，也可以在更大系统里互相连接。

其中，最初项目矩阵直接包含了五个方向：

- CoverPilot
- RegMatrix
- TestForge RL
- DVCore
- WaveScope MCP

为了让整个组合更完整，另外补入了三个紧邻且具有真实工程支撑的方向：

- FailSense
- AssertMind
- TraceLens

整体结构可以概括为：

1. Overview
2. CoverPilot
3. RegMatrix
4. TestForge RL
5. DVCore
6. WaveScope MCP
7. FailSense
8. AssertMind
9. TraceLens
10. Conclusion

这八个方向合在一起，覆盖了 DV 工作流中的大部分关键活动：从 agent 基础设施、规格文档理解，到 coverage 优化、回归失败 triage、waveform debug 与 traceability 管理。

---

# 第 1 章：Overview —— 为什么 AI 辅助设计验证值得认真做

设计验证团队每天都在处理大量工程数据：

- regression logs
- coverage reports
- assertion 与 protocol checker 输出
- test metadata
- waveform traces
- register 与 specification 文档
- bug history 与 debug note

真正困难的地方往往不是“生成更多数据”，而是把这些数据转化成工程决策：

- 哪些 failure 才是真正新的？
- 哪些 coverage hole 最值得优先处理？
- 规格里哪些隐含约束应该转成验证动作？
- 在预算有限时，哪些 tests 应该先跑？
- 波形究竟从哪里开始偏离预期？
- 多个 AI 辅助流程该如何被组织成一套完整系统？

这正是 DV 很适合引入 AI 的原因。

AI 最有价值的角色，不是替代验证工程师，也不是自动做 signoff judgment，而是作为 **copilot** 来帮助完成：

- summarization（摘要）
- clustering（聚类）
- prioritization（排序与优先级判断）
- traceability（链路关联）
- recommendation（建议）
- workflow orchestration（工作流编排）

目标不是让工程师退出环路，而是减少重复分析劳动，让团队能更快从原始 artifact 走到有依据的行动。

本文把这个总体愿景拆成八个方向：

1. **CoverPilot** —— coverage intelligence
2. **RegMatrix** —— register/spec intelligence
3. **TestForge RL** —— 强化学习驱动或自适应测试选择
4. **DVCore** —— AI-native DV 的 agent foundation 与 orchestration layer
5. **WaveScope MCP** —— waveform-aware debug intelligence
6. **FailSense** —— regression failure intelligence
7. **AssertMind** —— assertion / formal intelligence
8. **TraceLens** —— spec-to-test traceability intelligence

每个方向都可以独立存在；但当它们被连接起来时，才能形成真正实用的 AI-assisted DV stack。

---

# 第 2 章：CoverPilot —— 设计验证中的 Coverage Intelligence

## 问题定义

Coverage closure 是验证里最耗时的工作之一。团队经常要面对：

- 大量未覆盖的 bins 与 scenarios
- 很弱的可解释性：为什么这个 hole 还在？
- 很难把 coverage hole 映射回 RTL 结构或 feature intent
- 不知道下一步应该补 test、调 constraint、改 monitor，还是更新 coverage model

传统 coverage report 能告诉你“缺了什么”，但很少能可靠回答“接下来最应该做什么”。

## 为什么 AI 有帮助

Coverage 分析很适合作为 AI 辅助场景，因为它结合了：

- structured data（coverage report、hierarchy、test metadata）
- partial semantics（feature name、RTL block、coverage model 命名）
- 大量重复出现的工程判断模式

AI 可以把原始 coverage 输出转化成更容易排序、解释与行动的建议层。

## 核心思路

**CoverPilot** 是一个 coverage intelligence agent，它可以：

- 分析 coverage holes
- 把 hole 映射到 RTL hierarchy 与 feature context
- 区分 black-box 与 white-box 的 coverage reasoning
- 找出真正值得优先处理的 gap
- 建议更可能有效的 closure 动作

## 典型输入

- line / toggle / branch / FSM coverage
- functional coverage reports
- test metadata 与 pass/fail 历史
- RTL hierarchy 与 module ownership
- feature mapping 或 requirement tags
- 以往 closure note 与 known exclusions

## 典型输出

- 按优先级排序的 coverage-hole 列表
- 每个 hole 可能关联的 RTL block
- hole 持续存在的可能原因
- 建议的下一步动作
- closure progress summary

## AI 可辅助的例子

- “这 5 个 uncovered bins 看起来都与 DMA descriptor 的 burst-mode corner case 相关。”
- “缺失 hit 主要集中在 AXI write-response path 下方逻辑。”
- “这个 hole 更像是 stimulus 被 over-constrained，而不是 checker 缺失。”
- “下一组最值得试的实验是 tests A、C、F，并放宽 constraint X。”

## 工程挑战

- coverage point 与 feature intent 的映射往往不完整
- 有些 holes 本身噪声大、价值低
- 很难区分 unreachable hole 与 under-tested hole
- coverage report 和实际验证动作之间缺少中间推理层

## 评估指标

- closure 时间是否缩短
- 工程师采纳的建议数量与质量
- hole 到 RTL / feature 的映射准确率
- 手工 coverage triage 工作量是否下降

## 相关参考

### Academic references

- Y.-T. Ho, S.-Y. Huang, and J.-Y. Jou, “Acceleration of coverage closure using machine learning techniques in functional verification,” *IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems*, 2022.
- T. B. Preußer, “Functional coverage closure using reinforcement learning,” *arXiv*, 2024.

### Engineering / tool references

- Verification Academy – Coverage — <https://verificationacademy.com/topics/coverage/>
- UCIS 与主流 simulator 的 coverage workflow

## 为什么这个方向值得做

CoverPilot 是近期最容易落地的方向之一，因为 coverage 数据在大多数 DV 流程中本来就存在，而“更快做完 closure”也是团队最容易理解和接受的价值主张之一。

---

# 第 3 章：RegMatrix —— Register / Spec Intelligence

## 问题定义

寄存器验证看起来很结构化，但现实里依然很容易变得杂乱：

- spec 文档、表格、注释、脚本常常分散存在
- field 间依赖、约束、side effect 不一定写得清晰
- 把 spec 转成测试点和约束模型常常很花时间
- 很容易漏掉 mode interaction、reset behavior、access policy 等 corner case

## 为什么 AI 有帮助

这是一个很适合“半自动智能整理”而不是“完全自动生成”的领域：

- register / field 描述常带有一定结构
- 可以抽取 access type、reset value、dependency、behavior pattern
- 可以把文档语言转换成更接近 DV 动作的候选建议

## 核心思路

**RegMatrix** 是寄存器与规格文档的 intelligence layer，用于：

- 解析 spec / register 描述
- 提取 field 关系、依赖、约束与行为模式
- 组织成适合 DV 使用的结构化关系图
- 输出测试建议、corner case 建议与 coverage 建议

## 典型输入

- register spec / CSR 文档
- field 描述、access policy、reset value
- YAML / XML / IP-XACT / 内部表格导出
- 现有 RAL model 或 register scripts
- 相关 feature requirements

## 典型输出

- field dependency graph
- 可疑 spec 模糊点或冲突点
- candidate test scenarios
- 可派生的约束关系
- 建议补充的 checker / coverage points

## AI 可辅助的例子

- “这个 enable bit 和 mode field 有联动，建议增加 mode 切换下的 write/readback 测试。”
- “这些字段共享 reset dependency，但文档描述彼此不一致。”
- “这个只读字段可能受另一个 status event 间接影响，建议验证 side-effect update。”
- “基于 access type 与 dependency，建议补上 illegal access 与 reset-after-write 两类测试。”

## 工程挑战

- spec 文字经常模糊、不完整，甚至互相矛盾
- 并非所有 dependency 都能直接从文本里抽取
- 不能把它包装成“自动理解所有规格”的过度承诺
- 输出必须方便工程师 review 与修改，而不是一个黑盒结果

## 评估指标

- 是否发现真实缺失的寄存器测试点
- 是否减少人工阅读 / 整理 spec 的时间
- 是否提升 register verification completeness
- 工程师是否愿意把结果纳入现有 RAL / test-planning 工作流

## 相关参考

### Engineering / methodology references

- UVM 1.2 Reference Documentation — <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- IP-XACT / register metadata workflows
- PyVSC、NetworkX 等适合表示约束与依赖图的工程库

## 为什么这个方向值得做

RegMatrix 非常适合作为一个强 topic：它足够结构化，适合部分自动化；同时也足够痛，团队很容易感受到“多一层智能整理”带来的实际价值。

---

# 第 4 章：TestForge RL —— 回归优化与预算感知测试选择

## 问题定义

回归资源永远有限，而测试集合却会越来越大：

- 不是所有 tests 的价值都一样
- 许多 tests 覆盖的区域高度重叠
- compute budget、license、farm 资源、回归窗口都有限
- 团队希望尽快看到“最重要的 failure”与“最有效的 coverage 增量”

## 为什么 AI 有帮助

测试选择与调度本质上是优化问题：

- 在预算受限下最大化 coverage gain
- 尽早发现真正新的 failures
- 减少重复运行低价值测试

因此，这类问题天然适合 reinforcement learning，或者更广义的 adaptive selection / prioritization 策略。

## 核心思路

**TestForge RL** 并不一定执着于“必须是 RL”；更准确地说，它是一个预算感知的 regression intelligence layer，用来：

- 评估 tests 的历史价值
- 根据当前 coverage / failure 状态选择更值得运行的 tests
- 动态调整 test 优先级
- 在有限预算下提升整体验证效率

## 典型输入

- regression history
- test metadata
- pass/fail 历史与 novelty 信息
- coverage 变化趋势
- runtime / farm cost / queue pressure
- 当前 debug 阶段或 release 阶段的策略偏好

## 典型输出

- test priority list
- 建议先跑 / 后跑 / 暂缓运行的测试组
- 预算内的最优或近似最优回归组合
- 对收益与风险的解释

## AI 可辅助的例子

- “在当前预算下，这 20 个测试最可能带来新的 coverage 增量。”
- “这组 tests 在过去 10 次回归里高度重复，短期可降权。”
- “若目标是尽快暴露 failures，应优先跑历史 novelty 较高的测试子集。”
- “当前 smoke + directed + 3 个 stress tests 的组合性价比最高。”

## 工程挑战

- reward function 很难定义得恰到好处
- 历史数据分布可能有偏
- coverage gain 与 debug value 不一定是同一个目标
- 需要避免宣称 RL 已经是 DV 的标准答案

## 评估指标

- 相同预算下 coverage 是否更高
- 是否更快发现关键 failures
- 平均回归成本是否下降
- 工程师是否能理解并信任调度建议

## 相关参考

### Academic references

- regression test selection / prioritization 相关研究
- RL 用于 coverage closure 或 test scheduling 的邻近工作

### Engineering / tool references

- RLlib / Ray 等 RL 框架
- 现有 regression manager / scheduler workflows
- test history analytics pipelines

## 为什么这个方向值得做

TestForge RL 是一个很有吸引力的中期方向，尤其适合拥有大规模回归环境、明确 coverage 目标、且强烈关注 compute efficiency 的团队。

---

# 第 5 章：DVCore —— AI-Native DV 的 Agent Foundation

## 问题定义

如果没有统一基础设施，AI 在 DV 里很容易变成一堆彼此断开的 demo：

- 一个工具看 logs
- 一个工具看 coverage
- 一个工具看 spec
- 一个工具调脚本
- 但它们之间没有统一 memory、context、task routing 与 observability

这样得到的并不是“平台”，而只是一堆零散工具。

## 为什么 AI 需要这一层

DV 需要的不只是单个 AI 模型，而是一整套系统去完成：

- tool invocation
- context memory
- artifact passing
- task decomposition 与 subagent routing
- multi-step reasoning 与 result synthesis
- engineer-facing execution trace

## 核心思路

**DVCore** 是验证场景下的 agent foundation，也就是“verification brain”。它负责：

- 连接不同 DV artifact 与工具
- 保存任务上下文与历史结论
- 把子任务路由到合适的 agent / tool
- 提供统一的工程师交互入口
- 把其他 topic 组织成可复用工作流

## 典型输入

- regression logs / reports
- coverage 数据
- spec / requirement 文档
- waveform / trace 信息
- bug history / debug notes
- 用户任务请求

## 典型输出

- step-by-step execution plan
- 子任务结果整合摘要
- 带引用的工程结论
- 下一步建议
- 可追踪的 workflow record

## AI 可辅助的例子

- “我先做 failure clustering，再让另一个 agent 做 coverage-gap 分析，最后汇总成 debug 建议。”
- “先从 spec 里抽出 constraints，再交给测试生成子流程。”
- “记录这个 failure cluster 的历史归因，供下轮回归复用。”
- “把 logs、coverage、requirements 与 owner 信息串成一个 engineer-facing summary。”

## 工程挑战

- 多工具编排很容易失控
- context 与 memory 需要精炼，而不是无限膨胀
- subagent 结果需要统一格式与可追踪性
- 最稳的表述应是 orchestration layer，而不是夸成业界成熟标准架构

## 评估指标

- 多步骤任务完成时间是否下降
- 工程师是否更快从原始 artifact 走到可执行结论
- 子代理协作是否稳定
- 不同 topic 是否能在统一平台里自然联动

## 相关参考

### Engineering / system references

- LangChain / graph-style orchestration frameworks
- OpenTelemetry / observability pipelines
- artifact pipeline 与 execution trace workflows

## 为什么这个方向值得做

DVCore 属于基础设施层。它让其他 topic 不再像分散实验，而更像一个真正能组合起来的 AI-assisted DV system。

---

# 第 6 章：WaveScope MCP —— 面向波形调试的 Debug Intelligence

## 问题定义

Waveform debug 是验证里最值钱、也最难自动化的环节之一：

- 数据量巨大
- 时间相关性复杂
- 根因往往隐藏在多层 event chain 之后
- 高度依赖资深工程师经验

## 为什么 AI 有帮助

AI 不必声称“自动看懂全部波形”，但它可以在很多子任务上显著提速：

- 提取关键信号变化与异常 events
- 识别 divergence window
- 总结 suspicious path
- 把长波形压缩成更适合工程师理解的结构化摘要

## 核心思路

**WaveScope MCP** 是一个 waveform-aware debug intelligence layer，重点不是替代 debug，而是：

- 从波形中提取高价值线索
- 缩小工程师真正需要看的时间窗口
- 把 debug 过程结构化
- 让波形分析与 log、assertion、spec 等 artifact 联动

## 典型输入

- waveform trace
- signal list / hierarchy
- 预期协议行为
- assertion failure location
- test metadata
- 相关 log / reports

## 典型输出

- divergence 时间窗口
- 可疑信号列表
- event sequence 摘要
- 可能的根因路径候选
- 与 assertion / spec / failure cluster 的关联说明

## AI 可辅助的例子

- “在 12.43us 到 12.58us 之间，req/ack 时序开始偏离预期。”
- “第一次异常传播出现在 FIFO full 与 backpressure handshake 组合场景。”
- “建议优先查看这 6 个信号，而不是整个 block 的全部波形。”
- “该异常与上一轮 regression 的 cluster-3 高度相似。”

## 工程挑战

- 波形理解是高难度问题，不能过度承诺
- 当信号语义或上下文不足时，误判风险较高
- 数据体量大，对预处理与索引要求高
- 更稳的 framing 是 debug acceleration，而非全自动 root-cause engine

## 评估指标

- 工程师定位问题时间是否缩短
- 是否能更快缩小可疑时间窗口与信号集合
- AI 摘要对真实 debug 是否有帮助
- 与 assertion / failure triage 联动后是否更实用

## 相关参考

### Engineering / tool references

- waveform viewers / trace databases
- debug scripts / event extraction pipelines
- protocol checker outputs

## 为什么这个方向值得做

WaveScope MCP 不一定是最先落地的项目，但它是长期战略价值最高的方向之一，因为资深工程师大量时间都消耗在 waveform debug 上。

---

# 第 7 章：FailSense —— Regression Failure Intelligence

## 问题定义

大规模 regression 失败之后，真正困难的通常不是“失败发生了”，而是：

- 哪些 failures 其实属于同一类问题？
- 哪些 failures 是新的？
- 哪些只是重复或噪声？
- 谁最适合优先处理？
- 哪个 cluster 才最值得先 debug？

人工 triage 很耗时，也容易不一致。

## 为什么 AI 有帮助

Failure triage 是 AI 很强的应用场景，因为它天然包含：

- 大量文本 / log 信息
- 可聚类的相似模式
- 可以排序的 novelty 与 severity
- 高重复性的人工判断

## 核心思路

**FailSense** 是一个 regression failure intelligence layer，它可以：

- 聚类相似 failures
- 识别新型 failure
- 给出 owner hints
- 汇总 triage summary
- 把 failure 与历史记录、波形、assertion failure、bug note 联系起来

## 典型输入

- regression logs
- error messages / stack / assertion fail 文本
- test metadata
- 历史 failure clusters
- owner / module mapping
- bug database 线索

## 典型输出

- failure cluster 列表
- novelty / duplicate 标记
- owner / block hints
- triage summary
- 建议优先处理顺序

## AI 可辅助的例子

- “这 37 个 failures 可以归为同一 cluster，核心特征是 AXI write timeout。”
- “这次出现了一个之前回归中没见过的新型 failure signature。”
- “这些 failures 最可能归属 DMA scheduler block。”
- “建议先看 cluster-2，因为它影响范围最大且最像真实功能回退。”

## 工程挑战

- 相似 failure 不一定意味着同一根因
- log 质量差会显著影响聚类效果
- novelty 检测需要足够稳定的历史基线
- 输出必须帮助 triage，而不是制造额外噪声

## 评估指标

- triage 时间是否下降
- cluster 质量是否足够被工程师接受
- 是否更快识别真正的新问题
- 是否减少重复 debug

## 相关参考

### Academic references

- RTL regression failure triage / clustering 相关研究
- semantic similarity / defect clustering 邻近研究

### Engineering / methodology references

- UVM methodology artifacts
- regression log processing pipelines
- bug triage / clustering workflows

## 为什么这个方向值得做

FailSense 是 8 个 topic 里学术支撑最直接、最扎实的方向之一，也非常适合作为最早能给团队带来明显价值的项目。

---

# 第 8 章：AssertMind —— Assertion / Formal Intelligence

## 问题定义

Assertion 与 formal 工作很重要，但也经常非常费劲：

- property 写法可能不完整或含糊
- counterexample 分析耗时
- formal 结果不容易向更广泛团队解释
- 工程师常要在 spec、property、波形、失败 trace 之间来回切换

## 为什么 AI 有帮助

这个方向最适合 AI 扮演的角色不是“自动生成所有 assertion”，而是：

- 帮助解释 property 语义
- 帮助 review assertion completeness
- 总结 counterexample
- 把 formal 结果翻译成更适合工程沟通的语言

## 核心思路

**AssertMind** 是 assertion / formal intelligence layer，用于：

- review property 的结构与表达
- 解释 counterexample
- 帮助定位 assertion failure 的上下文
- 连接 formal 结果与 spec / waveform / debug artifacts

## 典型输入

- assertion / property 文本
- formal run 结果
- counterexample trace
- spec requirement
- 相关 waveform / debug note

## 典型输出

- assertion 解释摘要
- 可疑遗漏点
- counterexample 的工程化说明
- 建议补充的 property 方向
- formal result summary

## AI 可辅助的例子

- “这个 property 约束了握手完成，但没有覆盖 backpressure 下的保持条件。”
- “这个 counterexample 的核心是 reset release 后两拍内状态未稳定。”
- “这组 assertions 更适合作为 protocol compliance 层，而非 feature intent 层。”
- “建议增加一条覆盖 mode switch 期间 invalid request 的 property。”

## 工程挑战

- 不应把它包装成 autonomous assertion generator
- formal 语义非常敏感，错误解释成本高
- 输出必须允许工程师 review 与改写
- 更稳妥的 framing 是 review / explain / debug assist

## 评估指标

- property review 时间是否缩短
- counterexample 理解是否更快
- 是否发现真实 assertion gaps
- formal 结果是否更容易传播与复用

## 相关参考

### Engineering / tool references

- Verification Academy – Formal Verification — <https://verificationacademy.com/topics/formal-verification/>
- assertion / formal tool documentation

## 为什么这个方向值得做

AssertMind 是一个需要保守表达、但很实用的方向。最稳妥的定位不是“自动写 assertion”，而是“formal / property copilot for review, explanation, and debug assistance”。

---

# 第 9 章：TraceLens —— Spec-to-Test Traceability Intelligence

## 问题定义

缺少强 traceability 时，DV 知识很容易散落在：

- requirement 文档
- spec 章节
- test list
- coverage reports
- bug / debug notes
- 工程师的个人记忆里

这会直接带来几个问题：

- 很难回答“这个 requirement 是由谁、通过什么方式验证的？”
- 很难判断 coverage gap 是否对应真实 requirement gap
- 很难做 planning、audit 与 handoff

## 为什么 AI 有帮助

Traceability 问题非常适合 AI 作为“连接层”来处理：

- 在 requirement、spec、test、coverage、debug 之间建立弱关联
- 把零散信息整理成可读结构
- 帮助发现缺失链路

## 核心思路

**TraceLens** 是一个 traceability intelligence layer，用于：

- 连接 requirements 与 tests
- 把 coverage 与 feature intent 对齐
- 追踪 debug evidence 与验证结论
- 输出更适合 planning / review 的 traceability 视图

## 典型输入

- requirement 文档
- spec / feature 描述
- test plan / test metadata
- coverage reports
- bug history / debug notes

## 典型输出

- requirement-to-test 映射候选
- 缺失链接提示
- feature coverage 摘要
- traceability matrix
- 适合评审的验证状态视图

## AI 可辅助的例子

- “这个 requirement 在 test plan 中已有映射，但 coverage 证据不足。”
- “这组 tests 看起来都在验证同一个 feature，而另一个 feature 几乎没有验证证据。”
- “这个 bug 修复后，建议补一条 traceability link 到 regression suite X。”
- “当前 spec 第 4 节与 test plan 第 7 项之间存在明显缺口。”

## 工程挑战

- requirement 与 test 经常不是严格一一对应
- 文档语言模糊，容易造成误匹配
- 最稳的 framing 是 linkage assistant，而不是 fully automatic requirement mining system

## 评估指标

- requirement gap 是否能更快发现
- planning / review 是否更高效
- traceability matrix 的维护成本是否下降
- 工程师是否愿意使用建议映射作为起点

## 相关参考

### Engineering / methodology references

- UVM / test planning / coverage workflows
- requirement management 与 traceability tooling patterns

## 为什么这个方向值得做

TraceLens 的学术匹配相对间接，但工程故事很强。它最适合被描述成 requirements、tests、coverage 与 debug evidence 之间的 traceability intelligence layer。

---

# 第 10 章：Conclusion —— 把 AI for DV 说清楚

AI-assisted design verification 最稳妥、也最有工程说服力的表达方式，不是“AI 将自动完成验证”，而是：

> AI in DV 最适合作为一套围绕真实验证 artifacts 构建的 copilot / assistant / orchestration stack。

它的核心目标是：

- 减少重复分析工作
- 缩短从原始数据到工程行动的反馈周期
- 帮助工程师在 coverage、failure、spec、assertion、waveform 与 traceability 之间更快建立联系

本文提出的 8 个 topic，不是为了把所有事情都变成一个超级助手，而是为了给 AI-assisted DV 提供一套更清晰、更可落地的项目地图：

- **CoverPilot**：coverage intelligence
- **RegMatrix**：register/spec intelligence
- **TestForge RL**：regression optimization
- **DVCore**：agent foundation
- **WaveScope MCP**：waveform debug intelligence
- **FailSense**：failure intelligence
- **AssertMind**：assertion/formal intelligence
- **TraceLens**：traceability intelligence

这些方向并不要求同时启动。它们完全可以按团队的痛点优先级分阶段推进：

- 短期：FailSense、CoverPilot、RegMatrix
- 中期：TestForge RL、TraceLens
- 长期：WaveScope MCP、DVCore 深度整合、AssertMind 深度协作

当这些能力逐渐组合起来时，AI 在 DV 中的角色就不再只是“写点脚本”或“帮忙总结日志”，而会变成一整套真正服务工程判断的辅助系统。
