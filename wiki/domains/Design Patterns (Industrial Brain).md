---
type: domain
title: "Design Patterns (Industrial Brain)"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - patterns
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Clean Architecture]]"
  - "[[Base Brain Agent]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Design Patterns (Industrial Brain)

Recurring engineering patterns across the codebase.

## Ports and Adapters

Every external system sits behind a domain interface (`I...`), implemented in
`infrastructure/`. See [[Clean Architecture]]. Enables fake-based unit tests.

## Composition Root

One [[Dependency Injection Container]] constructs and wires everything; no module
news up its own dependencies.

## Template Method (brains)

[[Base Brain Agent]] defines the shared LangGraph flow and citation helpers; each
brain overrides only its retrieve/synthesize specifics. See
[[Intelligence Brains]].

## Task Chain (ingestion)

`parse -> embed -> kg` [[Celery]] chain; each stage reuses its existing use case
rather than reimplementing logic. See [[Ingestion Pipeline]].

## Strategy (pluggable backends)

`INGESTION_BACKEND` swaps Celery vs in-process worker; `IModelGateway` swaps
[[Ollama]] vs [[Gemini]]. Behaviour changes by config, not code.

## Idempotent Writes

KG `MERGE`, `CREATE ... IF NOT EXISTS` migrations, and idempotent infra init let
startup and re-runs be safe. See [[Knowledge Graph]], [[Data Layer]].

## Graceful Degradation

Missing [[PaddleOCR]] -> figure chunks; per-chunk extraction failures skipped;
aborted API calls handled without a crash. Robustness over brittleness.

## Structural + Statistical Guardrails

Grounding enforced by [[Citation Validation]] (per answer) and the
[[Hallucination Gate]] (aggregate). Two independent checks, not one.

## Sources

- [[Industrial Brain OS Repository]] — `docs/engineering_bible.md`
