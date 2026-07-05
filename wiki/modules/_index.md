---
type: meta
title: "Modules Index"
updated: 2026-07-04
tags:
  - meta
  - index
  - module
  - industrial-brain
status: evergreen
related:
  - "[[index]]"
  - "[[domains/_index|Domains]]"
  - "[[Industrial Brain OS]]"
---

# Modules Index

Per-module / per-class notes for [[Industrial Brain OS]]. Each documents purpose,
responsibilities, dependencies, callers, downstream calls, related ADRs, and
milestones.

Navigation: [[index]] | [[domains/_index|Domains]] | [[Industrial Brain OS]]

## Backend Core
- [[Dependency Injection Container]] — the composition root

## Agents (the five brains)
- [[Base Brain Agent]] — shared LangGraph + citation foundation
- [[Knowledge Brain]] — grounded copilot (default chat)
- [[Maintenance Brain]] — work orders, failure history
- [[Compliance Brain]] — regulation-to-procedure gaps
- [[Root Cause Analysis Brain]] — 5-Whys / Ishikawa
- [[Lessons Learned Brain]] — incident pattern mining

## Quality
- [[E2E Validation Suite]] — Playwright + Chrome browser validation
