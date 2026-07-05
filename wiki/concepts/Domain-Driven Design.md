---
type: concept
title: "Domain-Driven Design"
complexity: advanced
domain: industrial-brain
aliases:
  - "DDD"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - architecture
status: mature
related:
  - "[[Clean Architecture]]"
  - "[[Backend Architecture]]"
  - "[[Industrial Ontology]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Domain-Driven Design

## Definition

The modelling discipline behind the backend (ADR-014): the code is organised
around the industrial domain (documents, jobs, equipment, failure modes,
citations) with a shared ubiquitous language, not around technical layers alone.

## How It Works

Each bounded context (auth, document, chat, search, graph, each brain) has its
own `domain/` package with entities, value objects, and ports. Business rules
live in the domain and application layers; infrastructure only adapts.

## Why It Matters

- The ubiquitous language keeps the [[Industrial Ontology]], the API models, and
  the [[Knowledge Graph]] node types consistent.
- Bounded contexts keep the five [[Intelligence Brains]] loosely coupled.

## Connections

- Structural partner of [[Clean Architecture]].
- The graph vocabulary is formalised in the [[Industrial Ontology]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-014
