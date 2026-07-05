---
type: entity
title: "Docker"
entity_type: product
role: "Containerisation / local infra + deployment"
first_mentioned: "[[Deployment]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - deployment
status: mature
related:
  - "[[Deployment]]"
  - "[[Data Layer]]"
  - "[[Ingestion Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Docker

## Overview

Containerisation for the whole stack (ADR-018). `docker-compose.yml` brings up
every dependency with one command.

## Key Facts

- Services: `ib_postgres`, `ib_neo4j`, `ib_qdrant`, `ib_redis`, `ib_minio`, plus
  `ib_jaeger`, `ib_prometheus`, `ib_grafana` ([[Observability]]).
- The backend image is shared by the API and the `ib_worker` container that runs
  the [[Celery]] worker for the [[Ingestion Pipeline]].
- `make up` / `make down` manage the infra services.

## Connections

- The substrate for [[Deployment]] and the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-018, `docker-compose.yml`
