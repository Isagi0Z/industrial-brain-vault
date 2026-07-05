---
type: domain
title: "Tech Stack"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - reference
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Decision Log (Industrial Brain)]]"
  - "[[Data Layer]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Tech Stack

Every major technology and the note that explains it. Rationale for each choice
is in the [[Decision Log (Industrial Brain)]].

| Layer | Technology | Note |
|-------|-----------|------|
| Backend framework | [[FastAPI]] + Uvicorn | [[Backend Architecture]] |
| Frontend | [[React]] 18 + Vite + TS + Tailwind | [[Frontend Architecture]] |
| Agents | [[LangGraph]] | [[Base Brain Agent]] |
| LLM | [[Ollama]] (llama3.2), [[Gemini]] optional | [[Intelligence Brains]] |
| Relational | [[PostgreSQL]] | [[Data Layer]] |
| Graph | [[Neo4j]] | [[Knowledge Graph]] |
| Vectors | [[Qdrant]] (bge-large 1024-d) | [[Qdrant]] |
| Keyword | [[rank-bm25]] (Postgres index) | [[Hybrid Retrieval]] |
| Reranker | BAAI/bge-reranker-large | [[GraphRAG Pipeline]] |
| Compression | [[LLMLingua]] | [[Context Compression]] |
| Cache / broker | [[Redis]] | [[Ingestion Pipeline]] |
| Object store | [[MinIO]] | [[Data Layer]] |
| Async tasks | [[Celery]] | [[Ingestion Pipeline]] |
| OCR | [[PaddleOCR]] + PyMuPDF | [[Document Parsing and OCR]] |
| NER | [[spaCy]] | [[Entity and Relation Extraction]] |
| Tracing | [[OpenTelemetry]] -> Jaeger | [[Observability]] |
| Metrics | Prometheus + Grafana | [[Observability]] |
| Containers | [[Docker]] Compose | [[Deployment]] |
| E2E tests | Playwright + Chrome | [[E2E Validation Suite]] |

## Languages and Contracts

Python 3.9 (backend), TypeScript (frontend), shared contract packages in
`shared/ts` and `shared/python` so the API surface stays consistent across the
boundary.

## Sources

- [[Industrial Brain OS Repository]] — `backend/requirements.txt`, `frontend/package.json`
