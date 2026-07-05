---
type: module
title: "Compliance Brain"
path: "backend/app/application/compliance_brain/"
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
  - "[[Industrial Ontology]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Compliance Brain

Automated safety/quality agent (M11). Maps regulatory requirements against
current procedures, equipment states, and inspection records to flag compliance
gaps with reviewer-ready evidence.

## Purpose

Detect regulation-to-procedure gaps (OSHA, OISD, PESO, environmental, quality
standards) and produce cited evidence.

## Responsibilities

- Distinguish regulation text from procedure text and compare them.
- Surface gaps and cite the regulation + procedure involved.

## Dependencies

- [[Base Brain Agent]], [[GraphRAG Pipeline]], [[PromptOps]] (`compliance_brain`).

## Callers

- `ComplianceBrainAgent` via DI. Console surfaces the Compliance status panel
  (`/api/v1/compliance/status`).

## Downstream Calls

- [[Knowledge Graph]] (Regulation / Procedure / Document nodes), [[Qdrant]],
  [[Ollama]].

## Related ADRs

- ADR-019 (multi-brain), ADR-010 (ontology).

## Related Milestones

- M11.

> [!gap] Regulation vs procedure is distinguished at retrieval time by a
> title-keyword heuristic (`_looks_like_regulation`), not an enforced
> `document_category` field. Upload regulations with a keyword-bearing title
> (e.g. "OSHA 1910.119"). See [[Troubleshooting (Industrial Brain)]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/compliance_brain/`, `ai/agents/compliance_brain/`
