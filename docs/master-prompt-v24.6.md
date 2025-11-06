# 🚀 Master Prompt — Doing Phase (Execution Layer, v24.6)

### Purpose

- Use `~/projects/MegaCampusAI/docs/IMPLEMENTATION_ROADMAP_EN.md` and related docs as the **source of truth** for AI Team status and work.
- Integrate `~/projects/agents-to-build/docs/roadmaps/INTERNAL_ROADMAP_EN-v10.md` (gap‑covering roadmap) into the **overall plan** — fold its initiatives into the broader roadmap, not as a baseline but as complementary enablers.
- Produce a **full set of Jira payloads** (Epics, Stories, Tasks) describing the project for both AI Team and LMS Team, plus future specialists.
- Generate an **Investor Progress Report (RU)** with a short **Telegram digest**.
- Produce **Russian‑language specs** for Backend, Frontend, and a **plain‑language Learning Designer Brief** (templates, examples, checklists).
- Preserve history and lessons learned, but do not hard‑code version numbers. Always check existing execution logs for lessons learned and confirm with me if they still apply.

---

### The Project Roadmap

- **Artifact name**: `PROJECT_ROADMAP_EN_YYYY-MM-DD_HHMM.md`
- **Purpose**: This is the **single, integrated project plan**.  
  - It unifies AI Team’s implementation roadmap, v10 gap‑closures, LMS integration milestones, and investor constraints.  
  - It is the authoritative reference for **all teams and stakeholders** (AI, LMS, investors, future specialists).  
  - It must clearly show: what has been achieved, what is in progress, and what comes next.  
- **History**: Older roadmaps/specs/logs are preserved in `docs/archive/` for traceability, but never treated as current truth.

---

### Inputs to Read

- `~/projects/MegaCampusAI/docs/IMPLEMENTATION_ROADMAP_EN.md`

- `~/projects/MegaCampusAI/docs/FUTURE/*`

- `~/projects/MegaCampusAI/docs/Agents Ecosystem/*`

- `~/projects/MegaCampusAI/.claude/{agents,commands,skills}`

- `~/projects/agents-to-build/.claude/{agents,commands,skills}`

- `~/projects/agents-to-build/docs/roadmaps/INTERNAL_ROADMAP_EN-v10.md`

- `~/projects/agents-to-build/docs/LMSv1.md`

- Exclude: `.specify/*`

**Bias‑prevention tie‑in:** Only these inputs are to be treated as canonical sources of truth. Old generated outputs (roadmaps, specs, Jira payloads, logs) are never to be used as inputs — they are archived for history only.

---

### MCP Servers

- **context7** → always try to use this first when resolving references to canonical docs.  
- **server-sequential-thinking** → always try to use this first when structuring execution steps, sequencing, and dependencies.  

---

### Agent & Skill Utilization

- **Agents and skills** defined in `.claude/{agents,commands,skills}` (both MegaCampusAI and agents-to-build) must be **launched and applied to the tasks they are designed for**.  
- Normalize overlapping or differently‑named agents into canonical roles.  
- Use their outputs to enrich roadmaps, specs, and Jira payloads.  
- In Jira artifacts, always collapse to **roles only** (never expose agent/tool names).  
- Log normalization and outdated payloads in the execution log.

---

### Jira Payload Rules

- **Epics**: Theme + Outcome, high‑level description, business value, acceptance anchors, dependencies.  
- **Stories**: User story form — *“As a [role/persona], I want [goal], so that [business value].”*  
- **Tasks**: Actionable technical steps linked to Stories.  
- **Labels/Metadata**: `scope:current` / `scope:future`, `responsibility:<role>`, `verification:<role>`, `acceptance-anchor:<doc#section>`, `evidence:<artifact>`.

---

### Investor Progress Report (RU)

- **File**: `INVESTOR_PROGRESS_RU_YYYY-MM-DD_HHMM.md`
- **Format**:  
  1. Резюме (Executive Summary)  
  2. Что сделано (What’s Done)  
  3. Что дальше (What’s Next)  
  4. Риски и меры (Risks & Mitigations)  
  5. Доказательства (Evidence)  
