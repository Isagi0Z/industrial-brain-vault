---
type: entity
title: "LLMLingua"
entity_type: product
role: "Prompt/context compression"
first_mentioned: "[[Context Compression]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - retrieval
status: mature
related:
  - "[[Context Compression]]"
  - "[[GraphRAG Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# LLMLingua

## Overview

The compression library behind [[Context Compression]] (stage 7 of the
[[GraphRAG Pipeline]], M14).

## Key Facts

- Scores token importance and prunes low-signal spans from retrieved context.
- Configured via `LLMLINGUA_MODEL`; lazy-loaded on first use.
- Reduces prompt size and latency for the local [[Ollama]] model.

## Connections

- Runs between reranking and generation in the [[GraphRAG Pipeline]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/graphrag/llmlingua_compressor.py`
