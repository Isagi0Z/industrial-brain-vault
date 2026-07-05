---
type: entity
title: "React"
entity_type: product
role: "Frontend UI library (React 18 + Vite)"
first_mentioned: "[[Frontend Architecture]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - frontend
status: mature
related:
  - "[[Frontend Architecture]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# React

## Overview

The UI library for the operator console (React 18 + Vite 6 + TypeScript,
ADR-002).

## Key Facts

- Routing via `react-router-dom` v6 with a pathless `RequireAuth` guard.
- Tailwind design system, `framer-motion` animations, `cytoscape` for the graph
  view, `react-pdf` for the document viewer.
- Dev server proxies `/api` to the backend; theme persisted to `localStorage`.

## Connections

- The whole [[Frontend Architecture]]; talks to
  [[API Reference (Industrial Brain)]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-002, `frontend/`
