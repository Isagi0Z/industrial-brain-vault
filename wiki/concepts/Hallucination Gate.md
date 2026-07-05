---
type: concept
title: "Hallucination Gate"
complexity: intermediate
domain: industrial-brain
aliases: []
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - evaluation
status: mature
related:
  - "[[Evaluation Layer]]"
  - "[[Citation Validation]]"
  - "[[GraphRAG Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Hallucination Gate

## Definition

The CI merge gate that fails the build if answer groundedness regresses:
`hallucination_rate <= 0.15` over the golden dataset (M16). The statistical
half of the grounding story; the structural half is [[Citation Validation]].

## How It Works

`make eval` runs the golden Q&A set through the [[GraphRAG Pipeline]], scores the
fraction of answers with unsupported claims, and compares against
`docs/eval_baseline.json`. Above threshold, the [[Evaluation Layer]] blocks the
merge and the metric is also exported to Prometheus ([[Observability]]).

## Why It Matters

For [[Judge Q&A]], "never hallucinated" is a claim you can defend with a number,
not a promise. The gate keeps that number honest across changes to prompts
([[PromptOps]]), retrieval, or models.

## Connections

- Enforced by the [[Evaluation Layer]]; complements [[Citation Validation]].

## Sources

- [[Industrial Brain OS Repository]] — `scripts/run_eval.py`, `docs/eval_baseline.json`
