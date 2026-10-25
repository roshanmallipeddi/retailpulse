# Sprint 02 — "Loops and first queries"

**Phase:** 1 — Programming & SQL Foundations · **Modules:** Python, SQL, Git
**Dates:** Sun Nov 15 – Sat Nov 28, 2026 · **Capacity:** ~20 hrs (US Thanksgiving week — plan for a lighter Weekend 2 if needed) · **ChatGPT ladder:** hints only

> Tentative brief. Claude confirms or adjusts it at the Sprint 1 review.

## Goal
Use loops and exception handling in Python, and write your first correct SQL queries against a real PostgreSQL database.

## Why it matters
Loops are how you process every row of data; exceptions are how pipelines survive bad input. SQL is the single most-requested data skill — and RetailPulse will answer its first business questions in SQL.

## Concepts in scope
- Python (CS50P lectures 2–3): `while`, `for`, `range`, lists and dicts basics, iterating, `try/except/else`, raising exceptions, input validation.
- SQL (Data with Baraa course, intro sections): what a database/table/row/column is, `SELECT`, `FROM`, `WHERE`, comparison and logical operators, `ORDER BY`, `DISTINCT`, `LIMIT`, column aliases.
- PostgreSQL: connecting with `psql`, creating a database, loading the course dataset (Baraa provides PostgreSQL versions).
- Git: Learn Git Branching levels 3–4 (merging, rebasing basics).

**Out of scope:** joins, aggregation (Sprint 3+).

## Design spec
1. `learning-notes/python/cs50p/week2/`, `week3/` — problem set solutions.
2. `retailpulse/sql/01_select_basics.sql` — **15 queries** against the course dataset, each preceded by a comment with: the business question in plain English, and your reasoning for filters/ordering. Format: UPPERCASE keywords, one clause per line.

## Acceptance tests
- Problem sets behave as specified for the example inputs, including invalid input where the spec requires handling it.
- Every query in `01_select_basics.sql` runs without error in `psql` and returns the result its comment describes.

## Definition of Done
- [ ] CS50P weeks 2–3 solved and pushed
- [ ] `sql/01_select_basics.sql` with 15 commented queries, merged via PR
- [ ] Explain-back answered; `claude-approved`; merged
- [ ] Learn Git Branching levels 3–4 done
- [ ] Tracker updated; sprint review + retro done

## Review criteria
- Query correctness vs the stated question; SQL style (UPPERCASE, aliases, comments explain *why*).
- Explain-back examples: Why does `WHERE` run before `SELECT` aliases are available? What's the difference between `DISTINCT` on one column vs several? When would `try/except` hide a bug?

## ChatGPT tutoring notes
- For SQL, have me predict result row counts before running queries.
- Common pitfalls: `NULL` comparisons with `=`, string quotes, ordering by an alias.

## Stretch
- 5 SQLBolt lessons.
