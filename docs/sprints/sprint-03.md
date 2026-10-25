# Sprint 03 — "First RetailPulse data"

**Phase:** 1 — Programming & SQL Foundations · **Modules:** Python, SQL, Linux
**Dates:** Sun Nov 29 – Sat Dec 12, 2026 · **Capacity:** ~20 hrs · **ChatGPT ladder:** hints only

> Tentative brief. Claude confirms or adjusts it at the Sprint 2 review.

## Goal
Build the first RetailPulse artifact: a deterministic data generator for customers and products, with tests, and load its output into PostgreSQL to answer aggregation questions.

## Why it matters
Every RetailPulse layer needs data. A generator that produces the **same output from the same seed** is how real teams build reproducible tests and demos. Loading it and aggregating it is the first end-to-end "data pipeline" you'll own.

## Concepts in scope
- Python (CS50P lectures 4–5): importing libraries, `random` with a seed, `sys.argv`, writing your own functions in a module, unit tests with `pytest`.
- Linux: pipes `|`, redirection `>` `>>`, `head`, `wc -l`, `grep`.
- SQL: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, `GROUP BY`, `HAVING`, NULL basics, `COPY` to load CSV.
- Project setup: `uv init` a Python project in `retailpulse`, `pyproject.toml`, `src/retailpulse/` package layout, `tests/`.

**Out of scope:** orders/order items (Sprint 4+), file I/O with the `csv` module (Sprint 4), classes.

## Design spec
- `src/retailpulse/data_generator.py` with functions:
  - `make_customer(customer_id: int, rng) -> list[str]` → `customer_id, name, email, signup_date, region, segment`
  - `make_product(product_id: int, rng) -> list[str]` → `product_id, name, category, price, stock_quantity`
  - a `main()` that prints a header row + N rows as comma-separated text to standard output, taking `kind` (`customers` or `products`), `count` and `seed` from the command line.
- Usage: `uv run python -m retailpulse.data_generator customers 100 42 > data/customers.csv`
- `tests/test_data_generator.py` with at least 3 tests: same seed → same output; correct number of fields per row; values within allowed sets (regions, segments, categories) and price > 0.
- `sql/02_customer_product_aggregations.sql`: create tables, `COPY` the two CSVs in, and 10 commented aggregation queries (e.g. customers per region, average price per category, categories with more than N products).
- `data/` is ignored by Git (generated data is never committed).

## Acceptance tests
- Running the generator twice with seed 42 produces byte-identical files (`diff` shows nothing).
- `uv run pytest -q` passes; `uvx ruff check .` passes.
- `wc -l data/customers.csv` shows N + 1 lines.
- All 10 queries run and match their comments.

## Definition of Done
- [ ] Generator + tests + SQL file merged via one or two small PRs
- [ ] Deterministic output demonstrated in the PR description (commands + result)
- [ ] CI green, explain-back answered, `claude-approved`, merged
- [ ] CS50P weeks 4–5 problem sets in `learning-notes`
- [ ] Tracker updated; sprint review + retro done

## Review criteria
- Determinism and tests; type hints and docstrings; no hardcoded paths; logging not required yet (introduced in Sprint 5+), but no debug prints left in.
- SQL style and grain thinking ("one row per what?") in comments.
- Explain-back examples: Why does a seed make output reproducible? Why doesn't generated data go into Git? What's the difference between `WHERE` and `HAVING`?

## ChatGPT tutoring notes
- Teach `uv init`, the src layout and `pytest` discovery step by step; this is the first real project structure.
- Let me design the function signatures' internals myself; give hints on using `rng.choice` and string formatting.

## Stretch
- Add a `--help` message.
- One query using `CASE` to bucket prices into bands.
