---
type: entity
title: "PostgreSQL"
entity_type: product
role: "Relational store — users, documents, jobs, chunks, BM25"
first_mentioned: "[[Data Layer]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - database
status: mature
related:
  - "[[Data Layer]]"
  - "[[Ingestion Pipeline]]"
  - "[[Authentication and Authorization]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# PostgreSQL

## Overview

The relational system of record (ADR-003): users, documents, ingestion jobs,
chunks, and the BM25 keyword index.

## Key Facts

- Accessed via `psycopg2`; schema migrated with Alembic (`make db-migrate`).
- Stores the `bm25_index` table rebuilt during `embed_task`, powering the lexical
  arm of [[Hybrid Retrieval]].
- Holds document lifecycle status (`READY_FOR_PROCESSING` -> `PROCESSED`) and job
  stage tracking used by the [[Ingestion Pipeline]].

## Connections

- Backs [[Authentication and Authorization]] and document management.
- Part of the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-003
