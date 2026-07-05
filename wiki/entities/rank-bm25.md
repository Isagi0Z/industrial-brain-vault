---
type: entity
title: "rank-bm25"
entity_type: product
role: "BM25 lexical scoring"
first_mentioned: "[[GraphRAG Pipeline]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - retrieval
status: mature
related:
  - "[[Hybrid Retrieval]]"
  - "[[GraphRAG Pipeline]]"
  - "[[PostgreSQL]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# rank-bm25

## Overview

The BM25 implementation behind the lexical arm of [[Hybrid Retrieval]] (stage 3
of the [[GraphRAG Pipeline]]).

## Key Facts

- Scores exact keyword overlap, which is essential for recalling equipment tags
  like `P-102A` that dense vectors miss.
- The index is materialised in a Postgres `bm25_index` table, rebuilt during
  `embed_task` ([[Ingestion Pipeline]]).

## Connections

- Complements [[Qdrant]] vectors and [[Neo4j]] traversal in [[Hybrid Retrieval]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/search/`
