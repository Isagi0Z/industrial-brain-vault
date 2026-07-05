---
type: entity
title: "PaddleOCR"
entity_type: product
role: "OCR engine for scanned pages and images"
first_mentioned: "[[Document Parsing and OCR]]"
created: 2026-07-04
updated: 2026-07-04
tags:
  - entity
  - industrial-brain
  - ingestion
status: developing
related:
  - "[[Document Parsing and OCR]]"
  - "[[Ingestion Pipeline]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# PaddleOCR

## Overview

The OCR engine for scanned documents and image files (ADR-011), part of
[[Document Parsing and OCR]].

## Key Facts

- Chosen for strong performance on dense, technical, mixed-language documents.
- Optional at runtime: when unavailable the parser degrades gracefully, storing
  image pages as figure chunks rather than failing.
- Not installed in the current dev environment; text PDFs still parse fully.

## Connections

- Invoked by `parse_task` in the [[Ingestion Pipeline]].

## Sources

- [[Industrial Brain OS Repository]] — ADR-011
