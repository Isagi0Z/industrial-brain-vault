---
type: entity
title: "Redis"
entity_type: product
role: "Cache + Celery broker + live state"
first_mentioned: "[[Ingestion Pipeline]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - database
status: mature
related:
  - "[[Ingestion Pipeline]]"
  - "[[Celery]]"
  - "[[Data Layer]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Redis

## Overview

In-memory store used as cache, [[Celery]] broker/result backend, and live-state
store (e.g. RCA sessions).

## Key Facts

- Logical DB 1 = Celery broker (queue `ingestion`), DB 2 = result backend
  ([[Ingestion Pipeline]]).
- The legacy in-process worker (`INGESTION_BACKEND=redis-queue`) consumes a Redis
  list `ingestion:jobs`.
- Also used by rate limiting and session/live state.

## Connections

- Broker for [[Event-Driven Ingestion]]; part of the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — `docker-compose.yml`, ADR-015
