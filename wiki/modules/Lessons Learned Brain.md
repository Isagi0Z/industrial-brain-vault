---
type: module
title: "Lessons Learned Brain"
path: "backend/app/application/lessons_learned_brain/"
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
  - "[[Knowledge Graph]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Lessons Learned Brain

Failure-intelligence agent (M13). Mines incident reports, near-miss records,
audit findings, and non-conformances for systemic patterns and pushes relevant
warnings.

## Purpose

Abstract operational knowledge from history into reusable lessons linked to
assets, and surface patterns invisible to any single review.

## Responsibilities

- Cluster and categorise incidents / near-misses.
- Link lessons to the assets and failure modes they concern.
- Return cited, actionable lessons.

## Dependencies

- [[Base Brain Agent]], [[GraphRAG Pipeline]], [[PromptOps]] (`lessons_learned_brain`).
- A dedicated Qdrant `lessons_learned` collection (role-scoped).

## Callers

- `LessonsLearnedBrainAgent` via DI. Console surfaces the Lessons Learned status
  panel (`/api/v1/lessons-learned/status`).

## Downstream Calls

- [[Knowledge Graph]] (LessonLearned nodes), [[Qdrant]], [[Ollama]].

## Related ADRs

- ADR-019 (multi-brain).

## Related Milestones

- M13.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/application/lessons_learned_brain/`
