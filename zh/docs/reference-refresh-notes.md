# AI 辅助设计验证：Reference Refresh Notes（中英文整理版·中文版）

这份笔记用于为 AI-assisted design verification 的 8 个 topic 补强 reference 包。目标不是夸大说每个方向都已经是成熟独立产品，而是把它们分别锚定到：

- **Academic references（学术文献）**
- **Engineering / tooling references（工程方法、标准、工具、文档）**

这样后续无论你要继续写英文版、中文版，还是把 supporting references 再拆细，都有一份更稳的底稿。

---

## 1. CoverPilot — Coverage Intelligence

### 学术文献

1. **Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation** (2023)  
   DOI: <https://doi.org/10.1109/DAC56929.2023.10247936>  
   **相关性：** 直接把 RTL coverage、simulation result 和 data-driven test selection 连起来，是 CoverPilot 最强的一类支撑。  
   **证据强度：强**

2. **Speed Up Functional Coverage Closure of CORDIC Designs Using Machine Learning Models** (2021)  
   DOI: <https://doi.org/10.1109/ICM52667.2021.9664930>  
   **相关性：** 明确讨论 ML 如何加速 functional coverage closure。虽然设计对象较窄，但方向高度匹配。  
   **证据强度：强**

3. **Using Deep Neural Networks And Derivative Free Optimization To Accelerate Coverage Closure** (2021)  
   DOI: <https://doi.org/10.1109/MLCAD52597.2021.9531234>  
   **相关性：** 说明 coverage closure 不只是“看报告”，还可以做优化驱动。  
   **证据强度：强**

4. **Accelerated Design Verification Coverage Closure Using Machine Learning** (2025)  
   DOI: <https://doi.org/10.1109/VLSID64188.2025.00070>  
   **相关性：** 证明这个方向到近年仍在持续发表。  
   **证据强度：中**

### 工程 / 工具参考

1. **Verification Academy – Coverage**  
   <https://verificationacademy.com/topics/coverage/>  
   **相关性：** 证明 coverage closure 本身就是非常真实的 DV 问题。  
   **证据强度：强**

2. **PyUCIS Documentation**  
   <https://pyucis.readthedocs.io/en/latest/>  
   **相关性：** 支撑 coverage 数据结构化处理。  
   **证据强度：强**

3. **Accellera / IEEE standards portal**  
   <https://www.accellera.org/downloads/ieee>  
   **相关性：** 提供标准/方法论背景。  
   **证据强度：中**

4. **PyVSC Documentation**  
   <https://pyvsc.readthedocs.io/en/latest/>  
   **相关性：** 当 coverage 建议需要回流到 stimulus refinement 时很有用。  
   **证据强度：中**

### 建议写法

建议写成：**“CoverPilot 用数据驱动方式帮助优先级排序 coverage holes、关联 RTL/feature，并给出下一步 closure 实验建议。”**  
避免写成：**“AI 可以自动解决 coverage closure。”**

---

## 2. RegMatrix — Register / Spec Intelligence

### 学术文献

1. **Real-time automated register abstraction active power-aware electronic system level verification framework** (2020)  
   DOI: <https://doi.org/10.1016/j.vlsi.2020.11.013>  
   **相关性：** 支撑 automated register abstraction 与 register-level verification。  
   **证据强度：中**

2. **Functional Test Generation with Distribution Constraints** (2011)  
   DOI: <https://doi.org/10.1007/978-3-642-19237-1_7>  
   **相关性：** 支撑 constraint-aware test generation，这对 RegMatrix 很关键。  
   **证据强度：中**

3. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 作为 AI-for-DV 总体背景支撑。  
   **证据强度：中**

### 工程 / 工具参考

1. **Accellera UVM Standard**  
   <https://accellera.org/downloads/standards/uvm>  
   **相关性：** register/spec intelligence 最终要服务真实 DV methodology。  
   **证据强度：强**

