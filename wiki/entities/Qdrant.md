---
type: entity
title: "Qdrant"
entity_type: product
role: "Vector database — chunk embeddings"
first_mentioned: "[[GraphRAG Pipeline]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - database
status: mature
related:
  - "[[GraphRAG Pipeline]]"
  - "[[Data Layer]]"
  - "[[Hybrid Retrieval]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Qdrant

## Overview

The vector store for chunk embeddings (ADR-005). Powers semantic retrieval,
stage 2 of the [[GraphRAG Pipeline]].

## Key Facts

- Embeddings are 1024-dimensional (`BAAI/bge-large-en-v1.5`).
- Collections: `document_chunks` (main corpus) plus role-scoped collections such
  as `lessons_learned`; payload indexes on `chunk_type`, `role_scope`,
  `document_id`.
- Collections created idempotently by `scripts/init_infra.py` / startup lifespan.
- Changing the embedding model requires dropping and recreating the collection
  (vector dimension change).

## Connections

- Written by `embed_task` ([[Ingestion Pipeline]]); read via [[Hybrid Retrieval]].
- Part of the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-005
