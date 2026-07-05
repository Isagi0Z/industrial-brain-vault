---
type: entity
title: "Celery"
entity_type: product
role: "Distributed task queue — async ingestion"
first_mentioned: "[[Ingestion Pipeline]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - ingestion
status: mature
related:
  - "[[Ingestion Pipeline]]"
  - "[[Event-Driven Ingestion]]"
  - "[[Redis]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Celery

## Overview

The distributed task queue that runs the async [[Ingestion Pipeline]] (ADR-015).
Broker and result backend are [[Redis]].

## Key Facts

- App: `app.worker` -> `app.infrastructure.celery.celery_app`. Tasks:
  `ingestion.parse`, `ingestion.embed`, `ingestion.kg`, dispatched as a `chain`.
- Default queue `ingestion`; `task_acks_late=True` re-delivers on worker death.
- Worker command: `celery -A app.worker worker -Q ingestion --pool=solo`
  (`--pool=solo` on Windows). Started locally via `python scripts/run_worker.py`,
  in production via the `ib_worker` container.
- Without a running worker, uploads stay `QUEUED` (a frequent local pitfall, see
  [[Troubleshooting (Industrial Brain)]]).

## Connections

- Realises [[Event-Driven Ingestion]]; brokered by [[Redis]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/celery/`
