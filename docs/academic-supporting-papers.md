# Academic Supporting Papers for AI-Assisted Design Verification

This document collects a focused shortlist of academic papers that are relevant to the technical directions discussed in this repository. The goal is not to claim that all of these papers solve the exact same problem addressed here, but to show that the ideas in this project are connected to real prior work in hardware verification, regression debugging, coverage closure, test selection, and machine-learning-assisted verification workflows.

The shortlist intentionally favors papers that are more directly usable as support for this repository's narrative, especially around:

- AI-assisted regression failure triage
- coverage closure intelligence
- machine-learning-guided verification planning
- structured verification data pipelines
- test prioritization and optimization

---

## 1. Regression Failure Triage / RTL Debugging

### Clustering-based failure triage for RTL regression debugging
- **Year:** 2014
- **Venue:** International Test Conference (ITC)
- **DOI:** <https://doi.org/10.1109/TEST.2014.7035339>
- **Why it matters:**
  This is one of the most directly relevant papers for the repository’s primary deep-dive direction: AI-assisted regression failure triage. The title itself maps closely to the proposed workflow of reducing large regressions into clustered issue buckets. Even though the paper predates today’s LLM-driven workflows, it provides important evidence that failure clustering and regression triage are real and valuable verification problems.
- **Relevant to:**
  regression intelligence, failure clustering, duplicate reduction, root-cause grouping

---

## 2. Hardware Functional Verification + ML

### Machine Learning in the Service of Hardware Functional Verification
- **Year:** 2022
- **Venue:** *Machine Learning Applications in Electronic Design Automation*
- **DOI:** <https://doi.org/10.1007/978-3-031-13074-8_14>
- **Why it matters:**
  This is a strong overview-style reference for the broader theme of using ML to augment hardware functional verification. It is especially useful when positioning this repository as part of a larger AI-for-DV landscape rather than as a single narrow idea.
- **Relevant to:**
  AI for DV framing, verification intelligence, broader repository positioning

### Data-Centric Machine Learning Pipeline for Hardware Verification
- **Year:** 2022
- **Venue:** IEEE International System-on-Chip Conference (SOCC)
- **DOI:** <https://doi.org/10.1109/SOCC56010.2022.9908095>
- **Why it matters:**
  One of the recurring themes in this repository is that useful AI for DV requires structured artifacts, persistent data, and pipeline thinking. This paper is particularly relevant because it supports the idea that verification can be treated as a data-centric ML pipeline rather than as isolated heuristic scripting.
- **Relevant to:**
  regression data pipelines, structured artifacts, verification analytics, historical learning loops

### High Performance Machine Learning Models for Functional Verification of Hardware Designs
- **Year:** 2021
- **Venue:** Novel Intelligent and Leading Emerging Sciences Conference
- **DOI:** <https://doi.org/10.1109/NILES53778.2021.9600502>
- **Why it matters:**
  This paper supports the broader claim that machine-learning models can play a meaningful role in hardware functional verification. It is useful as evidence that verification-oriented ML work is already happening in practice, even when the exact workflows differ from those proposed here.
- **Relevant to:**
  ML-assisted verification, functional verification augmentation, evidence for feasibility

### Efficient Hardware Verification Using Machine Learning Approach
- **Year:** 2019
- **Venue:** IEEE International Symposium on Smart Electronic Systems (iSES)
- **DOI:** <https://doi.org/10.1109/ISES47678.2019.00045>
- **Why it matters:**
  This is a useful earlier reference showing that machine learning for hardware verification has been explored for several years. It helps avoid framing AI-assisted DV as a completely new or unsupported direction.
- **Relevant to:**
  historical context, ML for verification, prior art support

---

## 3. Coverage Closure Intelligence

### Late Breaking Results: Test Selection For RTL Coverage By Unsupervised Learning From Fast Functional Simulation
- **Year:** 2023
- **Venue:** Design Automation Conference (DAC)
- **DOI:** <https://doi.org/10.1109/DAC56929.2023.10247936>
- **Why it matters:**
  This paper is highly relevant to coverage intelligence because it directly connects RTL coverage, test selection, and unsupervised learning. It is one of the strongest supports for the repository’s discussion of data-driven coverage planning and intelligent regression selection.
- **Relevant to:**
  coverage intelligence, RTL test selection, unsupervised guidance, regression planning

### Speed Up Functional Coverage Closure of CORDIC Designs Using Machine Learning Models
- **Year:** 2021
- **Venue:** IEEE ICM
- **DOI:** <https://doi.org/10.1109/ICM52667.2021.9664930>
- **Why it matters:**
  This paper directly supports the claim that ML can be used to accelerate coverage closure. Even if the target design class is narrow, it still provides concrete support for the repository’s argument that coverage closure is a practical and tractable AI-assistance target.
- **Relevant to:**
  coverage closure acceleration, hole prioritization, ML-guided verification effort

