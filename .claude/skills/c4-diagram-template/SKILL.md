---
name: c4-diagram-template
description: Render Mermaid C4-style diagrams (Context/Container/Component) from structured inputs. Use to document architecture quickly and consistently.
---

# C4 Diagram Template

Generate consistent Mermaid diagrams for C4-style views using simple inputs.

## When to Use

- System/Container/Component diagrams for architecture docs
- Visualizing boundaries, dependencies, and external integrations
- Keeping diagrams in-version alongside ADRs/ARCHITECTURE.md

## Inputs

Provide a JSON payload describing the view and nodes:

```json
{
  "view": "context|container|component",
  "title": "<Diagram Title>",
  "elements": [
    { "id": "user", "type": "person", "label": "End User" },
    { "id": "app", "type": "system|container|component", "label": "Web App" },
    { "id": "db", "type": "container", "label": "Postgres (Supabase)" }
  ],
  "relations": [
    { "from": "user", "to": "app", "label": "uses", "tech": "HTTPS" },
    { "from": "app", "to": "db", "label": "queries", "tech": "SQL/RLS" }
  ],
  "notes": ["Assumes JWT auth via Supabase", "Multi-tenant isolation via RLS"]
}
```

## Instructions

1. Choose Layout
   - Use `flowchart TB` for top-to-bottom layout (or `LR` for left-right).
2. Map Types to Shapes
   - person → rounded box; system → double border; container → single box; component → thin box.
3. Emit Nodes
   - Format: `id[Label]`, and add stereotypes like `[Container] Label` in the text.
4. Emit Edges
   - Format: `id1 -->|label (tech)| id2`.
5. Styling (Optional)
   - Use `classDef` to style node categories; apply with `class id className`.
6. Output
   - Produce a Mermaid code block with optional title and legend.

## Output

A ready-to-embed Mermaid block, e.g. in `docs/ARCHITECTURE.md`:

```mermaid
flowchart TB
  %% Title
  %% C4-Context: MegaCampus Overview

  user([Person] End User)
  app([[System] MegaCampus App])
  ext([[System] 3rd-Party Service])
  db([Container] Supabase Postgres)

  user -->|uses (HTTPS)| app
  app -->|queries (SQL/RLS)| db
  app -->|integrates (REST)| ext

  classDef person fill:#E3F2FD,stroke:#64B5F6,color:#0D47A1
  classDef system fill:#E8F5E9,stroke:#81C784,color:#1B5E20
  classDef container fill:#FFF3E0,stroke:#FFB74D,color:#E65100
  class user person
  class app,ext system
  class db container
```

## Tips

- Keep labels short; put details in notes below the diagram.
- For component view, group by module using `subgraph` blocks.
- Version diagrams by feature/ADR to track changes.

## Report / Response

Return:
- Mermaid block
- Short notes/assumptions list
- Suggested file path to insert/update

