---
type: module
title: "Root Cause Analysis Brain"
path: "backend/app/application/rca_brain/"
status: active
language: python
created: 2026-07-04
updated: 2026-07-04
tags:
  - module
  - industrial-brain
  - agents
related:
  - "[[Intelligence Brains]]"
  - "[[Base Brain Agent]]"
  - "[[Knowledge Graph]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Root Cause Analysis Brain

Reliability-engineering agent (M12). Guides structured root-cause investigations
using historical failure patterns and logical causality paths.

## Purpose

Support 5-Whys and Ishikawa/fishbone investigations grounded in real failure
evidence from the corpus and [[Knowledge Graph]].

## Responsibilities

- Build structured causal chains from a failure symptom.
- Pull historical failure correlations for the equipment involved.
- Cite the evidence behind each causal step.

## Dependencies

- [[Base Brain Agent]], [[GraphRAG Pipeline]], [[PromptOps]] (`rca_brain`).
- Session state (RCA sessions persisted via a repository, Redis live-state).

## Callers

- `RCABrainAgent` via DI. Console surfaces the Root Cause status panel
  (`/api/v1/rca/status`).

## Downstream Calls

- [[Knowledge Graph]] (Equipment -> FailureMode edges), [[Qdrant]], [[Ollama]].

## Related ADRs

- ADR-019 (multi-brain), ADR-008 (GraphRAG).

## Related Milestones

- M12.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/rca_brain/`, `infrastructure/rca/`
