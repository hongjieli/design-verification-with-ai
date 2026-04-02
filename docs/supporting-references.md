# Supporting References for AI-Assisted Design Verification

This document collects external references that support the technical directions discussed in this repository. The goal is not to claim that every reference is a direct blueprint for AI-native design verification, but to show that the proposed ideas are grounded in real verification methodology, established ML techniques, and practical engineering workflows.

The references are grouped by topic and mapped to the major directions in this project:

- Regression Intelligence
- Coverage Intelligence
- Spec / Register Intelligence
- Test Optimization
- Debug Intelligence
- Verification Platform

---

## 1. Core References for Regression Intelligence

### Accellera UVM Standard
- **Source:** Accellera
- **Link:** <https://accellera.org/downloads/standards/uvm>
- **Why it matters:**
  UVM is one of the foundational verification methodologies behind the kinds of artifacts discussed throughout this repository: simulation logs, report messages, component hierarchy, scoreboards, monitors, drivers, and structured testbench behavior. Any proposal around AI-assisted regression triage becomes much more credible when rooted in an actual verification methodology rather than in abstract “AI for hardware” language.
- **Relevant to:**
  regression failure triage, failure classification, testbench-aware analysis, ownership inference

### UVM 1.2 Reference Documentation
- **Source:** Verification Academy
- **Link:** <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **Why it matters:**
  This reference helps ground discussions of UVM report mechanisms, verification components, and structured environments. It supports the argument that regression triage can consume well-defined verification artifacts rather than only raw ad hoc logs.
- **Relevant to:**
  regression intelligence, structured failure packets, verification-environment context

### scikit-learn Clustering Documentation
- **Source:** scikit-learn
- **Link:** <https://scikit-learn.org/stable/modules/clustering.html>
- **Why it matters:**
  Failure grouping and root-cause clustering do not need to rely solely on large language models. Classical clustering methods remain highly relevant for grouping similar failures, separating recurring patterns, and identifying coarse issue buckets before higher-level AI summarization is applied.
- **Relevant to:**
  failure clustering, root-cause grouping, novelty separation

### DBSCAN Documentation
- **Source:** scikit-learn
- **Link:** <https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html>
- **Why it matters:**
  DBSCAN is especially relevant for regression-failure analysis because verification data is noisy, cluster counts are usually unknown in advance, and some failures are outliers rather than members of well-formed groups. This makes it a useful conceptual and practical reference for “unique issue” discovery.
- **Relevant to:**
  duplicate reduction, outlier detection, novelty-oriented triage

### Sentence Transformers Documentation
- **Source:** Sentence Transformers
- **Link:** <https://www.sbert.net/>
- **Why it matters:**
  Many verification failures that share the same root cause do not have identical textual signatures. Embedding-based similarity methods are therefore a strong fit for semantic deduplication of failures, similarity search across historical regressions, and retrieval of related prior incidents.
- **Relevant to:**
  semantic failure similarity, historical retrieval, embedding-based clustering

### Faiss Documentation
- **Source:** Faiss
- **Link:** <https://faiss.ai/>
- **Why it matters:**
  Once a verification organization accumulates enough historical failures, bug reports, and issue summaries, similarity search at scale becomes important. Faiss provides a strong reference point for the retrieval side of a regression intelligence system.
- **Relevant to:**
  nearest-neighbor search, historical failure retrieval, known-issue matching

### LangChain Overview
- **Source:** LangChain
- **Link:** <https://docs.langchain.com/oss/python/langchain/overview>
- **Why it matters:**
  The repository discusses retrieval-augmented verification copilots and multi-stage AI workflows. LangChain is not a verification-specific framework, but it is a useful reference for how retrieval, tool use, summarization, and workflow orchestration can be composed in practice.
- **Relevant to:**
  retrieval-augmented triage, verification copilot flows, multi-step reasoning pipelines

---

## 2. Coverage Intelligence References

### Verification Academy – Coverage
- **Source:** Verification Academy
- **Link:** <https://verificationacademy.com/topics/coverage/>
- **Why it matters:**
  Coverage closure is one of the most time-consuming parts of verification, and this topic area helps validate that coverage analysis is a real and central engineering problem. It supports the repository’s position that AI can add value by summarizing holes, prioritizing gaps, and mapping coverage deficits back to features or RTL areas.
- **Relevant to:**
  coverage closure intelligence, hole prioritization, feature-to-coverage mapping

### IEEE Standards Portal via Accellera
- **Source:** Accellera
- **Link:** <https://www.accellera.org/downloads/ieee>
- **Why it matters:**
  This is a useful standards-oriented anchor for verification topics such as SystemVerilog, assertions, and related methodology foundations. It helps frame coverage and verification analysis as standard-grounded engineering domains rather than purely tool-driven practices.
