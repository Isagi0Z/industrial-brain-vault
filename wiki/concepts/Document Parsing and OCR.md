---
type: concept
title: "Document Parsing and OCR"
complexity: intermediate
domain: industrial-brain
aliases:
  - "Layout-aware parsing"
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - industrial-brain
  - ingestion
status: mature
related:
  - "[[Ingestion Pipeline]]"
  - "[[PaddleOCR]]"
  - "[[Document Parsing and OCR]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Document Parsing and OCR

## Definition

The first ingestion stage (M2 + M3): extract text from heterogeneous files, OCR
scanned/image content, respect layout, and split into chunks.

## How It Works

`parse_task` runs `DocumentParsingUseCase`:
- PyMuPDF extracts native text from PDFs; python-docx / openpyxl handle DOCX /
  XLSX; images go through OCR.
- Layout-aware parsing (ADR-012) preserves structure so tables and sections do
  not become word soup.
- [[PaddleOCR]] (ADR-011) handles scanned pages and image files; when PaddleOCR
  is unavailable the parser degrades gracefully, storing image pages as figure
  chunks.
- Output chunks are written to Postgres and handed to `embed_task`.

## Why It Matters

Industrial documents are messy: scanned P&IDs, spreadsheet logs, mixed-layout
manuals. Robust parsing + OCR is the difference between a searchable corpus and
noise.

> [!gap] In this environment PaddleOCR is not installed, so image-only pages
> become figure chunks rather than OCR text. Text PDFs (the demo corpus) parse
> fully.

## Connections

- Feeds embedding and [[Entity and Relation Extraction]] in the
  [[Ingestion Pipeline]].

## Sources

- [[Industrial Brain OS Repository]] — `backend/app/infrastructure/document/parsing/`
