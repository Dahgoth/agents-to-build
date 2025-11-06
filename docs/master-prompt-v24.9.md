# 🚀 Master Prompt — Doing Phase (Execution Layer, v24.9)

## Purpose

- Build **MegaCampusAI**: a new LMS platform (v2) developed jointly by LMS Team and AI Team, based on **LMSv1** and **CourseAI**.  
- Reflect **AI Team’s CourseAI milestones** (mid‑Nov showcase) and **LMS Team’s new build plan** in one integrated roadmap.  
- Produce **Russian‑language specs** (Backend, Frontend, Learning Designer Brief) for the LMS platform.  
- Generate **Jira payloads (RU)** for both AI Team and LMS Team, clearly separated but in one file for investor clarity.  
- Generate an **Investor Progress Report (RU)** with subsections for CourseAI and MegaCampusAI, plus a Telegram digest.  
- Enforce **approval gates per artifact** (Preflight, Roadmap, Specs, Jira, Report).  
- Always use **MCP servers** and **agents/skills** for their designed tasks; fail closed if skipped.  
- Preserve history but never bias outputs with old generated docs.

---

## The Project Roadmap

- **Artifact name**: `PROJECT_ROADMAP_EN_YYYY-MM-DD_HHMM.md`  
- **Purpose**: Single, integrated plan unifying:  
  - AI Team’s CourseAI roadmap (status, milestones, constraints).  
  - LMS Team’s MegaCampusAI build plan (from LMSv1 baseline).  
  - Investor constraints and compliance placeholders.  
- **History**: Older roadmaps/specs/logs archived in `docs/archive/`; never treated as current truth.

---

## Inputs to Read

- `~/projects/MegaCampusAI/docs/IMPLEMENTATION_ROADMAP_EN.md`  
- `~/projects/MegaCampusAI/docs/TECHNICAL_SPECIFICATION_PRODUCTION_EN.md` (**main canonical doc**)  
- `~/projects/MegaCampusAI/docs/FUTURE/*`  
- `~/projects/MegaCampusAI/docs/Agents Ecosystem/*`  
- `~/projects/MegaCampusAI/.claude/{agents,commands,skills}`  
- `~/projects/agents-to-build/.claude/{agents,commands,skills}`  
- `~/projects/agents-to-build/docs/roadmaps/INTERNAL_ROADMAP_EN-v10.md`  
- `~/projects/agents-to-build/docs/LMSv1.md`  
- Exclude: `.specify/*`  

**Bias‑prevention tie‑in:** Only these inputs are canonical truth. Old generated outputs are for history only.

---

## MCP Servers

- **context7** → always try first for resolving references to canonical docs.  
- **server-sequential-thinking** → always try first for structuring execution steps, sequencing, dependencies.  
- If unavailable, halt and request fallback approval.

---

## Agent & Skill Utilization

- Invoke agents/skills from both repos for the tasks they are designed for.  
- Normalize overlapping agents into canonical roles.  
- Verification is assigned to **Verification Agents**, not individuals:  
  - Backend Verification Agent  
  - Frontend Verification Agent  
  - Data Verification Agent  
  - Compliance Verification Agent  
  - Infra Verification Agent  
- If Codex finds missing verification roles, propose new agents and log them.  
- Log all agent/skill invocations in the execution log.

---

## Approval Workflow (mandatory)

- **Preflight Summary (RU)** → wait for “Approved: Preflight”  
- **Roadmap (EN)** → wait for “Approved: Roadmap”  
- **Specs (RU)** → wait for “Approved: Specs”  
- **Jira Payloads (RU)** → wait for “Approved: Jira”  
- **Investor Report (RU)** → wait for “Approved: Report”  
- Each stage must pause for explicit approval before writing files.

---

## Project Roadmap (EN)

- **File**: `PROJECT_ROADMAP_EN_YYYY-MM-DD_HHMM.md`  
- **Contents**:  
  - Achieved / In progress / Next (months 1–5).  
  - AI Team milestones (CourseAI v2 mid‑Nov).  
  - LMS Team build plan (from LMSv1 baseline).  
  - Dependencies across teams.  
  - Responsibilities per canonical role.  
  - Acceptance anchors referencing canonical docs.  
  - Risks and early warnings.  
- **Codex pre‑check**: must scan canonical docs to avoid duplication; mark already‑done items as covered.

---

## Specs (RU) — LMS platform build

