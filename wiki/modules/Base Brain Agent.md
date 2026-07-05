---
type: module
title: "Base Brain Agent"
path: "backend/app/application/agents/base.py"
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
  - "[[LangGraph]]"
  - "[[GraphRAG Pipeline]]"
  - "[[Citation Validation]]"
  - "[[PromptOps]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Base Brain Agent

`BaseBrainAgent` (`app/application/agents/base.py`) is the shared foundation every
brain subclasses. It exists so the five [[Intelligence Brains]] share one correct
implementation of prompt loading, context formatting, citation handling, and
error/step-limit control instead of five drifting copies.

## Purpose

Provide the common LangGraph scaffolding and the shared citation/prompt helpers
for all brain agents.

## Responsibilities

- Step-limit guard (bounded reasoning loops).
- `error_or(default=...)` conditional edge selector for the LangGraph state machine.
- Shared helpers: `load_prompt()`, `format_context_blocks()`,
  `validate_chunk_citations()`, `render_citations()`.
- Enforce the `[[chunk:<id>]]` citation marker convention ([[Citation Validation]]).

## Dependencies

- [[LangGraph]] (`StateGraph`) for the agent graph.
- [[PromptOps]] for prompt loading.
- The domain search models (`SearchResult`, `Citation`).

## Callers

- [[Knowledge Brain]], [[Maintenance Brain]], [[Compliance Brain]],
  [[Root Cause Analysis Brain]], [[Lessons Learned Brain]] (all subclass it).

## Downstream Calls

- [[GraphRAG Pipeline]] (`IGraphRAGEngine`) for retrieval.
- `IModelGateway` -> [[Ollama]] for generation.

## Related ADRs

- ADR-007 (LangGraph), ADR-019 (multi-brain), ADR-008 (GraphRAG). See
  [[Decision Log (Industrial Brain)]].

## Related Milestones

- M9 (introduced with the [[Knowledge Brain]]), reused in M10-M13. See
  [[Development Timeline]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/agents/base.py`
