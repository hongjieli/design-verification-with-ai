# AI辅助设计验证的学术支持论文清单

本文档整理了一份聚焦型的学术论文 shortlist，用于支持本仓库中关于 **AI + Design Verification (DV)** 的核心技术方向。目标不是声称这些论文已经完整解决了本项目中的所有问题，而是说明本仓库提出的思路——例如回归失败归因、coverage closure 智能化、测试优化、验证数据管线化——都能在现有学术研究中找到真实的关联和支撑。

本清单优先选择那些最适合为本仓库叙事提供“可信学术背书”的论文，尤其围绕：

- AI辅助回归失败分类与归因
- coverage closure intelligence
- 机器学习引导的验证计划与测试选择
- 结构化验证数据管线
- regression prioritization / optimization

---

## 1. 回归失败归类 / RTL 调试

### Clustering-based failure triage for RTL regression debugging
- **年份：** 2014
- **会议：** International Test Conference (ITC)
- **DOI：** <https://doi.org/10.1109/TEST.2014.7035339>
- **为什么重要：**
  这是目前最直接贴合本仓库主线——**AI-assisted regression failure triage**——的一篇论文。论文标题本身就高度对应“将大规模回归失败压缩成若干 failure clusters / issue buckets”的思路。虽然它早于今天的 LLM 工作流，但它非常有价值，因为它证明了 failure clustering 和 regression triage 本身就是设计验证中的真实问题，而不是 AI 时代凭空创造出来的需求。
- **适合支撑：**
  regression intelligence、failure clustering、重复失败归并、root-cause grouping

---

## 2. Hardware Functional Verification + ML

### Machine Learning in the Service of Hardware Functional Verification
- **年份：** 2022
- **来源：** *Machine Learning Applications in Electronic Design Automation*
- **DOI：** <https://doi.org/10.1007/978-3-031-13074-8_14>
- **为什么重要：**
  这篇论文很适合作为“总览型”支撑文献，帮助说明 ML 在 hardware functional verification 中并不是孤立的小技巧，而是一个逐渐成型的技术方向。对本仓库来说，它尤其适合用来支撑“AI for DV 是一个值得严肃看待的方向”这一整体论点。
- **适合支撑：**
  AI for DV 总体 framing、verification intelligence、项目方向定位

### Data-Centric Machine Learning Pipeline for Hardware Verification
- **年份：** 2022
- **会议：** IEEE International System-on-Chip Conference (SOCC)
- **DOI：** <https://doi.org/10.1109/SOCC56010.2022.9908095>
- **为什么重要：**
  本仓库反复强调：真正有价值的 AI for DV，不能只停留在 prompt 和摘要层面，而要建立在结构化 artifacts、持久数据积累和 pipeline thinking 之上。这篇论文正好支撑这种思路——验证流程可以被看作一个 data-centric 的 ML pipeline，而不仅仅是零散脚本和人工经验的堆叠。
- **适合支撑：**
  regression data pipeline、structured artifacts、verification analytics、historical learning loop

### High Performance Machine Learning Models for Functional Verification of Hardware Designs
- **年份：** 2021
- **会议：** Novel Intelligent and Leading Emerging Sciences Conference
- **DOI：** <https://doi.org/10.1109/NILES53778.2021.9600502>
- **为什么重要：**
  这篇论文支持“机器学习模型可以在 hardware functional verification 中发挥实际作用”这一论点。即便具体工作流与本仓库的实现方式不完全相同，它仍然能提供重要的可行性支撑。
- **适合支撑：**
  ML-assisted verification、functional verification augmentation、可行性支撑

### Efficient Hardware Verification Using Machine Learning Approach
- **年份：** 2019
- **会议：** IEEE International Symposium on Smart Electronic Systems (iSES)
- **DOI：** <https://doi.org/10.1109/ISES47678.2019.00045>
- **为什么重要：**
  这是一个较早期的参考，能帮助说明“机器学习用于硬件验证”并非近两年才突然冒出来的概念。对 supporting papers 而言，这种时间纵深很有用。