2. **UVM 1.2 Reference Documentation**  
   <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>  
   **相关性：** 让 RegMatrix 更容易与真实 testbench 场景挂钩。  
   **证据强度：强**

3. **PyVSC Documentation**  
   <https://pyvsc.readthedocs.io/en/latest/>  
   **相关性：** 从抽取出的约束到可执行 constrained-random 的桥梁。  
   **证据强度：强**

4. **NetworkX Documentation**  
   <https://networkx.org/documentation/stable/>  
   **相关性：** 很适合支撑 register relation graph / dependency graph。  
   **证据强度：强**

### 建议写法

建议写成：**“RegMatrix 从 spec 中抽取候选 register 关系与验证相关约束，并组织成可供工程师复核的 graph 与 test-oriented artifacts。”**  
避免写成全自动 spec 理解器。

---

## 3. TestForge RL — Stimulus Optimization / RL-guided Exploration

### 学术文献

1. **Reinforcement-Learning Based Method for Accelerating Functional Coverage Closure of Traffic Light Controller Dynamic Digital Design** (2022)  
   DOI: <https://doi.org/10.1109/ICCTA58027.2022.10206069>  
   **相关性：** 很直接地支撑 RL 用于 coverage closure。  
   **证据强度：强**

2. **Transaction Level Stimulus Optimization in Functional Verification Using Machine Learning Predictors** (2022)  
   DOI: <https://doi.org/10.1109/ISQED54688.2022.9806210>  
   **相关性：** 强支撑 ML-guided stimulus optimization。  
   **证据强度：强**

3. **Efficient Sequence Generation for Hardware Verification Using Machine Learning** (2021)  
   DOI: <https://doi.org/10.1109/ICECS53924.2021.9665495>  
   **相关性：** 支撑 sequence generation 与 intelligent verification stimulus。  
   **证据强度：中**

4. **Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation** (2023)  
   DOI: <https://doi.org/10.1109/DAC56929.2023.10247936>  
   **相关性：** 虽不是纯 RL，但与数据驱动 test selection 强相关。  
   **证据强度：强**

### 工程 / 工具参考

1. **Ray RLlib Documentation**  
   <https://docs.ray.io/en/latest/rllib/index.html>  
   **相关性：** 强实现支撑。  
   **证据强度：强**

2. **Gymnasium Documentation**  
   <https://gymnasium.farama.org/>  
   **相关性：** 适合把验证过程抽象成 state/action/reward。  
   **证据强度：强**

3. **pytest markers documentation**  
   <https://docs.pytest.org/en/stable/example/markers.html>  
   **相关性：** 虽偏软件测试，但可用作 selective execution / tagging 的工程类比。  
   **证据强度：中**

### 建议写法

建议写成：**“TestForge RL 探索 reward-driven 的 stimulus 与 test-selection 策略，以在有限 runtime 预算下提升 coverage 效率。”**

---

## 4. DVCore — Multi-Agent DV Platform / Orchestration

### 学术文献

1. **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
   DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
   **相关性：** DVCore 最强的学术支撑，说明 verification 可以被组织成 structured artifact pipeline。  
   **证据强度：强**

2. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 支撑多个 AI-for-DV capability 被统一编排。  
   **证据强度：中**

3. **High Performance Machine Learning Models for Functional Verification of Hardware Designs** (2021)  
   DOI: <https://doi.org/10.1109/NILES53778.2021.9600502>  
   **相关性：** 从 feasibility 角度支撑 ML-driven verification workflow。  
   **证据强度：中**

### 工程 / 工具参考

1. **LangChain Overview**  
   <https://docs.langchain.com/oss/python/langchain/overview>  
   **相关性：** 支撑 retrieval、tool use、多阶段 workflow。  
   **证据强度：强**

2. **OpenTelemetry Logs**  
   <https://opentelemetry.io/docs/concepts/signals/logs/>  
   **相关性：** 支撑结构化日志采集。  
   **证据强度：强**

3. **OpenTelemetry Traces**  
   <https://opentelemetry.io/docs/concepts/signals/traces/>  
   **相关性：** 支撑因果链、跨流程 observability。  
   **证据强度：强**