### Using Deep Neural Networks And Derivative Free Optimization To Accelerate Coverage Closure
- **Year:** 2021
- **Venue:** Workshop on Machine Learning for CAD (MLCAD)
- **DOI:** <https://doi.org/10.1109/MLCAD52597.2021.9531234>
- **Why it matters:**
  This is one of the more technically interesting references for optimization-driven coverage closure. It helps support the repository’s position that AI assistance in DV is not limited to summarization or classification, but can also include optimization of verification effort.
- **Relevant to:**
  coverage optimization, intelligent closure acceleration, ML-based search guidance

### Accelerated Design Verification Coverage Closure Using Machine Learning
- **Year:** 2025
- **Venue:** International Conference on VLSI Design
- **DOI:** <https://doi.org/10.1109/VLSID64188.2025.00070>
- **Why it matters:**
  This is a recent paper whose title is very closely aligned with the repository’s coverage-closure direction. It is useful as evidence that the topic continues to receive explicit attention in current literature.
- **Relevant to:**
  current ML-for-DV trends, coverage intelligence, modern relevance

---

## 4. Stimulus Optimization / Test Generation / RL-style Exploration

### Transaction Level Stimulus Optimization in Functional Verification Using Machine Learning Predictors
- **Year:** 2022
- **Venue:** IEEE International Symposium on Quality Electronic Design (ISQED)
- **DOI:** <https://doi.org/10.1109/ISQED54688.2022.9806210>
- **Why it matters:**
  This paper is particularly useful for the repository’s discussions of intelligent stimulus generation and test optimization. It supports the idea that AI can guide verification effort by influencing what gets exercised, not just by analyzing outputs afterward.
- **Relevant to:**
  stimulus intelligence, test optimization, verification planning

### Efficient Sequence Generation for Hardware Verification Using Machine Learning
- **Year:** 2021
- **Venue:** International Conference on Electronics, Circuits, and Systems
- **DOI:** <https://doi.org/10.1109/ICECS53924.2021.9665495>
- **Why it matters:**
  This paper provides supporting evidence for ML-guided generation of useful verification sequences. It aligns naturally with the repository’s interest in moving from passive analysis toward active verification optimization.
- **Relevant to:**
  sequence generation, intelligent verification stimulus, data-driven test creation

### Reinforcement-Learning Based Method for Accelerating Functional Coverage Closure of Traffic Light Controller Dynamic Digital Design
- **Year:** 2022
- **Venue:** International Conference on Computing: Theory and Applications (ICCTA)
- **DOI:** <https://doi.org/10.1109/ICCTA58027.2022.10206069>
- **Why it matters:**
  This paper is not the final word on RL for DV, but it is useful supporting evidence that reinforcement learning has already been explored in the context of functional coverage closure. That makes it a valuable reference for the repository’s TestForge RL direction.
- **Relevant to:**
  reinforcement learning for verification, reward-driven exploration, coverage-guided optimization

---

## 5. Test Selection / Prioritization

### Test Case Prioritization for Regression Testing Using Machine Learning
- **Year:** 2024
- **Venue:** IEEE International Conference on Artificial Intelligence Testing (AITest)
- **DOI:** <https://doi.org/10.1109/AITest62860.2024.00027>
- **Why it matters:**
  Although this paper is not RTL-verification-specific, it is still highly relevant for the repository’s regression-planning direction. It supports the broader idea that machine learning can prioritize tests under limited budget and improve regression efficiency.
- **Relevant to:**
  regression planning, ML-based test prioritization, budget-aware test selection

### Selection, Minimization and Prioritization of Test Cases for Regression Testing
- **Year:** 2011
- **Venue:** *Software Testing*
- **DOI:** <https://doi.org/10.1017/CBO9781139196185.008>
- **Why it matters:**
  This is a useful foundational reference for the broader problem of regression test selection. It helps show that the repository’s AI-based prioritization ideas build on a long-standing testing problem rather than inventing a problem that did not previously exist.
- **Relevant to:**
  historical grounding for regression planning, test selection foundations

### Survey of Test Case Prioritization Techniques for Regression Testing
- **Year:** 2014
- **Venue:** Journal of Software
- **DOI:** <https://doi.org/10.3724/SP.J.1001.2013.04420>
- **Why it matters:**
  Survey papers are useful supporting references because they help frame a topic area rather than only a specific method. This survey supports the idea that prioritization is a mature optimization problem to which AI can be meaningfully applied.
- **Relevant to:**
  background context, test prioritization literature, motivation for ML/RL extensions

---

## 6. Formal Verification + AI Adjacency

### Machine-Learning-Enabled Hardware Formal Verification
- **Type:** Thesis / dissertation-style reference
- **DOI:** <https://doi.org/10.14711/thesis-hdl167709>
- **Why it matters:**
  This is not the strongest citation in the entire shortlist, but it is directly relevant to the repository’s formal-verification-plus-AI direction. It is most useful as adjacency evidence showing that researchers are exploring the intersection between ML and formal hardware verification.
- **Relevant to:**
  formal + AI, property-oriented assistance, long-term expansion of the repository scope

---

## 7. Suggested Core Subset for This Repository

If only a small number of academic references are needed, the most directly useful subset is:

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

This subset gives the repository a compact but credible academic backbone across its most important themes.
