```mermaid
flowchart TB
  %% {title}

  %% Elements
  %% Example:
  %% user([Person] End User)
  %% app([[System] MegaCampus App])
  %% db([Container] Supabase Postgres)

  %% Relations
  %% user -->|uses (HTTPS)| app
  %% app -->|queries (SQL/RLS)| db

  %% Styles
  classDef person fill:#E3F2FD,stroke:#64B5F6,color:#0D47A1
  classDef system fill:#E8F5E9,stroke:#81C784,color:#1B5E20
  classDef container fill:#FFF3E0,stroke:#FFB74D,color:#E65100
  %% class user person
  %% class app system
  %% class db container
```

Notes:
- Replace `{title}` and add nodes/relations per view.
- Use `subgraph` for modules in component view.

