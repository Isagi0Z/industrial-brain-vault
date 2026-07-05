---
type: concept
title: "Clean Architecture"
complexity: advanced
domain: industrial-brain
aliases:
  - "Ports and Adapters"
  - "Hexagonal Architecture"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - architecture
status: mature
related:
  - "[[Backend Architecture]]"
  - "[[Domain-Driven Design]]"
  - "[[Dependency Injection Container]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Clean Architecture

## Definition

The architectural style of the [[Industrial Brain OS]] backend (ADR-013):
concentric layers where source-code dependencies point only inward, toward the
domain. External concerns (frameworks, databases, LLMs) sit at the edge and are
reached through interfaces the inner layers define.

## How It Works

Four layers: `domain` (pure), `application` (use cases + agents), `infrastructure`
(adapters), `presentation` (FastAPI). The domain declares **ports**
(`interfaces.py`); infrastructure provides **adapters** that implement them; the
[[Dependency Injection Container]] wires adapters to ports at the composition
root. See [[Backend Architecture]] for the layer map.

## Why It Matters

- The domain has zero framework/DB imports, so use cases and the
  [[Intelligence Brains]] are unit-testable with plain fakes ([[Testing Strategy]]).
- Swapping an adapter (e.g. LLM gateway, vector store) never touches business
  logic.
- The rule is machine-enforced: `tests/test_architecture.py` fails CI if the
  domain imports outward.

## Examples

- `IGraphRAGEngine`, `IModelGateway`, `IQueueService`, repository ports are all
  domain interfaces with infrastructure implementations.

## Connections

- Pairs with [[Domain-Driven Design]] (ADR-014).
- Realised by the [[Dependency Injection Container]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-013
