# Design Verification with AI

This repository explores a structured portfolio of **AI-assisted design verification (DV)** topics.

Instead of treating AI for DV as a single monolithic idea, this repo organizes the space into several independent but related project directions:

- **CoverPilot** — coverage intelligence and closure guidance
- **RegMatrix** — register/spec intelligence and dynamic-constraint reasoning
- **TestForge RL** — reinforcement-learning-based test selection and coverage optimization
- **DVCore** — the agent foundation for AI-native DV workflows
- **WaveScope MCP** — waveform-aware debug intelligence

Together, these topics span a broad verification workflow, from document understanding and test planning to coverage analysis and waveform debug.

## Documents

- [Detailed idea landscape and engineering notes](docs/design-verification-ai-ideas.md)
- [Supporting references (standards, tools, engineering docs)](docs/supporting-references.md)
- [Academic supporting papers shortlist](docs/academic-supporting-papers.md)
- [中文学术支持论文清单](zh/docs/academic-supporting-papers.md)

## Why this repo exists

Design verification teams generate large volumes of logs, reports, test data, coverage data, waveforms, and documentation. AI is especially useful not as a replacement for verification engineers, but as a copilot for:

- triage
- summarization
- clustering
- prioritization
- traceability
- workflow acceleration

## Portfolio Structure

### 1. CoverPilot
Coverage-hole analysis, RTL mapping, and closure suggestions.

### 2. RegMatrix
Document parsing, register graphing, dynamic constraints, and test recommendation.

### 3. TestForge RL
RL-guided or learning-based test prioritization for better coverage efficiency.

### 4. DVCore
Agent framework, workflow execution, memory, and subagent routing for DV workflows.

### 5. WaveScope MCP
Structured waveform/event analysis to accelerate root-cause understanding.

## Suggested reading order

If you are new to the repo, a good reading path is:

1. `docs/design-verification-ai-ideas.md` — main topic-oriented overview
2. `docs/supporting-references.md` — standards, tools, and engineering references
3. `docs/academic-supporting-papers.md` — academic paper shortlist
4. `zh/docs/academic-supporting-papers.md` — Chinese academic paper version

## Best practical starting point

If building a first project in this space, the strongest starting directions are:

> **CoverPilot** and adjacent regression / coverage intelligence workflows

because they use existing DV artifacts, solve recurring engineering pain points, and are easier to measure than fully automated design-changing flows.