- **Relevant to:**
  coverage-related methodology, assertion-aware verification, standards grounding

### PyUCIS Documentation
- **Source:** PyUCIS
- **Link:** <https://pyucis.readthedocs.io/en/latest/>
- **Why it matters:**
  Coverage intelligence becomes much more practical when metrics and results can be represented in structured form. PyUCIS is relevant because it points toward a programmatic, tool-friendly way to work with verification coverage data rather than treating reports only as static text.
- **Relevant to:**
  structured coverage analysis, coverage data pipelines, intelligence over coverage results

---

## 3. Spec / Register Intelligence References

### Accellera UVM Standard
- **Source:** Accellera
- **Link:** <https://accellera.org/downloads/standards/uvm>
- **Why it matters:**
  Register and specification intelligence ideas become much more credible when connected to established verification methodology. UVM is not a complete answer for spec understanding, but it is part of the real engineering ecosystem that register-related intelligence must eventually serve.
- **Relevant to:**
  register-oriented verification, methodology grounding, requirement-to-test interpretation

### UVM 1.2 Reference Documentation
- **Source:** Verification Academy
- **Link:** <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- **Why it matters:**
  This reference supports the broader context in which register/spec intelligence would be used: structured environments, reusable verification components, and methodology-aware automation.
- **Relevant to:**
  spec/register intelligence, structured verification integration

### PyVSC Documentation
- **Source:** PyVSC
- **Link:** <https://pyvsc.readthedocs.io/en/latest/>
- **Why it matters:**
  PyVSC is a useful engineering reference for constrained-random and structured verification modeling in Python. For spec/register intelligence, it helps bridge the gap between extracted intent and executable stimulus strategy.
- **Relevant to:**
  constraint extraction, legal-value modeling, intelligent stimulus planning

### NetworkX Documentation
- **Source:** NetworkX
- **Link:** <https://networkx.org/documentation/stable/>
- **Why it matters:**
  Several ideas in this repository, especially around register/spec intelligence, naturally map to graph representations: field dependencies, requirement relationships, register graphs, and traceability structures. NetworkX is a practical reference for building and analyzing such graphs.
- **Relevant to:**
  register dependency graphs, requirement graphs, traceability modeling

---

## 4. Test Optimization References

### RLlib Documentation
- **Source:** Ray RLlib
- **Link:** <https://docs.ray.io/en/latest/rllib/index.html>
- **Why it matters:**
  The test-optimization direction in this repository discusses budget-aware regression planning and reinforcement learning as a possible strategy. RLlib provides a serious reference point for scalable reinforcement learning systems and helps show that such a direction can be engineered rather than merely proposed conceptually.
- **Relevant to:**
  regression planning, adaptive test prioritization, reward-driven scheduling

### Gymnasium Documentation
- **Source:** Gymnasium
- **Link:** <https://gymnasium.farama.org/>
- **Why it matters:**
  Test selection under limited runtime budget can be framed as a state/action/reward problem. Gymnasium is useful as a reference because it provides the standard conceptual language for building such environments and evaluating policies.
- **Relevant to:**
  RL framing for regression planning, environment definition, reward design discussions

### pytest – Working with Custom Markers
- **Source:** pytest
- **Link:** <https://docs.pytest.org/en/stable/example/markers.html>
- **Why it matters:**
  Although this is not a hardware-verification reference, it is still useful because it illustrates that scoped test selection, tagging, and targeted execution are mature engineering concerns in software testing as well. That strengthens the broader argument that regression selection is a real systems problem, not a speculative AI problem.
- **Relevant to:**
  selective execution, test categorization, budget-aware planning analogies

---

## 5. Debug Intelligence / Assertions / Formal References

### Verification Academy – Formal Verification
- **Source:** Verification Academy
- **Link:** <https://verificationacademy.com/topics/formal-verification/>
- **Why it matters:**
  The formal-verification topic area supports the repository’s broader claim that AI can assist not only simulation-based triage, but also property-focused reasoning, proof interpretation, and structured debug support.
- **Relevant to:**
  formal + AI, property review, proof-result interpretation

### SymbiYosys Documentation
- **Source:** YosysHQ
- **Link:** <https://yosyshq.readthedocs.io/projects/sby/en/latest/>
- **Why it matters:**
  Formal workflows have naturally structured inputs and outputs: properties, assumptions, proofs, counterexamples, and statuses. This makes them especially compatible with AI-assisted explanation, summarization, and recommendation layers.
- **Relevant to:**
  formal result summarization, property-targeting support, AI-assisted proof workflow ideas

