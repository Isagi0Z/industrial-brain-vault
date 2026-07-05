---
type: concept
title: "Context Compression"
complexity: intermediate
domain: industrial-brain
aliases:
  - "LLMLingua compression"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - retrieval
status: mature
related:
  - "[[GraphRAG Pipeline]]"
  - "[[LLMLingua]]"
  - "[[Hybrid Retrieval]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Context Compression

## Definition

Stage 7 of the [[GraphRAG Pipeline]] (M14): drop low-signal tokens from retrieved
context before it reaches the LLM, using [[LLMLingua]].

## How It Works

After reranking, the merged context can exceed a comfortable prompt budget.
LLMLingua scores token importance and prunes the least informative spans,
preserving the evidence needed to answer while cutting prompt size and latency.

## Why It Matters

- Keeps grounded answers affordable and fast on a local [[Ollama]] model.
- Lets [[Hybrid Retrieval]] cast a wide net (more candidates) without blowing the
  context window.

## Connections

- Runs between reranking and generation in the [[GraphRAG Pipeline]].
- Configurable via `LLMLINGUA_MODEL`.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/graphrag/llmlingua_compressor.py`