- **Backend Spec**: `LMS_BACKEND_SPEC_RU_YYYY-MM-DD_HHMM.md`  
  - APIs: courses, lessons, assessments, exports, webhooks.  
  - Auth: JWT/RLS, service accounts.  
  - Observability: OTel traces, SLI/SLO.  
  - Compliance placeholders: audit logs, retention, residency.  
- **Frontend Spec**: `LMS_FRONTEND_SPEC_RU_YYYY-MM-DD_HHMM.md`  
  - UI flows: authoring, imports/exports, tracking jobs, error handling, accessibility.  
- **Learning Designer Brief**: `LMS_LEARNING_DESIGNER_BRIEF_RU_YYYY-MM-DD_HHMM.md`  
  - Templates, rubrics, acceptance checklist, examples.  
- Verification roles: assigned to agents.

---

## Jira Payloads (RU)

- **File**: `JIRA_ARTIFACTS_RU_YYYY-MM-DD_HHMM.md`  
- **Epics**: Theme + Outcome (AI milestones, LMS build pillars).  
- **Stories**: User story format.  
- **Tasks**: Actionable technical steps.  
- **Metadata**:  
  - scope:current | scope:future  
  - responsibility:<role>  
  - verification:<verification agent>  
  - acceptance-anchor:<doc#section>  
  - evidence:<artifact>  
- **Dual focus**: AI Team scope + LMS Team scope, clearly separated.

---

## Investor Progress Report (RU)

- **File**: `INVESTOR_PROGRESS_RU_YYYY-MM-DD_HHMM.md`  
- **Sections**:  
  1. Executive summary  
  2. CourseAI — status, next steps, mid‑Nov readiness  
  3. MegaCampusAI — roadmap, next steps  
  4. Risks & mitigations  
  5. Evidence (anchors, artifacts)  
- **Telegram digest**: 3–4 lines: Done / Next / Risks.

---

## Execution Log

- **File**: `EXECUTION_LOG_YYYY-MM-DD_HHMM.md`  
- **Sections**:  
  - Provenance: inputs, MCP servers, agents invoked.  
  - Preflight: project vision, teams, stakeholders, repo purpose, constraints.  
  - Roadmap decisions: AI vs LMS scope, milestones.  
  - Specs produced: filenames, anchors.  
  - Jira payloads: filename, epics/stories/tasks.  
  - Role normalization: agents → roles; duplicates; outdated payloads.  
  - Lessons learned: carried forward (with confirmation) or discarded.  
  - Bias Prevention Checklist:  
    - [ ] Only treated Inputs to Read as canonical truth  
    - [ ] Did not treat old outputs as current truth  
    - [ ] Only reused lessons learned after explicit confirmation  
    - [ ] Regenerated outputs from canonical sources  
    - [ ] Logged outdated payloads separately  
    - [ ] Avoided copying/paraphrasing from archived versions  
  - Compliance Evidence Checklist:  
    - [ ] API schemas (Swagger/tRPC)  
    - [ ] CI reports (validators, contract tests)  
    - [ ] OTel traces and coverage  
    - [ ] Audit logs & retention policy docs  
    - [ ] SCORM validator output and import receipts  
  - Next steps: approvals pending; integrations required.

---

## Guardrails

- **Tools first**: Always attempt MCP servers and agents; fail closed if skipped.  
- **Approval gating**: No artifact generation without explicit “Approved: <artifact>”.  
- **History vs truth**: Archive old outputs; never treat them as current truth.  
- **Bias prevention**: As per checklists.

---

## Naming Conventions (all outputs include `_YYYY-MM-DD_HHMM`)

- PRELIGHT_SUMMARY_RU_YYYY-MM-DD_HHMM.md  
- PROJECT_ROADMAP_EN_YYYY-MM-DD_HHMM.md  
- INVESTOR_PROGRESS_RU_YYYY-MM-DD_HHMM.md  
- JIRA_ARTIFACTS_RU_YYYY-MM-DD_HHMM.md  
- LMS_BACKEND_SPEC_RU_YYYY-MM-DD_HHMM.md  
- LMS_FRONTEND_SPEC_RU_YYYY-MM-DD_HHMM.md  
- LMS_LEARNING_DESIGNER_BRIEF_RU_YYYY-MM-DD_HHMM.md  
- EXECUTION_LOG_YYYY-MM-DD_HHMM.md
