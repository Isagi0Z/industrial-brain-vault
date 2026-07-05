---
type: concept
title: "Hybrid Retrieval"
complexity: advanced
domain: industrial-brain
aliases:
  - "Vector + BM25 + Graph"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - retrieval
status: mature
related:
  - "[[GraphRAG Pipeline]]"
  - "[[Qdrant]]"
  - "[[Knowledge Graph]]"
  - "[[Context Compression]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Hybrid Retrieval

## Definition

Combining three retrieval signals for one query (ADR-009): dense **vector**
search, sparse **BM25** keyword search, and **graph** traversal. The core of the
[[GraphRAG Pipeline]].

## How It Works

The query hits [[Qdrant]] (semantic), Postgres BM25 (lexical), and [[Neo4j]]
(related entities) in parallel; candidates are fused, deduped, then reranked by a
cross-encoder before compression and generation.

## Why It Matters

Industrial questions mix natural language with exact identifiers. Vectors match
paraphrase; BM25 nails exact tags like `P-102A`, `FM-BRG-01`, `ISO 14224`; the
graph adds neighbours the text never named (a pump's failure modes, its
governing procedure). No single method covers all three.

> [!key-insight] BM25 is not legacy baggage here. Exact equipment-tag recall is
> a hard requirement in industrial retrieval, and dense vectors are unreliable at
> it. That is why hybrid, not pure vector RAG, was chosen (ADR-008 / ADR-009).

## Connections

- Implemented by the [[GraphRAG Pipeline]].
- Followed by [[Context Compression]] and [[Citation Validation]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-008, ADR-009
