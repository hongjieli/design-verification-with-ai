# JiraMine

Historical issue intelligence for mining JIRA and bug history to find test cases that are most likely to expose real RTL bugs.

## Problem Statement
Teams often have years of issue data in JIRA or similar bug trackers, but that history is rarely turned into regression strategy. In practice, some tests, sequences, configurations, and feature combinations repeatedly reveal meaningful RTL bugs, while others mostly consume cycles without producing new learning.

## Why AI Helps
This is a strong AI use case because bug history contains noisy natural language, partial labels, duplicate issues, ownership data, affected modules, and links to failing tests. AI can connect these signals and rank which test cases historically have the highest bug-discovery value.

## Core Idea
**JiraMine** is a historical issue mining engine that:
- links JIRA bugs to failing tests, features, modules, and regression contexts
- identifies tests and scenarios with unusually high bug yield
- separates one-off incidents from consistently valuable bug-finding patterns
- recommends high-value tests for smoke, sanity, or priority regressions
- explains why a test is considered bug-rich

## Typical Inputs
- JIRA tickets and bug summaries
- linked failing test names or regression jobs
- module / feature tags
- root-cause labels when available
- ownership and resolution metadata
- historical pass/fail and runtime data

## Typical Outputs
- ranked list of high-yield test cases
- feature/scenario clusters strongly associated with real bugs
- explanation of historical bug density by test or feature area
- suggested priority sets for future regressions
- candidate smoke tests for fast bug exposure

## Example AI-Assisted Capabilities
- “These 12 tests are linked to 38% of past cache-coherency RTL bugs.”
- “This scenario finds fewer failures overall, but the failures it finds are disproportionately true RTL issues rather than environment noise.”
- “Bugs in the DMA error path are strongly associated with three burst-stress sequences and two backpressure variants.”

## Engineering Challenges
- weak linkage between tickets and exact failing tests
- duplicate or low-quality bug records
- test renames and evolving regression structure
- separating bug-finding power from simple test popularity

## Evaluation Metrics
- bug yield per selected high-priority test
- percentage of important bugs exposed by the recommended subset
- time-to-first-real-bug in smoke or early regressions
- engineer acceptance of recommended high-value tests
