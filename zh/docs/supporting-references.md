# AI辅助设计验证的支持性参考资料

本文档整理了与本仓库相关的外部参考资料，用于支撑这里讨论的各类 **AI-assisted design verification** 方向。目标不是说这些资料已经直接构成一整套现成的 AI for DV 方案，而是说明本仓库里的项目思路——例如 coverage intelligence、register/spec intelligence、test selection、waveform-aware debug、DV agent orchestration——都可以建立在真实存在的验证方法学、工程工具链和通用 AI 技术之上。

这些参考资料主要分为几类：

- 验证方法学与标准
- coverage / register / formal 相关工程知识
- clustering / retrieval / ML 技术基础
- 数据管线与实现基础设施

---

## 1. 回归分析与验证方法学基础

### Accellera UVM Standard
- **来源：** Accellera
- **链接：** <https://accellera.org/downloads/standards/uvm>
- **为什么重要：**
  UVM 是现代设计验证里最核心的方法学之一。本仓库很多方向——无论是 regression triage、coverage intelligence，还是 agent-based DV workflow——都默认建立在日志、UVM report、scoreboard、monitor、driver、sequencer、register model 等真实验证 artifacts 之上。这个引用的意义在于：说明本仓库不是在空谈“AI for hardware”，而是在接入成熟验证方法学产生的数据。
- **适合支撑：**
  regression intelligence、testbench-aware analysis、verification artifacts grounding

### UVM 1.2 Reference Documentation
- **来源：** Verification Academy
- **链接：** <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **为什么重要：**
  这份参考文档有助于支撑关于 UVM report、component hierarchy、验证环境结构化信息的讨论。对于 AI-assisted DV 而言，这类结构化上下文本身就是非常有价值的输入源。
- **适合支撑：**
  UVM-based artifact parsing、structured failure packet、verification context awareness

---

## 2. Coverage / Register / Formal 方向的工程支撑

### Verification Academy – Coverage
- **来源：** Verification Academy
- **链接：** <https://verificationacademy.com/topics/coverage/>
- **为什么重要：**
  coverage closure 是 DV 里最典型、最耗时的工作之一。这个入口能帮助支撑本仓库里 **CoverPilot** 的定位：AI 的作用不是替代 coverage methodology，而是帮助做 hole prioritization、RTL mapping 和 closure suggestion。
- **适合支撑：**
  coverage intelligence、coverage-hole analysis、closure guidance

### Verification Academy – Formal Verification
- **来源：** Verification Academy
- **链接：** <https://verificationacademy.com/topics/formal-verification/>
- **为什么重要：**
  formal verification 是本仓库长期扩展方向的重要邻接领域。虽然当前主结构里没有单列 formal project，但它与 assertion reasoning、property assistance、root-cause explanation 都高度相关。
- **适合支撑：**
  formal + AI、property-oriented analysis、long-term DV expansion

### PyUCIS Documentation
- **来源：** PyUCIS
- **链接：** <https://pyucis.readthedocs.io/en/latest/>
- **为什么重要：**
  如果要把 coverage intelligence 从“文字说明”推进到“结构化分析系统”，就需要 programmatic access to coverage data。PyUCIS 这类资料能很好地支撑这一点。
- **适合支撑：**
  structured coverage processing、coverage analytics pipeline

### PyVSC Documentation
- **来源：** PyVSC
- **链接：** <https://pyvsc.readthedocs.io/en/latest/>
- **为什么重要：**
  PyVSC 能帮助支撑 **RegMatrix** 与 intelligent stimulus planning 的连接。因为 register/spec intelligence 最终不只是读文档，还要能映射到可执行的验证约束和 test intent。
- **适合支撑：**
  dynamic constraints、stimulus planning、constraint-aware verification

---

## 3. 聚类、检索与通用 ML 技术基础

### scikit-learn Clustering Documentation
- **来源：** scikit-learn
- **链接：** <https://scikit-learn.org/stable/modules/clustering.html>
- **为什么重要：**
  无论是 failure grouping、coverage pattern segmentation，还是历史结果分类，聚类都是非常自然的技术基础。它提醒读者：AI-assisted DV 不一定只依赖大模型，也可以结合经典 ML 方法。
- **适合支撑：**
  failure clustering、issue grouping、coverage pattern mining

### DBSCAN Documentation
- **来源：** scikit-learn
- **链接：** <https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html>
- **为什么重要：**
  验证数据往往 noisy、cluster 数量未知，而且常常存在 outlier failure。DBSCAN 这样的算法非常适合作为 failure triage / novelty detection 的支撑思路。
