---
type: concept
title: "Citation Validation"
complexity: intermediate
domain: industrial-brain
aliases: []
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - grounding
status: mature
related:
  - "[[GraphRAG Pipeline]]"
  - "[[Base Brain Agent]]"
  - "[[Hallucination Gate]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Citation Validation

## Definition

The structural anti-hallucination step (stage 8 of the [[GraphRAG Pipeline]],
M14). The LLM is asked to cite evidence with `[[chunk:<chunk_id>]]` markers;
validation resolves each marker against the chunks actually retrieved and drops
any that do not match.

## How It Works

`validate_chunk_citations(text, retrieved_chunks)` (in [[Base Brain Agent]])
scans the answer for `[[chunk:<id>]]` markers, keeps only those whose id is in
the retrieved set (deduped), and builds `Citation` objects. `render_citations()`
then substitutes footnotes and appends a Sources block.

## Why It Matters

A hallucinated citation cannot survive: if the model invents a reference, the id
will not resolve and the citation is discarded. This is the per-answer guardrail
that complements the statistical [[Hallucination Gate]] in the
[[Evaluation Layer]].

> [!gap] The Knowledge Copilot answer can still contain prose-style references
> like `[source_1]` that are not the `[[chunk:...]]` marker, in which case no
> citation card renders. Aligning the generation prompt to always emit the
> canonical marker is a known improvement. See [[Troubleshooting (Industrial Brain)]].

## Connections

- Enforced by [[Base Brain Agent]]; measured by the [[Evaluation Layer]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/agents/base.py`
