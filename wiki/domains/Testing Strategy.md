---
type: domain
title: "Testing Strategy"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - testing
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[Clean Architecture]]"
  - "[[E2E Validation Suite]]"
  - "[[Evaluation Layer]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Testing Strategy

Multiple layers of verification, each catching a different class of defect.

| Layer | What it checks | Where |
|-------|----------------|-------|
| Unit | use cases / agents with plain fakes | `backend/tests/` (387 passing) |
| Architecture | domain never imports outward (ADR-013) | `tests/test_architecture.py` |
| Prompt | every prompt validates + manifest matches disk | `tests/test_prompts.py` ([[PromptOps]]) |
| Evaluation | groundedness gate `hallucination_rate <= 0.15` | [[Evaluation Layer]] |
| End-to-end | real browser flows | [[E2E Validation Suite]] |
| Security | bandit + pip-audit + pnpm audit | `make security-audit` (M20) |

> [!key-insight] The architecture test is the load-bearing one: it makes
> [[Clean Architecture]] a machine-checked invariant, not a guideline. A PR that
> imports a DB driver into the domain layer fails CI.

## Conventions

- Unit tests mock domain ports with `SimpleNamespace`/plain classes, no heavy
  mock framework.
- On Windows, use `pytest --basetemp=C:\temp\pytest-tmp` to dodge a temp-dir ACL
  quirk (`WinError 5`).
- Frontend verification is `tsc --noEmit` + eslint + the browser suite.

## Sources

- [[Industrial Brain OS Repository]] — `backend/tests/`, `e2e/`
