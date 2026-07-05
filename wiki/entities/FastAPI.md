---
type: entity
title: "FastAPI"
entity_type: product
role: "Backend web framework"
first_mentioned: "[[Backend Architecture]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - backend
status: mature
related:
  - "[[Backend Architecture]]"
  - "[[API Reference (Industrial Brain)]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# FastAPI

## Overview

The Python web framework for the backend (ADR-001), served by Uvicorn. Provides
the REST + WebSocket surface and auto-generated OpenAPI docs.

## Key Facts

- Routers live under `presentation/api/v1/`; middleware adds correlation ids and
  Prometheus metrics ([[Observability]]).
- Async lifespan verifies DB health and initialises infrastructure
  ([[Backend Architecture]]).
- WebSocket `/chat/stream` streams [[Knowledge Brain]] answers.
- OpenAPI snapshot committed at `docs/api/openapi.json`; live docs at `/docs`.

## Connections

- Hosts the [[API Reference (Industrial Brain)]] surface.

## Sources

- [[Industrial Brain OS Repository]] — ADR-001, `backend/app/main.py`
