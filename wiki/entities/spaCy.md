---
type: entity
title: "spaCy"
entity_type: product
role: "NLP / named-entity recognition"
first_mentioned: "[[Entity and Relation Extraction]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - knowledge-graph
status: mature
related:
  - "[[Entity and Relation Extraction]]"
  - "[[Knowledge Graph]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# spaCy

## Overview

The NLP library providing named-entity recognition for
[[Entity and Relation Extraction]] (model `en_core_web_sm`).

## Key Facts

- `SpacyEntityExtractor` finds candidate entities in each chunk before the LLM
  proposes ontology-legal relations.
- Fast, deterministic first pass that narrows what the LLM must reason about.

## Connections

- Feeds relation extraction into the [[Knowledge Graph]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/extraction/`
