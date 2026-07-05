---
type: entity
title: "Ollama"
entity_type: product
role: "Local LLM runtime (llama3.2)"
first_mentioned: "[[GraphRAG Pipeline]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - llm
status: mature
related:
  - "[[GraphRAG Pipeline]]"
  - "[[Intelligence Brains]]"
  - "[[Gemini]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Ollama

## Overview

The local LLM runtime serving generation for the brains (model `llama3.2`).
Keeps inference on-premise, which suits industrial data-sovereignty needs.

## Key Facts

- Reached through the `IModelGateway` port; the concrete `OllamaGateway` streams
  tokens for the WebSocket chat.
- Model shows as `ollama/llama3.2` in `token_usage`.
- A [[Gemini]] gateway exists as an alternative model backend (the
  `google.generativeai` SDK is deprecated upstream).
- First-token latency reflects model warm-up on CPU.

## Connections

- Generation engine for the [[GraphRAG Pipeline]] and every brain.

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/chat/ollama_gateway.py`
