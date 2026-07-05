---
type: concept
title: "Entity and Relation Extraction"
complexity: advanced
domain: industrial-brain
aliases:
  - "NER"
  - "KG extraction"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - knowledge-graph
status: mature
related:
  - "[[Knowledge Graph]]"
  - "[[Industrial Ontology]]"
  - "[[spaCy]]"
  - "[[Ingestion Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Entity and Relation Extraction

## Definition

The pipeline stage that turns chunk text into typed [[Knowledge Graph]] nodes and
edges (M7): [[spaCy]] NER plus an LLM relation-extraction prompt, constrained by
the [[Industrial Ontology]].

## How It Works

`kg_task` (last stage of the [[Ingestion Pipeline]]) runs `ExtractionUseCase`:
1. `SpacyEntityExtractor` (`en_core_web_sm`) finds candidate entities.
2. A [[PromptOps]]-governed relation-extraction prompt proposes ontology-legal
   relations between them.
3. The `OntologyValidatorService` rejects anything off-schema.
4. Idempotent `MERGE` writes nodes/edges into [[Neo4j]].

Per-chunk failures are isolated: one bad chunk (e.g. an LLM timeout) is skipped,
never crashing the document.

## Why It Matters

This is how unstructured PDFs become a structured, traversable graph, which is
what makes stage 4 of the [[GraphRAG Pipeline]] and the graph view possible.

## Connections

- Target vocabulary: [[Industrial Ontology]]. Output store: [[Knowledge Graph]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/extraction/`
