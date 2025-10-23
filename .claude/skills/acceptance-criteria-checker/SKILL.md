---
name: acceptance-criteria-checker
description: Validate user stories have clear, testable acceptance criteria and produce a traceability matrix to tasks/tests. Use on specs before implementation.
---

# Acceptance Criteria Checker

Assess AC completeness and quality, and map stories → AC → tasks/tests.

## When to Use

- Before committing tasks for a feature
- During spec reviews to ensure testability
- Prior to writing tests to confirm coverage

## Inputs

Either provide file paths or inline content:

```json
{
  "spec_path": "specs/<feature>/spec.md",
  "tasks_path": "specs/<feature>/tasks.md",
  "tests_glob": "packages/**/tests/**/*.{test,spec}.ts"
}
```

## Instructions

1. Read Source Docs
   - Load spec.md; detect stories via headings or patterns (e.g., "As a ... I want ... so that ...").
   - Identify AC blocks under each story: "Acceptance Criteria" or Gherkin (Given/When/Then).
2. Validate AC Quality (see CHECKLIST)
   - Each AC is observable and unambiguous; avoid vague terms (fast, simple, easy).
   - Prefer Gherkin or include condition, action, expected result.
   - Minimum 2–3 AC per story unless trivial.
3. Traceability
   - Map stories → tasks in tasks.md (by label or content match).
   - Map stories/AC → test files (if present) by filename or tags.
4. Report
   - Produce a table: Story ID | Has AC | Count | Quality Issues | Tasks Linked | Tests Linked.
   - List suggested improvements per story.

## Output

- Summary of gaps and risks
- Traceability matrix table (Markdown)
- Suggested AC rewrites (when needed)

## Example Traceability Table

| Story | Has AC | AC Count | Issues | Tasks | Tests |
| :--- | :---: | ---: | :--- | :--- | :--- |
| US1 | ✓ | 4 | — | T001,T005 | auth.e2e.test.ts |
| US2 | ⚠ | 1 | Vague terms; missing error cases | T010 | — |

## CHECKLIST Reference

See `CHECKLIST.md` for quality heuristics.

