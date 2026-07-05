---
type: module
title: "Maintenance Brain"
path: "backend/app/application/maintenance_brain/"
status: active
language: python
created: 2026-07-04
updated: 2026-07-04
tags:
  - module
  - industrial-brain
  - agents
related:
  - "[[Intelligence Brains]]"
  - "[[Base Brain Agent]]"
  - "[[Knowledge Graph]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Maintenance Brain

Operational maintenance agent (M10). Fuses work-order history, equipment failure
records, and OEM procedures to support diagnosis and maintenance decisions.

## Purpose

Answer maintenance questions (work orders, failure modes, equipment specs,
isolation/LOTO procedures) grounded in the corpus and [[Knowledge Graph]].

## Responsibilities

- Retrieve equipment-scoped evidence and traverse related failure modes /
  procedures / work orders in the graph.
- Synthesize a cited maintenance answer.

## Dependencies

- [[Base Brain Agent]], [[GraphRAG Pipeline]], [[PromptOps]] (`maintenance_brain`).

## Callers

- `MaintenanceBrainAgent` via its DI factory. In the console it currently
  surfaces as the Maintenance status panel (`/api/v1/maintenance/status`); the
  interactive chat endpoint is the [[Future Roadmap|next wiring step]].

## Downstream Calls

- [[Knowledge Graph]] traversal (equipment -> FailureMode / Procedure /
  Maintenance nodes), [[Qdrant]], [[Ollama]].

## Related ADRs

- ADR-019 (multi-brain), ADR-010 (ontology), ADR-008 (GraphRAG).

## Related Milestones

- M10.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/maintenance_brain/`, `ai/agents/`