- **适合支撑：**
  历史背景、ML for verification 的前期探索、prior art

---

## 3. Coverage Closure Intelligence

### Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation
- **年份：** 2023
- **会议：** Design Automation Conference (DAC)
- **DOI：** <https://doi.org/10.1109/DAC56929.2023.10247936>
- **为什么重要：**
  这篇论文非常适合支撑 coverage intelligence，因为它直接把 RTL coverage、test selection 和 unsupervised learning 联系在一起。对本仓库来说，这几乎是 coverage-driven regression selection 方向最强的一类 supporting evidence。
- **适合支撑：**
  coverage intelligence、RTL test selection、unsupervised guidance、regression planning

### Speed Up Functional Coverage Closure of CORDIC Designs Using Machine Learning Models
- **年份：** 2021
- **会议：** IEEE ICM
- **DOI：** <https://doi.org/10.1109/ICM52667.2021.9664930>
- **为什么重要：**
  这篇论文直接支持“机器学习可以加速 coverage closure”这一主张。即便它聚焦在特定设计类型上，仍然足以说明 coverage closure 是 AI 辅助的现实切入点，而不只是概念口号。
- **适合支撑：**
  coverage closure acceleration、hole prioritization、ML-guided verification effort

### Using Deep Neural Networks And Derivative Free Optimization To Accelerate Coverage Closure
- **年份：** 2021
- **会议：** Workshop on Machine Learning for CAD (MLCAD)
- **DOI：** <https://doi.org/10.1109/MLCAD52597.2021.9531234>
- **为什么重要：**
  这篇论文很好地支持了“coverage closure 不只是做总结和分类，也可以做优化”的思路。它能帮助本仓库说明：AI for DV 不是只能写总结，而是可以真正参与验证资源的优化配置。
- **适合支撑：**
  coverage optimization、intelligent closure acceleration、ML-based search guidance

### Accelerated Design Verification Coverage Closure Using Machine Learning
- **年份：** 2025
- **会议：** International Conference on VLSI Design
- **DOI：** <https://doi.org/10.1109/VLSID64188.2025.00070>
- **为什么重要：**
  这是一篇比较新的论文，标题与本仓库 coverage closure 方向高度贴近。它适合作为“这个方向仍然在持续演进”的近期证据。
- **适合支撑：**
  当前 ML-for-DV 趋势、coverage intelligence、现代相关性

---

## 4. Stimulus Optimization / Test Generation / RL-style Exploration

### Transaction Level Stimulus Optimization in Functional Verification Using Machine Learning Predictors
- **年份：** 2022
- **会议：** IEEE International Symposium on Quality Electronic Design (ISQED)
- **DOI：** <https://doi.org/10.1109/ISQED54688.2022.9806210>
- **为什么重要：**
  这篇论文很适合支撑本仓库关于 stimulus optimization 和 intelligent verification planning 的讨论。它说明 AI 不只是事后分析失败，也可以在“测试什么、怎么测”这个前置环节提供价值。
- **适合支撑：**
  stimulus intelligence、test optimization、verification planning

### Efficient Sequence Generation for Hardware Verification Using Machine Learning
- **年份：** 2021
- **会议：** International Conference on Electronics, Circuits, and Systems
- **DOI：** <https://doi.org/10.1109/ICECS53924.2021.9665495>
- **为什么重要：**
  这篇论文支持“通过机器学习生成更有效的验证序列”这一方向。它与本仓库中从被动分析走向主动优化验证行为的思路非常一致。
- **适合支撑：**
  sequence generation、intelligent verification stimulus、data-driven test creation

### Reinforcement-Learning Based Method for Accelerating Functional Coverage Closure of Traffic Light Controller Dynamic Digital Design
- **年份：** 2022
- **会议：** International Conference on Computing: Theory and Applications (ICCTA)
- **DOI：** <https://doi.org/10.1109/ICCTA58027.2022.10206069>
- **为什么重要：**
  这篇论文未必是 RL for DV 的终极代表，但它足以作为本仓库 **TestForge RL** 思路的现实支撑，证明 reinforcement learning 已经开始被尝试用于功能覆盖驱动的验证优化。