4. **GitHub Actions artifact documentation**  
   <https://docs.github.com/en/actions/tutorials/store-and-share-data>  
   **相关性：** 支撑 artifacts 的收集与流转。  
   **证据强度：中**

5. **SQLite JSON functions**  
   <https://www.sqlite.org/json1.html>  
   **相关性：** 适合 MVP 级的结构化 artifact store。  
   **证据强度：中**

### 建议写法

建议写成：**“DVCore 是 AI-assisted DV workflows 的 orchestration layer，把 logs、reports、retrieval、tool execution 与 observability 串成统一工程平台。”**

---

## 5. WaveScope MCP — Waveform / Debug Intelligence

### 学术文献

1. **Clustering-based failure triage for RTL regression debugging** (2014)  
   DOI: <https://doi.org/10.1109/TEST.2014.7035339>  
   **相关性：** 虽不专门讲 waveform，但对 debug artifact triage 很关键。  
   **证据强度：强**

2. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 给 ML-assisted debug 提供 broader framing。  
   **证据强度：中**

3. **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
   DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
   **相关性：** 支撑 structured debug artifacts + downstream analysis。  
   **证据强度：中**

### 工程 / 工具参考

1. **Verilator User’s Guide**  
   <https://verilator.org/guide/latest/>  
   **相关性：** 提供真实 open simulation/debug 语境。  
   **证据强度：强**

2. **cocotb Documentation**  
   <https://docs.cocotb.org/en/stable/>  
   **相关性：** 支撑 Python 化 orchestration 与 debug artifact 抽取。  
   **证据强度：强**

3. **OpenTelemetry Logs**  
   <https://opentelemetry.io/docs/concepts/signals/logs/>  
   **相关性：** 支撑 structured event extraction。  
   **证据强度：中**

4. **OpenTelemetry Traces**  
   <https://opentelemetry.io/docs/concepts/signals/traces/>  
   **相关性：** 支撑 first-divergence / causal-chain 这类叙述。  
   **证据强度：中**

### 建议写法

建议写成：**“WaveScope MCP 在 simulation artifacts 之上提供 structured、trace-aware 的 debug assistance，帮助工程师总结 divergence point 并追踪可能因果链。”**

---

## 6. FailSense — Regression Failure Intelligence

### 学术文献

1. **Clustering-based failure triage for RTL regression debugging** (2014)  
   DOI: <https://doi.org/10.1109/TEST.2014.7035339>  
   **相关性：** 这是 FailSense 最核心、最直接的 academic support。  
   **证据强度：强**

2. **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
   DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
   **相关性：** 支撑 regression intelligence 背后的 structured-data / pipeline 假设。  
   **证据强度：强**

3. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 提供 broader framing。  
   **证据强度：中**

4. **Efficient Hardware Verification Using Machine Learning Approach** (2019)  
   DOI: <https://doi.org/10.1109/ISES47678.2019.00045>  
   **相关性：** 提供早期 feasibility 支撑。  
   **证据强度：中**

### 工程 / 工具参考

1. **Accellera UVM Standard**  
   <https://accellera.org/downloads/standards/uvm>  
   **相关性：** 工业回归的大量 artifact 都来自 UVM 环境。  
   **证据强度：强**

2. **UVM 1.2 Reference Documentation**  
   <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>  
   **相关性：** 支撑 report messages、hierarchy、context packet。  
   **证据强度：强**

3. **scikit-learn clustering documentation**  
   <https://scikit-learn.org/stable/modules/clustering.html>  
   **相关性：** failure grouping 的经典 ML 基础。  
   **证据强度：强**

4. **DBSCAN documentation**  
   <https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html>  
   **相关性：** 很适合 noisy、unknown-cluster-count 的 regression 数据。  
   **证据强度：强**

5. **Sentence Transformers**  
   <https://www.sbert.net/>  
   **相关性：** 支撑非完全相同错误文本的语义相似度匹配。  
   **证据强度：强**

