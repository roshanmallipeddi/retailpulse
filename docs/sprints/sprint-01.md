# Sprint 01 — "Hello, engineer"

**Phase:** 1 — Programming & SQL Foundations · **Modules:** Python, Linux, Git
**Dates:** Sun Nov 1 – Sat Nov 14, 2026 · **Capacity:** ~20 hrs · **ChatGPT ladder:** hints only

## Goal
Write, run and commit small Python programs from WSL2, and take one change all the way through the RetailPulse workflow: branch → PR → Claude review → approval label → merge.

## Why it matters
Every data engineering job starts here: running code from a terminal, keeping it in Git, and getting it reviewed before it reaches `main`. In RetailPulse, every future pipeline, model and API will travel this exact path, so you learn the path first with something small.

## Concepts in scope
- Python: running a `.py` file, `print`, `input`, variables, `str`/`int`/`float`, f-strings, defining and calling functions, return values, `if/elif/else`, comparison and boolean operators (CS50P lectures 0–1).
- Shell: `pwd`, `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `cat`, `less`, paths, `man`, `--help` (Missing Semester lecture 1).
- Git: `init`/`clone`, `status`, `add`, `commit`, `push`, `pull`, branches, pull requests, commit message convention `type(scope): description`.

**Out of scope:** loops, files, libraries, SQL (they start in Sprint 2+).

## Resources
- Primary: Harvard CS50P lectures 0–1 and their problem sets · MIT Missing Semester lecture 1 (shell) and the Git lecture (first half).
- Practice: Learn Git Branching (levels 1–2) · OverTheWire Bandit levels 0–3 (optional, fun shell practice).

## Design spec
1. **`learning-notes` repo (private):**
   - `python/cs50p/week0/` and `python/cs50p/week1/` — your solutions to the CS50P problem sets for lectures 0 and 1, one `.py` file per problem.
   - `sessions/2026-11.md` — your 3-line handoff notes for each session this month.
2. **`retailpulse` repo (public)** — first pull request from branch `feature/learning-log`:
   - `docs/learning-log.md` — create it with a first entry: date, what you set up during groundwork, what you learned in Sprint 1, one thing that confused you and how you resolved it.
   - `README.md` — add a short section **"Why I'm building this"** (3–6 sentences in your own words).
   - Commits use the convention, e.g. `docs(log): add first learning log entry`.

## Acceptance tests
- Each CS50P problem runs with `python3 <file>.py` (or `uv run <file>.py`) and behaves as its specification says (use the examples in each problem statement as your test cases; `check50` is optional).
- `git log` in both repos shows commits with the naming convention.
- The PR in `retailpulse` links this brief and has the template filled in.

## Definition of Done
- [ ] CS50P week 0 and week 1 problem sets solved and pushed to `learning-notes`
- [ ] At least 4 session handoff notes in `sessions/2026-11.md`
- [ ] `retailpulse` PR opened from `feature/learning-log` with template completed
- [ ] Claude review posted; explain-back questions answered in the PR comments
- [ ] `claude-approved` label applied by Claude and `review-gate` passing
- [ ] PR merged into `main`
- [ ] Session Log rows filled in the Excel tracker; sprint review + retro done

## Review criteria (what Claude checks)
- Learning log entry is specific (real commands, real confusion), not generic.
- Commit messages follow the convention; PR template is complete; one artifact.
- No personal secrets or tokens anywhere.
- Explain-back (examples of what Claude may ask): What does `git add` do that `git commit` doesn't? Why work on a branch instead of `main`? What happens when a function has no `return` statement?

## ChatGPT tutoring notes
- Ladder: hints only. Don't solve CS50P problems; ask guiding questions and use different example problems.
- Expect first-week friction with WSL2 paths (Windows vs Linux paths) and Git authentication. Teach, don't just fix.
- Quiz on: variables vs values, what `return` does, `if/elif/else` order, branch vs commit.

## Stretch (optional)
- OverTheWire Bandit levels 4–6.
- A second small PR adding a "Tools I use" list to `docs/learning-log.md`.

## Risks / blockers
- Groundwork items not finished (WSL2, Git auth, branch protection) → finish them first; this sprint has slack for it.

## Suggested session plan
| When | Plan |
|---|---|
| Sun Nov 1 (2 blocks) | Block 1: CS50P lecture 0. Block 2: problem set 0 (first two problems). |
| Weekdays wk 1 | Missing Semester shell lecture (watch in two parts); recall quiz with ChatGPT. |
| Sat Nov 7 | Block 1: finish problem set 0. Block 2: Git basics + Learn Git Branching 1–2. |
| Sun Nov 8 | Block 1: CS50P lecture 1. Block 2: problem set 1 (start). |
| Weekdays wk 2 | Recall quiz; tidy session notes. |
| Sat Nov 14 | Block 1: finish problem set 1. Block 2: learning-log PR → `/review` → fix loop → merge → sprint review and retro. |
