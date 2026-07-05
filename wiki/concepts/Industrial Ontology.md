---
type: concept
title: "Industrial Ontology"
complexity: intermediate
domain: industrial-brain
aliases: []
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - knowledge-graph
status: mature
related:
  - "[[Knowledge Graph]]"
  - "[[Entity and Relation Extraction]]"
  - "[[Domain-Driven Design]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Industrial Ontology

## Definition

The formal schema of the [[Knowledge Graph]] (ADR-010):
`ontology/industrial_ontology.yaml`, defining 12 node types and 19 allowed
relations with required and optional properties.

## How It Works

`yaml_loader.py` loads and validates the file against a meta-schema (every node
type needs `required_properties`; every relation needs `source`/`relation`/`target`).
The `OntologyValidatorService` enforces it at KG write time, so only
schema-legal nodes and edges are persisted.

## Why It Matters

- Keeps the graph clean and queryable: an `Equipment` always has a `tag_number`,
  a `MONITORS` edge always runs Sensor -> Equipment.
- Gives [[Entity and Relation Extraction]] a fixed target vocabulary, reducing
  LLM drift.

## Examples

- Node types: `Asset`, `Equipment`, `Sensor`, `FailureMode`, `Procedure`,
  `Document`, `Regulation`, `Maintenance`, `Inspection`, `Personnel`, `Process`,
  `LessonLearned`.
- Relations: `MONITORS`, `IS_PART_OF`, `EXHIBITS`, `REQUIRES`, `REFERENCES`,
  `PERFORMED_BY`, and more.

## Connections

- Consumed by [[Entity and Relation Extraction]] and the [[Knowledge Graph]].

## Sources

- [[Industrial Brain OS Repository]] — `ontology/industrial_ontology.yaml`