6. **Faiss**  
   <https://faiss.ai/>  
   **相关性：** 支撑历史 issue 检索。  
   **证据强度：强**

### 建议写法

建议写成：**“FailSense 对 regression failures 做聚类、摘要、去重与历史问题检索，以减少人工 triage 成本。”**  
不要写成仅凭日志就能保证 root cause 正确。

---

## 7. JiraMine — JIRA-Guided High-Yield Test Mining Intelligence

### 学术文献

1. **Machine-Learning-Enabled Hardware Formal Verification**  
   DOI: <https://doi.org/10.14711/thesis-hdl167709>  
   **相关性：** 是 formal + ML 交叉方向比较直接的引用。  
   **证据强度：中**

2. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 作为 broader AI-for-DV support。  
   **证据强度：中**

### 工程 / 工具参考

1. **Verification Academy – Formal Verification**  
   <https://verificationacademy.com/topics/formal-verification/>  
   **相关性：** formal methodology grounding。  
   **证据强度：强**

2. **SymbiYosys Documentation**  
   <https://yosyshq.readthedocs.io/projects/sby/en/latest/>  
   **相关性：** 真实 formal workflow，适合 AI 帮忙解释 proof / cex。  
   **证据强度：强**

3. **PyEDA Documentation**  
   <https://pyeda.readthedocs.io/en/latest/>  
   **相关性：** 支撑 symbolic / Boolean reasoning。  
   **证据强度：中**

### 建议写法

建议写成：**“JiraMine 辅助 property review、proof-result interpretation 和 counterexample-oriented debug，特别适合 formal-friendly workflow。”**

---

## 8. RegCleanse — Low-Yield Regression Cleanup Intelligence

### 学术文献

1. **Functional Test Generation with Distribution Constraints** (2011)  
   DOI: <https://doi.org/10.1007/978-3-642-19237-1_7>  
   **相关性：** 支撑从 constraint / intent 到 test 的转换。  
   **证据强度：中**

2. **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
   DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
   **相关性：** 支撑 artifacts 可结构化、可查询、可连通。  
   **证据强度：中**

3. **Machine Learning in the Service of Hardware Functional Verification** (2022)  
   DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
   **相关性：** 提供 broader support。  
   **证据强度：中**

### 工程 / 工具参考

1. **Accellera UVM Standard**  
   <https://accellera.org/downloads/standards/uvm>  
   **相关性：** traceability 最终还是要连接实际 verification implementation。  
   **证据强度：强**

2. **UVM 1.2 Reference Documentation**  
   <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>  
   **相关性：** 支撑 requirement/spec 到 testbench artifact 的映射语境。  
   **证据强度：强**

3. **NetworkX Documentation**  
   <https://networkx.org/documentation/stable/>  
   **相关性：** 非常适合 requirement-to-test graph / traceability graph。  
   **证据强度：强**

4. **SQLite JSON functions**  
   <https://www.sqlite.org/json1.html>  
   **相关性：** 适合 requirement/test/coverage linkage 的轻量级原型。  
   **证据强度：中**

### 建议写法

建议写成：**“RegCleanse 构建 requirements、specs、tests、coverage 与 debug evidence 之间的 traceability links，帮助工程师识别哪些需求已实现、已验证、或仍然薄弱。”**

---

## 总体建议

如果你后续要在文档里给 8 个 topic 排一个“证据强弱层级”，我建议这样分：

### 第一梯队（证据最强）
1. **FailSense**
2. **CoverPilot**
3. **TestForge RL**

### 第二梯队（中等强度，工程上很合理）
4. **DVCore**
5. **WaveScope MCP**
6. **RegMatrix**

### 第三梯队（可支撑，但写法要收敛）
7. **JiraMine**
8. **RegCleanse**

这不代表后两项应该删掉，而是代表它们更适合写成：

- assistant
- copilot
- structured-support layer

而不是 fully automatic reasoning engine。
