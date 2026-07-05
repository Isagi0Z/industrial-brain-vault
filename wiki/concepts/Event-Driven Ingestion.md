---
type: concept
title: "Event-Driven Ingestion"
complexity: intermediate
domain: industrial-brain
aliases: []
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - ingestion
status: mature
related:
  - "[[Ingestion Pipeline]]"
  - "[[Celery]]"
  - "[[Redis]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Event-Driven Ingestion

## Definition

The decision to process documents asynchronously off an event queue rather than
synchronously in the request (ADR-015, M15). Uploading enqueues a job; a worker
does the heavy lifting.

## How It Works

`POST /documents/` stores the file, creates a job row, and dispatches a [[Celery]]
chain onto a [[Redis]] queue. The API returns 201 immediately. A worker consumes
the chain (`parse -> embed -> kg`) and updates job status. See
[[Ingestion Pipeline]].

## Why It Matters

- OCR, embedding, and extraction take seconds to minutes per document; blocking
  the request would time out and fail under load.
- `task_acks_late` re-delivers a task if a worker dies mid-job, so ingestion is
  crash-resilient.

> [!key-insight] The trade-off is operational: a worker must be running. With
> `INGESTION_BACKEND=celery` and no worker, uploads sit `QUEUED` forever. The
> single-node escape hatch is `INGESTION_BACKEND=redis-queue` (in-process
> worker). See [[Troubleshooting (Industrial Brain)]].

## Connections

- Realised by the [[Ingestion Pipeline]]; brokered by [[Redis]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-015
