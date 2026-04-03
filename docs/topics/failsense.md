# FailSense

Regression failure triage, clustering, novelty detection, and ownership hints.

---

## Problem Statement

Large regressions often produce more information than engineers can efficiently digest:

- many failing tests are duplicates of the same issue
- visible symptoms differ across seeds and test scenarios
- ownership is unclear
- some failures come from design bugs, others from testbench, infra, or environment problems
- manual triage consumes significant engineering time

This creates a high-value opportunity for AI-assisted failure intelligence.

## Why AI Helps

Regression failure triage is a strong AI use case because it combines:

- semi-structured logs
- repetitive clustering tasks
- text similarity and semantic grouping
- prioritization and novelty detection

AI can help reduce the raw failure volume into a smaller number of engineer-actionable issue buckets.

## Core Idea

**FailSense** is a regression failure intelligence engine that:

- summarizes failures
- clusters related issues
- estimates novelty
- suggests probable ownership
- recommends next debug actions

## Typical Inputs

- simulation logs
- UVM reports
- assertion failures
- timeout indicators
- test metadata
- historical known-issue records

## Typical Outputs

- failure summaries
- issue clusters
- novelty and priority estimates
- ownership suggestions
- recommended next actions

## Example AI-Assisted Capabilities

- “These 47 failing tests likely collapse into 3 root-cause groups.”
- “This timeout appears related to a previously seen reset-sequencing issue.”
- “The most likely first owner is the DMA block team.”
- “This cluster is probably infra-related and should be filtered from design bug counts.”

## Engineering Challenges

- noisy logs and inconsistent failure formatting
- weak or missing historical labels
- semantic duplicates with different surface symptoms
- balancing explainability with model complexity

## Evaluation Metrics

- reduction in number of failure buckets engineers must inspect
- triage time saved per regression
- correctness of duplicate grouping
- accuracy of novelty and ownership suggestions

## References

- Clustering-based failure triage for RTL regression debugging — <https://doi.org/10.1109/TEST.2014.7035339>
- Machine Learning in the Service of Hardware Functional Verification — <https://doi.org/10.1007/978-3-031-13074-8_14>
- Data-Centric Machine Learning Pipeline for Hardware Verification — <https://doi.org/10.1109/SOCC56010.2022.9908095>
