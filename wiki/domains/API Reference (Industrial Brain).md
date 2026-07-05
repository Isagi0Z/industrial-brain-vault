---
type: domain
title: "API Reference (Industrial Brain)"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - api
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[FastAPI]]"
  - "[[Authentication and Authorization]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# API Reference (Industrial Brain)

Base URL `http://localhost:8000/api/v1`. Live docs at `/docs`; a snapshot is
committed at `docs/api/openapi.json` (33 paths). Full field schemas are best read
from `/docs`.

## Auth

See [[Authentication and Authorization]]: `POST /auth/login` (form),
`POST /auth/register` (json), `POST /auth/refresh`, `POST /auth/logout`,
`GET /auth/me`. All other routes need `Authorization: Bearer <access>`.

## Documents

| Method | Path | Purpose |
|--------|------|---------|
| POST | `/documents/` | upload (multipart) -> enqueue [[Ingestion Pipeline]] |
| GET | `/documents/?limit=&status=` | list with status |
| GET | `/documents/{id}` | detail |
| GET | `/documents/{id}/status` | job stage / error |
| GET | `/documents/{id}/download` | presigned URL |
| POST | `/documents/{id}/retry` | re-queue ingestion |
| DELETE | `/documents/{id}` | delete |

## Knowledge Graph and Health

- `GET /graph/subgraph?entity_tag=&depth=1..3` -> nodes + edges ([[Knowledge Graph]]).
- `GET /health` -> per-datastore status ([[Data Layer]]).
- `GET /{brain}/status` -> brain scaffold status ([[Intelligence Brains]]).

## Chat (WebSocket)

`WS /api/v1/chat/stream?token=<jwt>`: send `{query, session_id, top_k, role_scope}`;
receive `token` frames, then a `done` frame carrying `citations` and
`token_usage` ([[Knowledge Brain]], [[GraphRAG Pipeline]]).

## Sources

- [[Industrial Brain OS Repository]] — `docs/api/openapi.json`, `docs/manual/API_REFERENCE.md`
