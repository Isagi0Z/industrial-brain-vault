---
type: domain
title: "Future Roadmap"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - roadmap
status: developing
related:
  - "[[Industrial Brain OS]]"
  - "[[Development Timeline]]"
  - "[[Judge Q&A]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Future Roadmap

What is scaffolded versus shipped, and the next honest steps. Sourced from
findings in the [[E2E Validation Suite]] and [[Troubleshooting (Industrial Brain)]].

## Shipped

- M1-M20 (see [[Development Timeline]]): ingestion, GraphRAG, five brain agents,
  evaluation gate, observability, PromptOps, UI + graph visualizer.
- Post-M20: self-service signup, E2E validation, runnable local worker.

## Next (highest value first)

1. **Wire one specialist brain to interactive chat.** All five agents exist, but
   Maintenance / Compliance / RCA / Lessons Learned render as status panels
   (`scaffold: true`). Exposing a `/brain/{name}/chat` UI makes the vertical
   demonstrable. See [[Intelligence Brains]].
2. **RBAC role hydration.** `role_scope` exists as a parameter but every user
   resolves to `public`. Populate roles per user for role-scoped retrieval. See
   [[Authentication and Authorization]].
3. **Enforce `document_category`.** Replace the regulation-vs-procedure keyword
   heuristic with a classified field set at ingest time. See
   [[Compliance Brain]].
4. **Align citation markers.** Make the generation prompt always emit
   `[[chunk:<id>]]` so [[Citation Validation]] always renders a card.
5. **Accessibility.** Fix the WCAG-AA color-contrast on muted text flagged by
   axe-core; add an explicit logout control.
6. **OCR install path.** [[PaddleOCR]] is optional and currently absent; document
   / bundle it for scanned-document demos.

## Longer Horizon

- Predictive maintenance from sensor telemetry (beyond document evidence).
- Derivative outputs (compliance evidence packages, RCA reports as documents).
- Multi-tenant deployment hardening.

## Sources

- [[Industrial Brain OS Repository]] — `reports/e2e/suggestions.md`, `docs/`
