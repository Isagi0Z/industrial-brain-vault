---
type: module
title: "Dependency Injection Container"
path: "backend/app/infrastructure/di/container.py"
status: active
language: python
created: 2026-07-04
updated: 2026-07-04
tags:
  - module
  - industrial-brain
  - backend
related:
  - "[[Backend Architecture]]"
  - "[[Clean Architecture]]"
  - "[[Ingestion Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Dependency Injection Container

`container.py` is the single composition root that wires ports to adapters for
the whole backend. It is the practical realisation of [[Clean Architecture]]:
nothing else constructs its own dependencies.

## Purpose

Build and cache every adapter, use case, and brain agent, injecting the right
implementations behind domain interfaces.

## Responsibilities

- Lazily construct DB clients (Postgres/Neo4j/Qdrant/Redis/MinIO), gateways
  (LLM, embedding), repositories, use cases, and the five [[Intelligence Brains]].
- Select the ingestion dispatcher from `INGESTION_BACKEND`
  (`CeleryQueueService` vs in-process `RedisQueueService`, see
  [[Ingestion Pipeline]]).
- Expose `get_*()` factories consumed by `main.py`, routers, and Celery tasks.

## Dependencies

- `infrastructure/config/settings.py` (env-driven Pydantic settings).
- Every infrastructure adapter.

## Callers

- `app/main.py`, all `presentation/api/v1` routers (via `Depends`), and the
  Celery tasks in the [[Ingestion Pipeline]].

## Downstream Calls

- Constructs all data clients ([[Data Layer]]) and LLM gateways ([[Ollama]]).

## Related ADRs

- ADR-013 (Clean Architecture), ADR-014 (DDD), ADR-015 (event-driven).

## Related Milestones

- M1 (introduced), then extended in nearly every milestone (it is the
  highest-churn file in the repo).

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/di/container.py`
