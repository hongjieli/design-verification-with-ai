# Academic Supporting Papers for AI-Assisted Design Verification（中文摘要版）

这一页的目标，是把英文版学术支撑页的用途完整保留下来：

- 说明 AI-assisted DV 并不是没有文献基础
- 明确哪些 topic 的学术支撑更强，哪些更多依赖工程支撑
- 帮助读者建立一套“证据层级”而不是平均用力地包装所有方向

## 哪些 topic 学术支撑最强

从当前材料看，支撑最直接的通常是：

1. **FailSense**
   - regression failure triage / clustering 与 RTL debug 相关性最强
2. **CoverPilot**
   - coverage closure acceleration、coverage guidance 有较直接邻近研究
3. **TestForge RL**
   - test prioritization / coverage optimization / RL 方向较容易找到方法学支撑

## 哪些 topic 更偏“工程强、论文弱”

- **DVCore**：更像 orchestration layer / platform foundation，学术支撑偏 pipeline / data-centric verification
- **WaveScope MCP**：方向很有价值，但“自动波形理解”不能过度承诺
- **TraceLens**：工程价值强，学术映射偏间接
- **AssertMind**：更适合作为 review / explain / debug assist，而不是 autonomous assertion generation
- **RegMatrix**：依赖文档结构抽取、约束表达、register verification 工程流程的结合

## 最稳的表达方式

这份学术页真正要支撑的，不是“每个 topic 都已经被学术界完全证明成熟”，而是：

- 有些 topic 已有明确邻近论文支持
- 有些 topic 更多建立在成熟工程流程之上
- 最稳妥的整体表述是：
  **AI in DV 最适合作为 copilot / assistant / orchestration layer，而不是替代 signoff judgment 的自动系统**

## 英文完整版入口

- `../../docs/academic-supporting-papers.md`

## 当前说明

这版先把中文站点恢复到“内容上可解释、立场上稳、用途上接近英文版”的状态。

如果你要，我可以继续把英文版论文列表逐条翻成完整中文注释版。