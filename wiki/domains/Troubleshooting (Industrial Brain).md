---
type: domain
title: "Troubleshooting (Industrial Brain)"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - troubleshooting
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Ingestion Pipeline]]"
  - "[[Deployment]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Troubleshooting (Industrial Brain)

Real failure modes seen while running the platform, with fixes.

## Uploads stuck in QUEUED / never process

Most common local issue. With `INGESTION_BACKEND=celery` the API does not process
documents itself; a [[Celery]] worker must consume the `ingestion` queue. Start
it: `python scripts/run_worker.py` (auto-resolves the backend venv,
`--pool=solo` on Windows). Single-node alternative: set
`INGESTION_BACKEND=redis-queue` for an in-process worker. See
[[Ingestion Pipeline]].

## "No module named 'langgraph'" when starting the worker

The shell's `python` resolved to a global interpreter, not the backend venv.
`scripts/run_worker.py` now re-execs through `backend/venv/Scripts/python.exe`
regardless of PATH. Run it, do not call bare `celery`.

## Login 500: "password cannot be longer than 72 bytes"

passlib 1.7.4 introspects a bcrypt version attribute removed in bcrypt 4.1. Fix:
pin `bcrypt<4.1.0` in `requirements.txt` ([[Authentication and Authorization]]).

## Inter font 403 under `pnpm dev`

pnpm hoists workspace deps to the repo-root `node_modules`, outside the frontend
root, so Vite's `server.fs` rejected it. Fix: `server.fs.allow: ['..']` in
`vite.config.ts` ([[Frontend Architecture]]).

## Port already in use (8000 / 3000)

The backend requires 8000 (the frontend hardcodes `ws://host:8000` and proxies
`/api` there), so keep `autoPort:false` for it and free the port. The frontend
can use `autoPort` and take any free port ([[Deployment]]).

## Knowledge Graph view empty for a tag you know exists

Traversal MATCHes on exact `tag_number`. Confirm the tag format matches Neo4j
exactly, the document finished ingestion (`PROCESSED`, KG written in the last
stage), and try `depth=2` or `3`. See [[Knowledge Graph]].

## Chat answers but shows no citation card

The model emitted a prose-style `[source_1]` reference instead of the canonical
`[[chunk:<id>]]` marker, so [[Citation Validation]] produced no card. Aligning
the generation prompt is the fix ([[PromptOps]]).

## Qdrant / MinIO show "unhealthy" in docker ps

A strict container healthcheck quirk; both serve correctly. The app-level
`GET /health` is authoritative ([[Data Layer]]).

## Sources

- [[Industrial Brain OS Repository]] — `docs/manual/TROUBLESHOOTING.md`
