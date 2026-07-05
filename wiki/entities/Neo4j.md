---
type: entity
title: "Neo4j"
entity_type: product
role: "Graph database — the industrial Knowledge Graph"
first_mentioned: "[[Knowledge Graph]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - database
status: mature
related:
  - "[[Knowledge Graph]]"
  - "[[Industrial Ontology]]"
  - "[[Data Layer]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Neo4j

## Overview

The graph database that stores the [[Knowledge Graph]] (Community edition,
ADR-004). Property-graph model, Cypher query language, Bolt driver.

## Key Facts

- Holds ontology-typed nodes and relations ([[Industrial Ontology]]).
- Uniqueness constraints on tag/code keys; range indexes for lookup.
- Traversed for stage 4 of the [[GraphRAG Pipeline]] and by the
  `/graph/subgraph` endpoint.
- Reached only through a domain port ([[Clean Architecture]]).

## Connections

- Written by [[Entity and Relation Extraction]]; read by the brains.
- Part of the [[Data Layer]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-004
