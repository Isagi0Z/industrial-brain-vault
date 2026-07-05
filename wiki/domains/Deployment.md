---
type: domain
title: "Deployment"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - deployment
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Docker]]"
  - "[[Ingestion Pipeline]]"
  - "[[Data Layer]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Deployment

The platform runs as a [[Docker]] Compose stack plus three application processes.

## Compose Services

```mermaid
flowchart TB
  subgraph Data
    PG[(ib_postgres)]
    NE[(ib_neo4j)]
    QD[(ib_qdrant)]
    RD[(ib_redis)]
    MI[(ib_minio)]
  end
  subgraph Telemetry
    JA[ib_jaeger]
    PR[ib_prometheus]
    GR[ib_grafana]
  end
  API[ib_backend / uvicorn] --> Data
  WK[ib_worker / celery] --> Data
  API --> Telemetry
```

## Local Dev (three processes)

`make dev` documents the three terminals required:

1. Backend: `uvicorn app.main:app --reload`
2. Worker: `python scripts/run_worker.py` (REQUIRED for ingestion, see
   [[Ingestion Pipeline]])
3. Frontend: `pnpm dev`

Infra first: `make up` (compose), then `make db-migrate` and
`python scripts/init_infra.py`.

> [!key-insight] The worker is a first-class process, not optional. In
> production the `ib_worker` container runs it; locally it must be started by
> hand. Forgetting it is the top cause of "uploads stuck in QUEUED" (see
> [[Troubleshooting (Industrial Brain)]]).

## Reset

- Soft: `make db-reset`.
- Hard: `docker compose down -v && docker compose up -d`, re-migrate, re-init.

## Sources

- [[Industrial Brain OS Repository]] — `docker-compose.yml`, `Makefile`, `docs/manual/DEPLOYMENT.md`