- **Telegram digest**: 3–4 строки, простым языком, формат “Сделано / Дальше / Риски”.

---

### Specs (RU)

- **Backend Spec**: `LMS_BACKEND_SPEC_RU_YYYY-MM-DD_HHMM.md`
- **Frontend Spec**: `LMS_FRONTEND_SPEC_RU_YYYY-MM-DD_HHMM.md`
- **Learning Designer Brief**: `LMS_LEARNING_DESIGNER_BRIEF_RU_YYYY-MM-DD_HHMM.md`

---

### Execution Log

- **File**: `EXECUTION_LOG_YYYY-MM-DD_HHMM.md`
- **Template** (all sections must be present):

```markdown
# Execution Log — YYYY-MM-DD HH:MM (MSK)

## Provenance

- Orchestrator: Execution Orchestrator
- Inputs consulted: [list docs, agents, skills]
- MCP servers used: [`context7`, `server-sequential-thinking`, etc.]
- Agents/skills invoked: [list roles/tasks]

## Roadmap Decisions

- Summary of how `PROJECT_ROADMAP` was updated
- Integration of v10 gap‑closures
- Investor constraints applied

## Specs Produced

- Backend spec filename
- Frontend spec filename
- Learning Designer brief filename

## Jira Payloads

- Jira artifacts filename
- Epics/Stories/Tasks generated

## Role Normalization

- Mapping of agents → canonical roles
- Duplicates resolved
- Outdated payloads logged

## Lessons Learned

- Items carried forward from previous logs
- Items explicitly discarded as no longer valid

## Bias Prevention Checklist

- [ ] Did not treat old generated docs/specs/payloads as current truth
- [ ] Only reused lessons learned after explicit confirmation
- [ ] Regenerated all outputs from canonical sources
- [ ] Logged outdated payloads separately for history
- [ ] Avoided paraphrasing/copying from archived versions

## Next Steps

- Pending approvals
- Manual imports or integrations required
```

---

### Guardrails

- **History vs Current Truth**:  
  - Preserve all old versions in `docs/archive/`.  
  - **Never treat old versions as current truth.** They are for traceability only.  
  - Always regenerate fresh outputs from the canonical sources.  
- **Bias prevention**:  
  - Do not copy or paraphrase content from old generated docs/specs/payloads.  
  - Only reuse “lessons learned” if explicitly confirmed valid.  
  - If unsure whether a lesson still applies, pause and ask for clarification.  
- **Approval workflow**:  
  1. Propose roadmap/Jira/specs/memo.  
  2. Wait for my approval.  
  3. If approved → finalize Jira artifacts in Russian.

---

### Execution Tasks

1. Integrate AI Team roadmap (`IMPLEMENTATION_ROADMAP_EN.md`) with v10 gap‑closures into a unified plan.  
2. Generate updated **Project Roadmap** (English).  
3. Produce Investor Progress Report (RU) + Telegram digest.  
4. Generate Russian specs (Backend, Frontend, Designer Brief) with timestamped filenames.  
5. Generate Jira payloads (Epics, Stories, Tasks) in Russian, following correct formats, with timestamped filenames.  
6. Update execution log with provenance, normalization, outdated payloads, lessons learned, MCP usage, and complete the Bias Prevention Checklist.

---

### Naming Conventions (all outputs must include `_YYYY-MM-DD_HHMM`)

- **Logs**: `EXECUTION_LOG_YYYY-MM-DD_HHMM.md`
- **Investor report**: `INVESTOR_PROGRESS_RU_YYYY-MM-DD_HHMM.md`
- **Jira artifacts**: `JIRA_ARTIFACTS_RU_YYYY-MM-DD_HHMM.md`
- **Specs**:  
  - `LMS_BACKEND_SPEC_RU_YYYY-MM-DD_HHMM.md`  
  - `LMS_FRONTEND_SPEC_RU_YYYY-MM-DD_HHMM.md`  
  - `LMS_LEARNING_DESIGNER_BRIEF_RU_YYYY-MM-DD_HHMM.md`
- **Roadmap**: `PROJECT_ROADMAP_EN_YYYY-MM-DD_HHMM.md`
