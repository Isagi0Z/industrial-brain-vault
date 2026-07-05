---
type: domain
title: "Decision Log (Industrial Brain)"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - decisions
  - adr
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Development Timeline]]"
  - "[[Tech Stack]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Decision Log (Industrial Brain)

The 20 Architecture Decision Records (`docs/architecture_decision_records.md`).
These are authoritative; the architecture is never redesigned (project rule).

| ADR | Decision | Why (short) | Note |
|-----|----------|-------------|------|
| ADR-001 | [[FastAPI]] | async, type-safe, auto OpenAPI | [[Backend Architecture]] |
| ADR-002 | [[React]] + Vite | fast HMR, TS, modern UI | [[Frontend Architecture]] |
| ADR-003 | [[PostgreSQL]] | ACID relational system of record | [[Data Layer]] |
| ADR-004 | [[Neo4j]] Community | native property graph + Cypher | [[Knowledge Graph]] |
| ADR-005 | [[Qdrant]] | performant filterable vector DB | [[Qdrant]] |
| ADR-006 | [[MinIO]] | self-hosted S3-compatible object store | [[Data Layer]] |
| ADR-007 | [[LangGraph]] | explicit, testable agent state machines | [[Base Brain Agent]] |
| ADR-008 | [[GraphRAG Pipeline\|GraphRAG]] | graph + RAG for grounded retrieval | [[GraphRAG Pipeline]] |
| ADR-009 | [[Hybrid Retrieval]] | vector + BM25 + graph together | [[Hybrid Retrieval]] |
| ADR-010 | [[Industrial Ontology]] | typed, validated KG schema | [[Industrial Ontology]] |
| ADR-011 | [[PaddleOCR]] | strong OCR for technical documents | [[Document Parsing and OCR]] |
| ADR-012 | Layout-Aware Parsing | preserve tables/structure, not word soup | [[Document Parsing and OCR]] |
| ADR-013 | [[Clean Architecture]] | dependency inversion, testability | [[Backend Architecture]] |
| ADR-014 | [[Domain-Driven Design]] | model the industrial domain | [[Backend Architecture]] |
| ADR-015 | [[Event-Driven Ingestion\|Event-Driven Processing]] | async, resilient ingestion | [[Ingestion Pipeline]] |
| ADR-016 | [[OpenTelemetry]] | vendor-neutral distributed tracing | [[Observability]] |
| ADR-017 | Prometheus + Grafana | metrics + dashboards | [[Observability]] |
| ADR-018 | [[Docker]] | reproducible infra + deployment | [[Deployment]] |
| ADR-019 | Multi-Brain Architecture | specialised agents per domain | [[Intelligence Brains]] |
| ADR-020 | [[PromptOps]] | prompts as governed, versioned artifacts | [[PromptOps]] |

> [!key-insight] The through-line: choose self-hostable, on-premise components
> ([[Ollama]], [[Neo4j]], [[Qdrant]], [[MinIO]]) so an industrial operator keeps
> data sovereignty, and enforce grounding structurally ([[Citation Validation]])
> and statistically ([[Hallucination Gate]]).

## Sources

- [[Industrial Brain OS Repository]] — `docs/architecture_decision_records.md`