- **适合支撑：**
  outlier detection、novelty-oriented triage、duplicate reduction

### Sentence Transformers Documentation
- **来源：** Sentence Transformers
- **链接：** <https://www.sbert.net/>
- **为什么重要：**
  许多失败虽然文本不完全一致，但语义上来自同一 root cause。embedding-based similarity 是 AI-assisted triage 里非常自然的一环。
- **适合支撑：**
  semantic failure similarity、historical retrieval、embedding clustering

### Faiss Documentation
- **来源：** Faiss
- **链接：** <https://faiss.ai/>
- **为什么重要：**
  一旦验证组织开始积累历史 failure、bug summary、debug notes，向量检索就会变得很有价值。Faiss 可以作为 large-scale retrieval 的底层支撑参考。
- **适合支撑：**
  similarity search、historical issue lookup、retrieval-backed analysis

### LangChain Overview
- **来源：** LangChain
- **链接：** <https://docs.langchain.com/oss/python/langchain/overview>
- **为什么重要：**
  对本仓库中的 **DVCore** 来说，workflow orchestration、tool use、retrieval augmentation 都是关键点。LangChain 不是 DV 专用框架，但它很好地展示了多步 agent workflow 的常见实现形态。
- **适合支撑：**
  DV agent orchestration、RAG-style verification copilot、tool-driven workflows

---

## 4. 数据管线与工程实现基础

### OpenTelemetry Logs
- **来源：** OpenTelemetry
- **链接：** <https://opentelemetry.io/docs/concepts/signals/logs/>
- **为什么重要：**
  本仓库里关于 log-aware AI 和 waveform-aware AI 的很多思路，都依赖“先把原始数据结构化，再让模型推理”。OpenTelemetry 的 logs 概念对这种思路很有启发性。
- **适合支撑：**
  structured event extraction、normalized failure artifacts、debug data modeling

### OpenTelemetry Traces
- **来源：** OpenTelemetry
- **链接：** <https://opentelemetry.io/docs/concepts/signals/traces/>
- **为什么重要：**
  如果把 waveform debug 理解成“定位 first divergence 和 causal chain”，那么 trace 思维就很值得借鉴。它不是直接替代 waveform，但能提供一个很好的抽象框架。
- **适合支撑：**
  causal debug timeline、event-sequence reasoning、WaveScope MCP framing

### GitHub Actions – Store and Share Data
- **来源：** GitHub Docs
- **链接：** <https://docs.github.com/en/actions/tutorials/store-and-share-data>
- **为什么重要：**
  regression intelligence 和 supporting reports 最终都需要有 artifact collection 和 post-processing pipeline。这个引用能让本仓库中的工程实现路径看起来更现实。
- **适合支撑：**
  regression artifacts、pipeline automation、report generation

### SQLite JSON Functions
- **来源：** SQLite
- **链接：** <https://www.sqlite.org/json1.html>
- **为什么重要：**
  本仓库中提到的 structured failure records、lightweight historical store，都很适合用 SQLite JSON 这种轻量方式先落地。
- **适合支撑：**
  lightweight failure database、local MVP storage、structured artifact queries

### Apache Parquet Documentation
- **来源：** Apache Parquet
- **链接：** <https://parquet.apache.org/docs/>
- **为什么重要：**
  如果未来将 AI-assisted DV 扩展为趋势分析、批量学习、历史模式挖掘，Parquet 这种列式存储就会变得很自然。
- **适合支撑：**
  historical analytics、large-scale verification datasets、offline analysis

---

## 5. 建议的最小参考集合

如果只想保留一组最关键的 supporting references，建议优先保留：

1. Accellera UVM Standard  
2. UVM 1.2 Reference Documentation  
3. Verification Academy – Coverage  
4. scikit-learn Clustering Documentation  
5. DBSCAN Documentation  
6. Sentence Transformers Documentation  
7. Faiss Documentation  
8. LangChain Overview  
9. OpenTelemetry Logs  
10. OpenTelemetry Traces  
11. GitHub Actions – Store and Share Data  
12. SQLite JSON Functions  

这组资料基本可以为本仓库最重要的主题——CoverPilot、RegMatrix、TestForge RL、DVCore、WaveScope MCP——提供一个比较可信的工程和方法学背景。


---

