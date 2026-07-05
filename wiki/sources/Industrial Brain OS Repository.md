---
type: source
title: "Industrial Brain OS Repository"
source_type: repository
author: "Isagi0Z"
date_published: 2026-07-04
url: "https://github.com/Isagi0Z/industrial-brain-os"
confidence: high
created: 2026-07-04
updated: 2026-07-04
tags:
  - source
  - industrial-brain
  - repository
status: evergreen
related:
  - "[[Industrial Brain OS]]"
  - "[[Backend Architecture]]"
  - "[[Development Timeline]]"
key_claims:
  - "FastAPI + React monorepo with shared TS/Python contracts"
  - "Hybrid GraphRAG over Neo4j + Qdrant with five LangGraph brain agents"
  - "20 milestones (M1-M20), 20 ADRs, 387 backend tests"
---

# Industrial Brain OS Repository

The canonical source for the entire [[Industrial Brain OS]] knowledge base. All
subsystem notes in this vault are synthesized from this repository.

## Key Facts

- **Location**: `D:\industrial-brain` (working branch `feature/bootstrap`).
- **Remote**: `github.com/Isagi0Z/industrial-brain-os`.
- **Shape**: monorepo. `backend/` (FastAPI, Python 3.9 venv), `frontend/`
  (React + Vite + TS), `shared/` (TS + Python contract packages), `docs/`,
  `ontology/`, `scripts/`, `e2e/` (Playwright validation), `demo_data/`.
- **Docs of record**: `docs/industrial_brain_architecture_v2.md`,
  `docs/engineering_bible.md`, `docs/architecture_decision_records.md`
  (see [[Decision Log (Industrial Brain)]]),
  `docs/implementation_roadmap.md` (see [[Development Timeline]]),
  `docs/manual/` (10-file professional manual).
- **Repo intelligence**: indexed by RepoWise; `.claude/CLAUDE.md` documents MCP
  tooling for orientation.

## Structure

```
industrial-brain/
├── backend/app/{domain,application,infrastructure,presentation}/
├── frontend/src/{components,pages,router,context}/
├── shared/{ts,python}/
├── ontology/industrial_ontology.yaml
├── docs/{architecture,manual,walkthroughs,verification,reports}/
├── e2e/                # Playwright + Chrome validation suite
└── demo_data/          # 10 P-102A industrial PDFs
```

## Connections

- Architecture map: [[Backend Architecture]], [[Frontend Architecture]]
- Build history: [[Development Timeline]]
- Decisions: [[Decision Log (Industrial Brain)]]

## Sources

- Self (primary source).
