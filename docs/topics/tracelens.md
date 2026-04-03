# TraceLens

Spec-to-test and requirement-to-coverage traceability intelligence.

---

## Problem Statement

One of the hardest management and engineering problems in verification is traceability:

- which requirements map to which tests
- which features are under-covered
- which coverage holes have no clear requirement linkage
- which tests still provide value and which have become redundant

Without strong traceability, DV knowledge becomes fragmented across documents, tests, coverage reports, and engineer memory.

## Why AI Helps

Traceability is a good AI target because it requires connecting multiple semi-structured sources:

- specification language
- test descriptions
- coverage models
- verification reports
- feature and block metadata

AI can help build and maintain these mappings more effectively than purely manual linking.

## Core Idea

**TraceLens** is a traceability intelligence layer that connects:

- requirement to test
- requirement to coverage
- register/spec features to verification intent
- historical execution evidence to verification planning

## Typical Inputs

- requirements/spec documents
- test plans and test descriptions
- coverage points and UCIS-style data
- historical regression outputs
- feature tags and ownership metadata

## Typical Outputs

- requirement-to-test mapping
- requirement-to-coverage mapping
- missing-verification-gap reports
- traceability dashboards
- suggestions for redundant or low-value tests

## Example AI-Assisted Capabilities

- “This requirement appears to be only partially covered by current tests.”
- “These coverage bins have no obvious requirement linkage and may reflect model drift.”
- “This register feature has implementation tests but no end-to-end validation trace.”
- “These tests appear redundant with respect to current feature traceability goals.”

## Engineering Challenges

- incomplete or weakly written requirements
- mismatch between feature language and test naming
- coverage models that drift away from current spec intent
- maintaining traceability as specs and tests evolve

## Evaluation Metrics

- completeness of requirement linkage
- reduction in orphaned coverage points
- usefulness of gap reports
- engineer confidence in generated traceability mapping

## References

- PyUCIS Documentation — <https://pyucis.readthedocs.io/en/latest/>
- Accellera UVM Standard — <https://accellera.org/downloads/standards/uvm>
- Data-Centric Machine Learning Pipeline for Hardware Verification — <https://doi.org/10.1109/SOCC56010.2022.9908095>
- Verification Academy – Coverage — <https://verificationacademy.com/topics/coverage/>
