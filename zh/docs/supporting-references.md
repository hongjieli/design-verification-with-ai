# Supporting References for AI-Assisted Design Verification（中文摘要版）

这个页面现在恢复成中文可读版本，并与英文版在用途上基本对齐：

- 支撑仓库里讨论的 8 个 topic
- 说明这些方向并非空想，而是建立在真实验证方法学、工程工具和相关 ML 思路之上
- 强调“不是说每个 reference 都直接等于一个成熟产品”，而是说明这些方向具备工程可落地性

## 这份 references 的作用

它主要承担三件事：

1. 给每个 topic 提供工程和方法学支撑
2. 避免把 AI for DV 说成凭空出现的新概念
3. 帮助读者理解：真正可靠的 AI-assisted DV，必须建立在已有验证流程、artifact 和工程实践之上

## 8 个 topic 的支撑结构

- **CoverPilot**：coverage closure、coverage analysis、coverage methodology
- **RegMatrix**：register / spec extraction、RAL / UVM、约束与依赖关系表达
- **TestForge RL**：test prioritization、regression optimization、RL / adaptive scheduling
- **DVCore**：artifact pipeline、agent orchestration、observability、workflow integration
- **WaveScope MCP**：waveform debug、trace extraction、debug artifact structuring
- **FailSense**：regression failure triage、clustering、novelty detection
- **AssertMind**：assertion review、formal result explanation、property-oriented assistance
- **TraceLens**：requirements / spec / tests / coverage 之间的 traceability

## 推荐的阅读方式

如果读者只想快速抓主线，可以按这个顺序看：

1. 英文主文档：`../../docs/design-verification-ai-ideas.md`
2. 英文 supporting references：`../../docs/supporting-references.md`
3. 英文学术文献页：`../../docs/academic-supporting-papers.md`
4. 中文各 topic 页面：`./topics/`

## 当前说明

这版是中文摘要增强版，目标是让中文站点在信息密度和用途上接近英文版，而不是继续停留在“只有一个占位链接”。

如果你要，我下一步可以继续把英文 `supporting-references.md` 全量逐段翻译成完整中文正式版。