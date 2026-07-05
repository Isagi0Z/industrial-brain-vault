---
type: entity
title: "MinIO"
entity_type: product
role: "S3-compatible object store — raw uploads"
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
sources:
  - "[[Industrial Brain OS Repository]]"
---

# MinIO

## Overview

S3-compatible object storage for raw uploaded files and processed artifacts
(ADR-006).

## Key Facts

- Buckets: `industrial-documents` (raw uploads), `processed-chunks`; created
  idempotently at startup.
- `POST /documents/` streams the raw file here before enqueuing ingestion.
- Download URLs are presigned; the console opens them in a new tab.

## Connections

- Source of truth for original files feeding the [[Ingestion Pipeline]]; part of
  the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-006
