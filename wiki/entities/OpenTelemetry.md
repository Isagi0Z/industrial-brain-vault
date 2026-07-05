---
type: entity
title: "OpenTelemetry"
entity_type: product
role: "Distributed tracing (traces to Jaeger)"
first_mentioned: "[[Observability]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - observability
status: mature
related:
  - "[[Observability]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# OpenTelemetry

## Overview

The tracing standard used for distributed traces (ADR-016), exported to Jaeger
via OTLP/HTTP. Part of [[Observability]].

## Key Facts

- FastAPI auto-instrumentation plus explicit spans on each ingestion stage
  (`celery.parse_task` / `embed_task` / `kg_task`).
- No-op unless `OTEL_ENABLED=true`; Jaeger UI on port 16686.
- Spans carry the request correlation id, joining API and worker traces.

## Connections

- One of the three signals in [[Observability]] (with Prometheus + logs).

## Sources

- [[Industrial Brain OS Repository]] — ADR-016