## 9. 按 8 个 Topic 重组后的增强参考文献包

这一节把仓库中的 supporting references 按 8 个核心 topic 重新组织，便于直接嵌入主文档。

### 9.1 CoverPilot — Coverage Intelligence

#### Academic references
- **Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation** (2023)  
  DOI: <https://doi.org/10.1109/DAC56929.2023.10247936>  
  相关性：直接把 RTL coverage 结果与数据驱动的 test selection 连接起来。
- **Speed Up Functional Coverage Closure of CORDIC Designs Using Machine Learning Models** (2021)  
  DOI: <https://doi.org/10.1109/ICM52667.2021.9664930>  
  相关性：明确证明 ML 可用于加速 coverage closure。
- **Using Deep Neural Networks And Derivative Free Optimization To Accelerate Coverage Closure** (2021)  
  DOI: <https://doi.org/10.1109/MLCAD52597.2021.9531234>  
  相关性：支撑优化驱动的 closure guidance，而不只是被动看报告。
- **Accelerated Design Verification Coverage Closure Using Machine Learning** (2025)  
  DOI: <https://doi.org/10.1109/VLSID64188.2025.00070>  
  相关性：说明 ML-for-coverage-closure 仍然是近年持续被研究的话题。

#### Engineering / tooling references
- **Verification Academy – Coverage** — <https://verificationacademy.com/topics/coverage/>
- **PyUCIS Documentation** — <https://pyucis.readthedocs.io/en/latest/>
- **Accellera / IEEE Standards Portal** — <https://www.accellera.org/downloads/ieee>
- **PyVSC Documentation** — <https://pyvsc.readthedocs.io/en/latest/>

### 9.2 RegMatrix — Register / Spec Intelligence

#### Academic references
- **Real-time automated register abstraction active power-aware electronic system level verification framework** (2020)  
  DOI: <https://doi.org/10.1016/j.vlsi.2020.11.013>  
  相关性：支撑 automated register abstraction 与结构化 register-level verification reasoning。
- **Functional Test Generation with Distribution Constraints** (2011)  
  DOI: <https://doi.org/10.1007/978-3-642-19237-1_7>  
  相关性：对 register/spec intelligence 中的 constraint-aware test generation 很有帮助。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：提供更广义的 AI-for-DV 背景支撑。

#### Engineering / tooling references
- **Accellera UVM Standard** — <https://accellera.org/downloads/standards/uvm>
- **UVM 1.2 Reference Documentation** — <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **PyVSC Documentation** — <https://pyvsc.readthedocs.io/en/latest/>
- **NetworkX Documentation** — <https://networkx.org/documentation/stable/>

### 9.3 TestForge RL — Stimulus Optimization / RL-guided Exploration

#### Academic references
- **Reinforcement-Learning Based Method for Accelerating Functional Coverage Closure of Traffic Light Controller Dynamic Digital Design** (2022)  
  DOI: <https://doi.org/10.1109/ICCTA58027.2022.10206069>  
  相关性：直接支撑 RL-guided coverage closure。
- **Transaction Level Stimulus Optimization in Functional Verification Using Machine Learning Predictors** (2022)  
  DOI: <https://doi.org/10.1109/ISQED54688.2022.9806210>  
  相关性：强支撑 ML-guided stimulus optimization。
- **Efficient Sequence Generation for Hardware Verification Using Machine Learning** (2021)  
  DOI: <https://doi.org/10.1109/ICECS53924.2021.9665495>  
  相关性：支撑 sequence generation for intelligent verification stimulus。
- **Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation** (2023)  
  DOI: <https://doi.org/10.1109/DAC56929.2023.10247936>  
  相关性：强支撑 coverage goal 下的数据驱动 test selection。

#### Engineering / tooling references
- **Ray RLlib Documentation** — <https://docs.ray.io/en/latest/rllib/index.html>
- **Gymnasium Documentation** — <https://gymnasium.farama.org/>
- **pytest markers documentation** — <https://docs.pytest.org/en/stable/example/markers.html>

### 9.4 DVCore — Multi-Agent DV Platform / Orchestration

#### Academic references
- **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
  DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
  相关性：把 DV 视为 structured artifact pipeline 的最强学术支撑。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：支撑统一编排多个 AI-for-DV capability 的平台层。
- **High Performance Machine Learning Models for Functional Verification of Hardware Designs** (2021)  
  DOI: <https://doi.org/10.1109/NILES53778.2021.9600502>  
  相关性：从 feasibility 角度支撑 ML-driven verification workflow。

