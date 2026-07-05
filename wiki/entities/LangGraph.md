---
type: entity
title: "LangGraph"
entity_type: product
role: "Agent orchestration — brain state machines"
first_mentioned: "[[Base Brain Agent]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - agents
status: mature
related:
  - "[[Base Brain Agent]]"
  - "[[Intelligence Brains]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# LangGraph

## Overview

The agent-orchestration library used to build each brain as a `StateGraph`
(ADR-007).

## Key Facts

- Every brain is a graph of nodes (retrieve -> synthesize -> validate/render)
  with conditional edges for errors and step limits.
- The shared graph scaffolding lives in [[Base Brain Agent]].
- Chosen over an ad-hoc loop for explicit, testable control flow.

## Connections

- Underpins all of [[Intelligence Brains]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-007
