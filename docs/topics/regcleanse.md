# RegCleanse

Regression-history intelligence for finding low-yield test cases that almost always pass and contribute little new verification value.

## Problem Statement
Large regressions accumulate legacy tests over time. Some tests were once important but now almost never fail, add little unique coverage, and consume disproportionate compute budget. Teams know this happens, but retiring tests is hard because the evidence is scattered across historical runs.

## Why AI Helps
AI can combine regression history, pass-rate trends, coverage contribution, bug linkage, and feature overlap to identify tests that appear consistently low-yield. This supports disciplined cleanup instead of keeping every historical test forever.

## Core Idea
**RegCleanse** is a regression cleanup intelligence engine that:
- identifies tests with extremely stable pass history and low unique bug yield
- measures overlap with other tests in feature, coverage, and failure profile
- recommends retirement, reduced frequency, lighter configs, or trigger-based execution
- highlights where a test still has value despite low failure rates
- produces explainable evidence before regression pruning decisions

## Typical Inputs
- long-term regression pass/fail history
- coverage contribution by test or test cluster
- historical bug links
- runtime and farm-cost data
- feature tags and scenario labels
- regression scheduling policies

## Typical Outputs
- ranked list of low-yield candidate tests
- overlap analysis showing redundant test groups
- recommendations for retire/demote/weekly-only/on-change execution
- estimated compute savings with expected risk tradeoff
- watchlist of tests that should not be removed despite low fail rate

## Example AI-Assisted Capabilities
- “These 27 tests have passed for 14 months, add minimal unique coverage, and overlap heavily with a stronger nightly subset.”
- “This test almost never fails, but it still covers a unique recovery path and should be kept at lower frequency rather than removed.”
- “Retiring this redundant cluster would save 11% regression runtime with negligible expected bug-loss risk.”

## Engineering Challenges
- avoiding removal of rare-but-critical tests
- incomplete coverage attribution by individual test
- policy resistance to regression pruning
- distinguishing low yield from long-tail protection value

## Evaluation Metrics
- compute/runtime savings after cleanup
- retained bug-detection rate after pruning or demotion
- retained unique coverage after optimization
- engineer trust in cleanup recommendations
