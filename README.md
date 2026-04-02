# Design Verification with AI

This repository explores practical ways to combine **AI** with **design verification (DV)**.

It covers a broader idea landscape including:
- regression failure triage
- coverage closure assistance
- register/spec intelligence
- reinforcement-learning-based test optimization
- multi-agent verification frameworks
- waveform-aware debug assistance

The main deep-dive currently focuses on **AI-assisted regression failure triage**, which is one of the most practical and measurable starting points for AI in DV.

## Documents

- [Detailed idea landscape and engineering notes](docs/design-verification-ai-ideas.md)
- [Supporting references (standards, tools, engineering docs)](docs/supporting-references.md)
- [Academic supporting papers shortlist](docs/academic-supporting-papers.md)
- [中文学术支持论文清单](zh/docs/academic-supporting-papers.md)

## Why this repo exists

Design verification teams generate large volumes of logs, reports, test data, coverage data, and documentation. AI is especially useful not as a replacement for verification engineers, but as a copilot for:

- triage
- summarization
- clustering
- prioritization
- traceability
- workflow acceleration

## Core idea categories

### 1. Regression / Failure Intelligence
AI-assisted regression failure triage, clustering, and root-cause summarization.

### 2. Coverage Intelligence
Coverage-hole analysis, RTL mapping, and closure suggestions.

### 3. Register / Spec Intelligence
Document parsing, register graphing, requirement traceability, and test recommendation.

### 4. Regression Optimization
RL-guided or learning-based test prioritization for better coverage efficiency.

### 5. Verification Platform Architecture
Multi-agent verification assistants that orchestrate specialized tools.

### 6. Waveform-Aware Debug
Structured waveform/event analysis to accelerate root-cause understanding.

## Best practical starting point

If building a first project in this space, the strongest starting direction is:

> **AI-assisted regression failure triage**

because it addresses a daily verification pain point, uses existing regression data, and delivers measurable engineering value without asking AI to replace signoff decisions.