- **适合支撑：**
  reinforcement learning for verification、reward-driven exploration、coverage-guided optimization

---

## 5. Test Selection / Prioritization

### Test Case Prioritization for Regression Testing Using Machine Learning
- **年份：** 2024
- **会议：** IEEE International Conference on Artificial Intelligence Testing (AITest)
- **DOI：** <https://doi.org/10.1109/AITest62860.2024.00027>
- **为什么重要：**
  虽然这篇论文不是 RTL DV 专用，但它依然非常适合支撑本仓库中的 regression planning 方向。它说明：在测试预算有限时，使用机器学习进行 test prioritization 是一个合理、严肃的问题。
- **适合支撑：**
  regression planning、ML-based test prioritization、budget-aware test selection

### Selection, Minimization and Prioritization of Test Cases for Regression Testing
- **年份：** 2011
- **来源：** *Software Testing*
- **DOI：** <https://doi.org/10.1017/CBO9781139196185.008>
- **为什么重要：**
  这是一个很好的基础型引用。它帮助说明：本仓库中的 AI-based prioritization 并不是凭空发明新问题，而是在一个已经存在多年的测试优化问题上继续往前推进。
- **适合支撑：**
  regression planning 的历史基础、test selection foundations

### Survey of Test Case Prioritization Techniques for Regression Testing
- **年份：** 2014
- **会议/期刊：** Journal of Software
- **DOI：** <https://doi.org/10.3724/SP.J.1001.2013.04420>
- **为什么重要：**
  survey 类文献非常适合做 supporting papers，因为它们帮助读者快速理解“test prioritization 本身是一个成熟问题域”。这也能自然引出：AI/ML/RL 只是这个问题的新一代方法。
- **适合支撑：**
  背景综述、test prioritization 文献脉络、AI 扩展的合理性

---

## 6. Formal Verification + AI 邻接方向

### Machine-Learning-Enabled Hardware Formal Verification
- **类型：** thesis / dissertation 风格参考
- **DOI：** <https://doi.org/10.14711/thesis-hdl167709>
- **为什么重要：**
  这不是整份清单中最强的引用，但它与本仓库中 formal + AI 的长期方向直接相关。更适合作为“邻接领域已有探索”的证据，而不是主轴引用。
- **适合支撑：**
  formal + AI、property-oriented assistance、项目长期扩展方向

---

## 7. 本仓库最推荐保留的核心子集

如果只想保留少量最有代表性的学术支持文献，建议优先保留以下 8 篇：

1. **Clustering-based failure triage for RTL regression debugging**  
   <https://doi.org/10.1109/TEST.2014.7035339>
2. **Machine Learning in the Service of Hardware Functional Verification**  
   <https://doi.org/10.1007/978-3-031-13074-8_14>
3. **Data-Centric Machine Learning Pipeline for Hardware Verification**  
   <https://doi.org/10.1109/SOCC56010.2022.9908095>
4. **Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation**  
   <https://doi.org/10.1109/DAC56929.2023.10247936>
5. **Transaction Level Stimulus Optimization in Functional Verification Using Machine Learning Predictors**  
   <https://doi.org/10.1109/ISQED54688.2022.9806210>
6. **Speed Up Functional Coverage Closure of CORDIC Designs Using Machine Learning Models**  
   <https://doi.org/10.1109/ICM52667.2021.9664930>
7. **Using Deep Neural Networks And Derivative Free Optimization To Accelerate Coverage Closure**  
   <https://doi.org/10.1109/MLCAD52597.2021.9531234>
8. **Test Case Prioritization for Regression Testing Using Machine Learning**  
   <https://doi.org/10.1109/AITest62860.2024.00027>

这组文献足以为本仓库最关键的几个技术方向提供一个紧凑但可信的学术支撑骨架。
