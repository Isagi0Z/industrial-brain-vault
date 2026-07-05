---
type: domain
title: "Judge Q&A"
created: 2026-07-04
updated: 2026-07-04
tags:
  - domain
  - industrial-brain
  - hackathon
status: mature
related:
  - "[[Industrial Brain OS]]"
  - "[[GraphRAG Pipeline]]"
  - "[[Evaluation Layer]]"
  - "[[Future Roadmap]]"
sources:
  - "[[Industrial Brain OS Repository]]"
---

# Judge Q&A

Hackathon evaluation prep. Judging criteria: Innovation 25, Business Impact 25,
Technical Excellence 20, Scalability 15, User Experience 15.

## Likely Questions and Crisp Answers

**How is this more than ChatGPT over PDFs?**
It is [[Hybrid Retrieval]] over a live [[Knowledge Graph]], not flat RAG. Vectors
+ BM25 + graph traversal recall exact equipment tags and their related entities,
then answers are cited and gated. See [[GraphRAG Pipeline]].

**How do you prevent hallucination?**
Two independent guardrails: [[Citation Validation]] drops any citation that does
not resolve to a retrieved chunk (per answer), and the [[Hallucination Gate]]
fails CI if `hallucination_rate > 0.15` over a golden set (aggregate). See
[[Evaluation Layer]].

**How do you handle exact identifiers like P-102A or ISO 14224?**
BM25 lexical matching ([[rank-bm25]]) plus graph tag lookup. Dense vectors alone
miss exact tags; that is why retrieval is hybrid, not pure vector.

**Why five brains instead of one prompt?**
Specialisation (ADR-019). Each brain has its own tools, prompt, and graph focus.
They share one correct foundation via [[Base Brain Agent]]. See
[[Intelligence Brains]].

**Is data private / on-premise?**
Yes. [[Ollama]], [[Neo4j]], [[Qdrant]], [[MinIO]] are all self-hosted; nothing
leaves the operator's network by default.

**How does it scale?**
Async [[Event-Driven Ingestion]] (Celery workers scale horizontally), stateless
API, polyglot [[Data Layer]] each sized to its job, full [[Observability]] to
find bottlenecks. Verified by benchmarks in M20.

**Is it production-grade or a prototype?**
[[Clean Architecture]] with a machine-enforced domain-purity test, 387 unit
tests, prompt validation, an evaluation gate, an [[E2E Validation Suite]]
(31/31), and a security audit (bandit + pip-audit). See [[Testing Strategy]].

## Honest Limitations (say them first)

- Four specialist brains render as status panels, not interactive chat yet.
- RBAC role hydration is a TODO (all users resolve to `public`).
- Regulation vs procedure is a title-keyword heuristic, not an enforced field.
See [[Future Roadmap]].

## Demo Path

Seed the graph (`make demo-data`), start the worker, upload a P-102A doc, watch
it reach `PROCESSED`, ask "rated discharge pressure of P-102A?", show the cited
answer, then open the [[Knowledge Graph]] view on `P-102A`.

## Sources

- [[Industrial Brain OS Repository]] — `docs/hackathon_problem_statement.md`