### PyEDA Documentation
- **Source:** PyEDA
- **Link:** <https://pyeda.readthedocs.io/en/latest/>
- **Why it matters:**
  For assertion generation or logic-oriented reasoning, it helps to reference tools and libraries that already operate over symbolic and Boolean structures. PyEDA is useful as a lower-level conceptual support point for logic-aware workflows.
- **Relevant to:**
  assertion/property support, symbolic reasoning, logic-level representation

---

## 6. Waveform / Trace-Aware Debug References

### OpenTelemetry Logs
- **Source:** OpenTelemetry
- **Link:** <https://opentelemetry.io/docs/concepts/signals/logs/>
- **Why it matters:**
  Waveform-aware and log-aware AI systems become much more realistic when they rely on structured events rather than raw unbounded text or raw waveform dumps. OpenTelemetry logs provide a strong reference point for structured observability thinking.
- **Relevant to:**
  event extraction, structured logging, normalized failure artifacts

### OpenTelemetry Traces
- **Source:** OpenTelemetry
- **Link:** <https://opentelemetry.io/docs/concepts/signals/traces/>
- **Why it matters:**
  The idea of causally connected timelines, first divergence, and event chains maps well onto debug intelligence for verification. While software tracing is not the same as waveform debug, the underlying abstraction is highly relevant.
- **Relevant to:**
  trace summarization, causal debug timelines, event-sequence reasoning

### Verilator User’s Guide
- **Source:** Verilator
- **Link:** <https://verilator.org/guide/latest/>
- **Why it matters:**
  Debug intelligence benefits from a realistic simulation and tracing context. Verilator is a useful open reference for the broader simulation/debug ecosystem in which trace-aware analysis can be built.
- **Relevant to:**
  waveform-aware tooling context, simulation outputs, engineering realism

### cocotb Documentation
- **Source:** cocotb
- **Link:** <https://docs.cocotb.org/en/stable/>
- **Why it matters:**
  cocotb is a practical reference for Python-driven verification orchestration. It is especially relevant when discussing AI-assisted workflows that may need to connect simulation runs, artifact extraction, and higher-level analysis in a flexible software-driven environment.
- **Relevant to:**
  Python-based verification workflows, debug data extraction, automation-friendly verification flows

---

## 7. Data Pipeline and Implementation References

### GitHub Actions – Store and Share Data with Workflow Artifacts
- **Source:** GitHub Docs
- **Link:** <https://docs.github.com/en/actions/tutorials/store-and-share-data>
- **Why it matters:**
  The regression-intelligence workflow described in this repository depends on collecting logs, reports, metadata, and summary artifacts after each run. This reference is useful for framing artifact collection and post-processing as standard pipeline engineering rather than as a custom side concern.
- **Relevant to:**
  regression data pipelines, artifact capture, automated reporting

### SQLite JSON Functions
- **Source:** SQLite
- **Link:** <https://www.sqlite.org/json1.html>
- **Why it matters:**
  The repository repeatedly emphasizes structured failure records and compact machine-usable representations. SQLite JSON support is a good practical reference for lightweight local prototypes and MVP-level storage.
- **Relevant to:**
  structured failure records, local prototyping, lightweight triage databases

### Apache Parquet Documentation
- **Source:** Apache Parquet
- **Link:** <https://parquet.apache.org/docs/>
- **Why it matters:**
  If regression intelligence expands into historical trend analysis, large-scale dataset mining, or model training, columnar storage becomes relevant. Parquet is therefore a useful reference for scalable historical analysis.
- **Relevant to:**
  historical triage datasets, analytics pipelines, large-scale result storage

---

## 8. Suggested Reading Priorities

If a reader wants the shortest path through the most relevant references, a practical starting set is:

1. Accellera UVM Standard
2. UVM 1.2 Reference Documentation
3. Verification Academy – Coverage
4. scikit-learn Clustering Documentation
5. DBSCAN Documentation
6. Sentence Transformers Documentation
7. Faiss Documentation
8. LangChain Overview
9. Verification Academy – Formal Verification
10. OpenTelemetry Logs and Traces
11. GitHub Actions – Store and Share Data
12. SQLite JSON Functions

This reading path roughly mirrors the architecture proposed in the repository:

- verification methodology foundation
- structured artifacts and data sources
- clustering and semantic similarity
- retrieval-augmented reasoning
- debug/formal adjacency
- implementation and data-pipeline realism

---

## 9. Notes on Scope

These references are intended to support feasibility, engineering realism, and technical framing. They do not claim that there is already a standardized, complete, off-the-shelf “AI for DV” stack. Instead, they show that the ideas explored in this repository can be grounded in:

- established verification methodology
- existing observability and data-pipeline practices
- mature clustering and retrieval techniques
- practical automation frameworks

That is exactly the kind of foundation needed for a credible AI-assisted design verification project.
