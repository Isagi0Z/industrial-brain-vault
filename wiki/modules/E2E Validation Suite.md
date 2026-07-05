---
type: module
title: "E2E Validation Suite"
path: "e2e/"
status: active
language: typescript
created: 2026-07-04
updated: 2026-07-04
tags:
  - module
  - industrial-brain
  - testing
related:
  - "[[Testing Strategy]]"
  - "[[Frontend Architecture]]"
  - "[[Authentication and Authorization]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# E2E Validation Suite

A Playwright suite that drives the real console in Google Chrome as a human
operator would (`e2e/`). Added post-M20.

## Purpose

Validate every observable workflow end-to-end through the browser, not via API
shortcuts.

## Responsibilities

- Cover auth / route guard / signup, full navigation, document upload -> ingest
  poll -> details -> delete, WebSocket-observed chat + citations, seeded
  [[Knowledge Graph]] render/inspect, the four brain panels, dark mode,
  responsive layouts, axe-core a11y, 404 / network-failure / multi-tab.
- Emit a report to `reports/e2e/` (summary, coverage matrix, screenshots,
  findings).

## Dependencies

- Playwright (`channel: 'chrome'`), `@axe-core/playwright`.
- A running backend + frontend (global-setup health-gates the backend and starts
  the frontend on a fixed port).

## Callers

- Run with `pnpm test` inside `e2e/`; report built by `scripts/build-report.mjs`.

## Related Milestones

- Post-M20 hardening; complements [[Testing Strategy]] and the [[Evaluation Layer]].

## Findings Surfaced

- 31/31 tests pass. Recorded findings: axe-core color-contrast (WCAG AA), no
  logout control, ingestion worker offline behaviour, brains-as-scaffolds. See
  [[Future Roadmap]] and [[Troubleshooting (Industrial Brain)]].

## Sources

- [[Industrial Brain OS Repository]] — `e2e/`, `reports/e2e/`
