---
type: entity
title: "Gemini"
entity_type: product
role: "Alternative cloud LLM gateway"
first_mentioned: "[[Ollama]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - llm
status: developing
related:
  - "[[Ollama]]"
  - "[[Intelligence Brains]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Gemini

## Overview

An alternative cloud LLM backend behind the same `IModelGateway` port as
[[Ollama]] (`GeminiGateway`).

## Key Facts

- Lets the platform swap local for cloud generation without touching brain logic
  ([[Clean Architecture]]).
- Uses the `google.generativeai` SDK, which is deprecated upstream (migrate to
  `google.genai`).
- [[Ollama]] is the default for on-premise data sovereignty.

## Connections

- Interchangeable model backend for [[Intelligence Brains]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/chat/gemini_gateway.py`
