# RetailPulse

A simulated e-commerce data and AI platform, built in layers from scratch between November 2026 and 2029 as a learning capstone.

> **Status:** Phase 1 — Programming & SQL Foundations. Most of what's described below doesn't exist yet. This README is the map; the commits are the journey.

## What it will become
RetailPulse will ingest an operational orders database, clickstream events and product documents into a Databricks lakehouse on Azure, model them into a tested dbt star schema, score customer churn with MLflow-tracked models, and answer business and policy questions through an evaluated RAG assistant and a LangGraph analyst agent — deployed through CI/CD with governance, observability and cost controls.

## How this repo works
- **Sprint briefs** in `docs/sprints/` define each two-week sprint's goal, design and Definition of Done.
- **Every change** arrives through a pull request linked to a brief.
- **Every pull request** is reviewed by Claude against a rubric. Merging requires the `claude-approved` label on the latest commit (enforced by the `review-gate` workflow and branch protection).
- **Decisions** are recorded as ADRs in `docs/adr/`.

## Roadmap (high level)
| Phase | Focus | Target |
|---|---|---|
| 1 | Programming & SQL foundations | May 2027 |
| 2 | Data modeling & engineering foundations | Oct 2027 |
| 3 | Lakehouse core (PySpark, Databricks) | Mar 2028 |
| 4 | Azure platform & production DE | Sep 2028 |
| 5 | Streaming, governance, Fabric + Power BI | Dec 2028 |
| 6 | ML & LLM foundations | Feb 2029 |
| 7 | RAG & AI evaluation | Jun 2029 |
| 8 | Agents, serving & integration | Sep 2029 |
| 9 | Hardening | Nov 2029 |

## Progress log
See `docs/learning-log.md`.
