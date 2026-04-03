# CoverPilot

Coverage intelligence for hole analysis, RTL mapping, and closure guidance.

---

## Problem Statement

Coverage closure is one of the most time-consuming activities in verification. Teams often face:

- large numbers of uncovered bins and scenarios
- weak visibility into why a hole still exists
- difficulty mapping coverage holes back to RTL structure or feature intent
- uncertainty about whether the fix should be a new test, a constraint change, a monitor change, or a coverage model update

Traditional coverage reports tell engineers what is missing, but they do not reliably explain what to do next.

## Why AI Helps

Coverage analysis is a strong AI target because it combines:

- structured data (coverage reports, hierarchy, test metadata)
- partial semantics (feature names, RTL blocks, coverage models)
- repetitive engineering reasoning

AI can help by turning raw coverage outputs into prioritized and explainable guidance.

## Core Idea

**CoverPilot** is a coverage intelligence agent that:

- analyzes coverage holes
- maps them to RTL hierarchy and feature context
- distinguishes black-box and white-box coverage reasoning
- prioritizes the most meaningful gaps
- suggests likely actions for closure

## Typical Inputs

- line/toggle/branch/FSM coverage
- functional coverage reports
- test metadata and pass/fail history
- RTL hierarchy and module ownership
- feature mapping or requirement tags
- prior closure notes or known exclusions

## Typical Outputs

- prioritized coverage-hole list
- probable RTL blocks related to each hole
- likely reasons a hole persists
- suggested next actions
- closure progress summaries

## Example AI-Assisted Capabilities

- “These five uncovered bins appear tied to the DMA descriptor corner case in burst mode.”
- “The missing hits are concentrated in logic under the AXI write-response path.”
- “This hole is more likely caused by over-constrained stimulus than by missing checker logic.”
- “The next best experiments are tests A, C, and F with relaxed constraint X.”

## Engineering Challenges

- incomplete mapping between coverage points and feature intent
- noisy or low-value coverage holes
- distinguishing unreachable holes from under-tested holes
- connecting coverage reports to actual verification actions

## Evaluation Metrics

- reduction in closure time
- number of useful closure suggestions accepted by engineers
- percentage of holes correctly mapped to relevant RTL/features
- reduction in manual coverage triage effort

## Position in the Stack

CoverPilot is one of the most practical near-term projects because coverage data already exists in most DV environments and the value of better closure guidance is easy to explain.
