# WaveScope MCP

Waveform-aware debug intelligence and root-cause acceleration.

---

## Problem Statement

Waveform debug is one of the most valuable but also one of the hardest places to apply AI in DV.

The difficulty is obvious:

- raw waveforms are large
- signal relationships are temporal
- the most important event is often the first divergence, not the final symptom
- useful interpretation requires RTL and protocol context

A large model cannot simply be handed a full waveform dump and expected to reason effectively.

## Why AI Helps

AI becomes useful here only after the data is structured. That means waveform-aware debug should focus on:

- event extraction
- suspicious signal detection
- timeline summarization
- protocol-aware reasoning
- root-cause hypothesis generation

## Core Idea

**WaveScope MCP** is a waveform/debug tool layer that gives large models a structured way to “see” verification waveforms.

It aims to:

- identify suspicious signals and transitions
- connect waveform anomalies to RTL logic context
- summarize event timelines
- propose likely root causes

## Typical Inputs

- waveform slices or extracted traces
- signal groups and hierarchy
- assertion failures
- protocol checker outputs
- transaction summaries
- relevant RTL context

## Typical Outputs

- suspicious signal list
- first-divergence summary
- event timeline
- candidate root-cause explanation
- suggested next debug steps

## Example AI-Assisted Capabilities

- “The first divergence appears on the write-response ready path after reset release.”
- “Signal X stays low longer than expected and likely stalls downstream handshaking.”
- “These three signals change consistently with a state-machine transition failure.”
- “The waveform symptom is likely downstream of an earlier protocol sequencing problem.”

## Engineering Challenges

- waveform scale and compression
- selecting the right signal subset
- aligning low-level signal changes with high-level transactions
- preventing overconfident but incorrect root-cause claims

## Evaluation Metrics

- time-to-first-useful-debug-hypothesis
- accuracy of suspicious signal localization
- reduction in waveform inspection effort
- engineer acceptance of generated root-cause summaries

## Position in the Stack

WaveScope MCP is likely not the very first project to implement, but it is one of the most strategically valuable long-term topics because waveform debug is where large amounts of expert engineering time are spent.
