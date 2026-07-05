---
type: module
title: "Knowledge Brain"
path: "backend/app/application/knowledge_brain/"
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
  - "[[GraphRAG Pipeline]]"
  - "[[Frontend Architecture]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Knowledge Brain

The grounded engineering copilot and the default chat experience. Answers
operational, maintenance, and engineering questions over the whole document
corpus with inline citations (M9).

## Purpose

Answer any question about the indexed industrial documents, grounded and cited,
never hallucinated.

## Responsibilities

- Retrieve evidence via the [[GraphRAG Pipeline]].
- Synthesize an answer with `[[chunk:<id>]]` citation markers.
- Validate and render citations ([[Citation Validation]]); drop unsupported ones.
- Stream tokens to the console over WebSocket.

## Dependencies

- [[Base Brain Agent]] ([[LangGraph]] `StateGraph`).
- [[GraphRAG Pipeline]] (`IGraphRAGEngine`), [[Ollama]] (`IModelGateway`),
  [[PromptOps]] (`knowledge_brain` prompt).

## Callers

- `KnowledgeBrainAgent` is invoked by the chat WebSocket `/api/v1/chat/stream`,
  which backs the [[Frontend Architecture|Knowledge Copilot]] screen.

## Downstream Calls

- [[Qdrant]] (vectors) + Postgres BM25 + [[Neo4j]] (graph) via the pipeline,
  then [[Ollama]] for generation.

## Related ADRs

- ADR-008 (GraphRAG), ADR-009 (Hybrid Retrieval), ADR-007 (LangGraph).

## Related Milestones

- M9. Extended by the full 8-stage pipeline in M14.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/knowledge_brain/`