#### Engineering / tooling references
- **LangChain Overview** — <https://docs.langchain.com/oss/python/langchain/overview>
- **OpenTelemetry Logs** — <https://opentelemetry.io/docs/concepts/signals/logs/>
- **OpenTelemetry Traces** — <https://opentelemetry.io/docs/concepts/signals/traces/>
- **GitHub Actions Artifacts** — <https://docs.github.com/en/actions/tutorials/store-and-share-data>
- **SQLite JSON Functions** — <https://www.sqlite.org/json1.html>

### 9.5 WaveScope MCP — Waveform / Debug Intelligence

#### Academic references
- **Clustering-based failure triage for RTL regression debugging** (2014)  
  DOI: <https://doi.org/10.1109/TEST.2014.7035339>  
  相关性：对 debug artifact triage 和 issue-bucket reasoning 很直接。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：为 ML-assisted debug analysis 提供 broader support。
- **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
  DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
  相关性：支撑 structured debug artifacts 与 downstream analysis。

#### Engineering / tooling references
- **Verilator User’s Guide** — <https://verilator.org/guide/latest/>
- **cocotb Documentation** — <https://docs.cocotb.org/en/stable/>
- **OpenTelemetry Logs** — <https://opentelemetry.io/docs/concepts/signals/logs/>
- **OpenTelemetry Traces** — <https://opentelemetry.io/docs/concepts/signals/traces/>

### 9.6 FailSense — Regression Failure Intelligence

#### Academic references
- **Clustering-based failure triage for RTL regression debugging** (2014)  
  DOI: <https://doi.org/10.1109/TEST.2014.7035339>  
  相关性：这是 regression failure clustering / triage 最直接、最强的支撑。
- **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
  DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
  相关性：支撑 practical regression intelligence 背后的 structured-data 假设。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：为 ML-assisted verification analytics 提供 broader framing。
- **Efficient Hardware Verification Using Machine Learning Approach** (2019)  
  DOI: <https://doi.org/10.1109/ISES47678.2019.00045>  
  相关性：较早证明 ML 有机会提升 hardware verification productivity。

#### Engineering / tooling references
- **Accellera UVM Standard** — <https://accellera.org/downloads/standards/uvm>
- **UVM 1.2 Reference Documentation** — <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **scikit-learn Clustering Documentation** — <https://scikit-learn.org/stable/modules/clustering.html>
- **DBSCAN Documentation** — <https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html>
- **Sentence Transformers Documentation** — <https://www.sbert.net/>
- **Faiss Documentation** — <https://faiss.ai/>

### 9.7 AssertMind — Assertion / Formal Intelligence

#### Academic references
- **Machine-Learning-Enabled Hardware Formal Verification**  
  DOI: <https://doi.org/10.14711/thesis-hdl167709>  
  相关性：formal + ML 交叉方向比较直接的引用。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：为 AI-enhanced verification reasoning 提供 broader support。

#### Engineering / tooling references
- **Verification Academy – Formal Verification** — <https://verificationacademy.com/topics/formal-verification/>
- **SymbiYosys Documentation** — <https://yosyshq.readthedocs.io/projects/sby/en/latest/>
- **PyEDA Documentation** — <https://pyeda.readthedocs.io/en/latest/>

### 9.8 TraceLens — Spec-to-Test Traceability Intelligence

#### Academic references
- **Functional Test Generation with Distribution Constraints** (2011)  
  DOI: <https://doi.org/10.1007/978-3-642-19237-1_7>  
  相关性：支撑从 constraints / intent 到 executable tests 的转换。
- **Data-Centric Machine Learning Pipeline for Hardware Verification** (2022)  
  DOI: <https://doi.org/10.1109/SOCC56010.2022.9908095>  
  相关性：支撑 verification artifacts 可被视为 connected、queryable data。
- **Machine Learning in the Service of Hardware Functional Verification** (2022)  
  DOI: <https://doi.org/10.1007/978-3-031-13074-8_14>  
  相关性：为连接 verification intent 与 execution 的 AI layer 提供 broader support。

#### Engineering / tooling references
- **Accellera UVM Standard** — <https://accellera.org/downloads/standards/uvm>
- **UVM 1.2 Reference Documentation** — <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **NetworkX Documentation** — <https://networkx.org/documentation/stable/>
- **SQLite JSON Functions** — <https://www.sqlite.org/json1.html>
