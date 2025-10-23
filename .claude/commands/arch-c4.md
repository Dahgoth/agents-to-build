---
description: Generate C4 Mermaid diagram using c4-diagram-template skill and insert/update docs. Accepts view, title, and output path.
---

# /arch-c4 command

## Syntax

/arch-c4 view:<context|container|component> title:"<Title>" output:"docs/ARCHITECTURE.md" [section:"C4-Context"]

## Your Task

1) Build Diagram Payload
- Create JSON payload for `c4-diagram-template` with `view`, `title`, `elements`, and `relations`.
- Example:
```json
{
  "view": "context",
  "title": "C4-Context: MegaCampus Overview",
  "elements": [
    {"id":"user","type":"person","label":"End User"},
    {"id":"app","type":"system","label":"MegaCampus App"},
    {"id":"db","type":"container","label":"Supabase Postgres"}
  ],
  "relations": [
    {"from":"user","to":"app","label":"uses","tech":"HTTPS"},
    {"from":"app","to":"db","label":"queries","tech":"SQL/RLS"}
  ]
}
```

2) Invoke Skill
- Use `c4-diagram-template` to generate a Mermaid block.

3) Write/Update File
- If `output` file exists: insert or replace section matching `section` heading; otherwise append under a new heading.
- If `output` missing: create file with a heading and the Mermaid block.

4) Report Completion
- Show output file path and section name
- Include Mermaid block in the response for preview

## Notes
- For component view, consider grouping modules with `subgraph`.
- Keep labels concise; put details in notes below the diagram.

