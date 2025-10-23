---
description: Scaffold audit taxonomy and logging strategy using audit-event-schema skill. Writes LOGGING-STRATEGY.md and AUDIT-TAXONOMY.md.
---

# /audit-setup command

## Syntax

/audit-setup categories:"auth,role_change,data_export,payment,policy_change" output_dir:"docs"

## Your Task

1) Prepare Inputs
- Split `categories` into a list.
- Optional: customize retention and access in the input JSON to `audit-event-schema`.

2) Invoke Skill: audit-event-schema
- Generate: canonical fields table, category matrix (retention/access), base JSON Schema, and example events.

3) Write Deliverables
- Create or update:
  - `${output_dir}/LOGGING-STRATEGY.md` — standards, libraries, redaction rules, examples.
  - `${output_dir}/AUDIT-TAXONOMY.md` — event categories, retention matrix, access controls, JSON Schema block, examples.

4) Report Completion
- Output file paths and brief summary of categories and retention.

## Notes
- Coordinate with `logging-and-audit` agent to wire sinks and runtime middleware.
- Ensure sensitive fields are redacted at log sink level.

