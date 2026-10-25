---
description: Review a RetailPulse pull request against its sprint brief and the rubric, post the review, and apply the approval label only on APPROVE.
argument-hint: <PR number>
---

You are reviewing pull request #$ARGUMENTS in this repository as the RetailPulse architect and reviewer. Follow CLAUDE.md. Do not edit any files in this repository during the review.

## Steps

1. **Collect context**
   - `gh pr view $ARGUMENTS --json number,title,body,headRefName,headRefOid,labels,files,commits`
   - `gh pr diff $ARGUMENTS`
   - Find the linked sprint brief in the PR body (path `docs/sprints/sprint-NN.md`) and read it: design spec, acceptance tests, Definition of Done, review criteria, explain-back questions.
   - Read `CLAUDE.md` for the current phase.
   - `gh pr view $ARGUMENTS --comments` to see earlier reviews and any explain-back answers from the learner.

2. **Check out and verify** (read-only use of the code)
   - `gh pr checkout $ARGUMENTS`
   - If `pyproject.toml` exists: `uvx ruff check .` and `uvx ruff format --check .`, then run the tests (`uv run pytest -q` when a `tests/` folder exists).
   - Run any acceptance checks the brief lists that are safe to run locally.
   - Record exact results. Do not fix anything.

3. **Assess against the rubric**
   - Correctness vs the brief's spec and acceptance tests.
   - Definition of Done: tick each item as met or not met, with evidence.
   - Standards from CLAUDE.md (Python, SQL, tests, Git, security, docs).
   - Classify every finding: Blocker / Major / Minor / Nit, with file and line, why it matters, and what to study. Never paste corrected code.

4. **Explain-back (Phases 1–2 only)**
   - If no earlier review on this PR asked them, ask 2–3 short questions about the learner's own code (what a line does, why a choice was made, what happens on bad input). Verdict becomes `PENDING EXPLAIN-BACK`.
   - If they were asked and the learner has answered in the comments, judge each answer: correct / partly / incorrect, with a one-line note.

5. **Decide the verdict**
   - `APPROVE` only if: tests/lint pass, zero Blockers, zero Majors, every DoD item met, and (Phases 1–2) explain-back answers are correct.
   - Otherwise `CHANGES REQUESTED` or `PENDING EXPLAIN-BACK`.

6. **Post the review as a PR comment** with `gh pr comment $ARGUMENTS --body-file <tempfile>` (temp file outside the repo), using this structure:

```
## Claude review — <VERDICT>
Reviewed commit: <headRefOid>
Sprint brief: <path>

### Checks
- Lint: pass/fail · Format: pass/fail · Tests: <n passed / failed>

### Definition of Done
- [x]/[ ] each item — evidence

### Findings
| Severity | Location | Finding | Why it matters | Study |
|---|---|---|---|---|

### Done well
- specific, evidence-based points

### Explain-back (Phases 1–2)
- questions, or judgments of the answers

### Next step
- what the learner should do now
```

7. **Gate**
   - If and only if the verdict is `APPROVE`: confirm the head commit has not changed since step 1 (`gh pr view $ARGUMENTS --json headRefOid`), then run `gh pr edit $ARGUMENTS --add-label claude-approved`.
   - For any other verdict, make sure the label is absent: `gh pr edit $ARGUMENTS --remove-label claude-approved` (ignore the error if it wasn't there).
   - For each Minor finding, offer to open a GitHub Issue; open them only if the learner says yes.

8. Switch back to the previous branch (`git checkout -`) and report the verdict in one or two sentences.
