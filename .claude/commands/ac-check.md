---
description: Validate acceptance criteria completeness and traceability using acceptance-criteria-checker skill. Produces a matrix and improvement suggestions.
---

# /ac-check command

## Syntax

/ac-check spec:"specs/<feature>/spec.md" tasks:"specs/<feature>/tasks.md" tests:"packages/**/tests/**/*.{test,spec}.ts"

## Your Task

1) Load Inputs
- Use Read tool to load `spec` and `tasks`. If `tests` glob provided, gather candidate files.

2) Invoke Skill: acceptance-criteria-checker
- Provide the three inputs and request a traceability matrix.

3) Output Results
- Print the matrix table: Story | Has AC | AC Count | Issues | Tasks | Tests
- List per-story improvement suggestions and any missing negative/error-path ACs.

4) (Optional) Write Report
- If `--write` provided, save results to `specs/<feature>/ac-traceability.md`.

## Notes
- Run this before implementation handoff and again before test creation to ensure coverage.

