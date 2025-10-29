# MegaCampusAI Internal Roadmap (EN)

Version: v10  
Date: 2025-10-24  
Target: Public launch planned March 2026  
Scenario IDs: S1-Core, S2-Plus, S3-Enterprise

> Note: Outcomes are planned milestones and intended results, not guarantees.

---

## Contents

- [MCP Usage](#mcp-usage)
- [Schema & Agent Ecosystem Summary](#schema--agent-ecosystem-summary)
- [Baseline Achievements](#baseline-achievements)
- [Six Compliance Pillars](#six-compliance-pillars)
- [Compliance Evidence Packs](#compliance-evidence-packs)
- [Assumptions & Excluded Scope](#assumptions--excluded-scope)
- [Decision Log Delta + Impact of Changes](#decision-log-delta--impact-of-changes)
- [Partner Readiness Matrix](#partner-readiness-matrix)
- [Roadmap Scenarios](#roadmap-scenarios)
  - [S1-Core](#s1-core)
  - [S2-Plus](#s2-plus)
  - [S3-Enterprise](#s3-enterprise)
- [Global Risk Register](#global-risk-register)
- [Highlighted Workstreams](#highlighted-workstreams)
- [Dependency Mapping](#dependency-mapping)
- [Story Guidance (Structure Only)](#story-guidance-structure-only)
- [Cross-References](#cross-references)

---

## MCP Usage

- Servers invoked: `server-sequential-thinking`, `context7`.
- Topics retrieved (context7):
  - Identity bridging and provisioning via BoxyHQ Jackson (SAML→OIDC, SCIM 2.0). Used to shape Identity pillar milestones and investor backlog for IdP/SCIM setup.
  - OpenTelemetry JavaScript SDK (Node/Next.js) for traces/metrics/logs, OTLP exporters, resource attributes. Used to shape Observability pillar and SLA evidence.
- Sequential Thinking: Used to structure scenarios, risk register, and phased checkpoints through Mar 2026.
- Insufficiency notes: No external MCP docs were pulled for SCORM specifics; export plan relies on our canonical PRICING-TIERS and LMS-INTEGRATION-ROADMAP.

---

## Schema & Agent Ecosystem Summary

- Canonical model (Architecture v2.0): Two-level hierarchy with Domain Orchestrators (L1) and Workers (L2); Return Control pattern; plan files and quality gates between phases. See: docs/Agents Ecosystem/ARCHITECTURE.md.
- Meta-agent schema: agent frontmatter, strict roles by type; workers must read plan, do internal validation, produce structured reports; orchestrators coordinate and validate (never invoke workers directly). See: .claude/agents/meta-agent-v3.md.
- Quality gates: blocking (type-check, build, tests, lockfile, no-critical-vulns) and non‑blocking (lint, bundle-size, performance). See: docs/Agents Ecosystem/QUALITY-GATES-SPECIFICATION.md.
- MCP usage rules: Workers SHOULD use MCP for implementation; orchestrators MAY use MCP for validation/guidance.
- Only schema‑compliant agents referenced below (existing in repo), e.g., health orchestrators and workers listed in docs/Agents Ecosystem/AI-AGENT-ECOSYSTEM-README.md.

---

## Baseline Achievements

- Stage 0 Foundation COMPLETE; Stage 1 Main Entry COMPLETE. Source: docs/TECHNICAL_SPECIFICATION_PRODUCTION_EN.md#🎉-completion-status
  - AuthN/AuthZ: Supabase Auth JWT + RLS; SuperAdmin role and concurrency limits.
  - Orchestration: BullMQ jobs and dashboard; cancellation and backoff.
  - API: tRPC endpoints ready; HTTP POST for LMS; examples in docs/API.md and docs/LMS-INTEGRATION-ROADMAP.md.
  - Data: Supabase PostgreSQL + pgvector; structured content separation.
  - Security: Zero known vulns at Stage 0-1, per spec.

---

## Six Compliance Pillars

The pillars below include baseline, gaps, roles, joint areas, reinforcement, qualitative asks, and business value.

### P1. Identity & Access (Auth, SSO/SAML, OIDC, SCIM)

- Baseline: Supabase Auth JWT; RBAC via roles; RLS for tenant isolation. See: docs/API.md#authentication, #authorization; README.md#authentication-flow.
- Gaps: Enterprise SSO (SAML/OIDC bridge), SCIM provisioning, IdP mapping, session/claims governance, test matrices.
- Our team: Define identity integration patterns; sample SP config; JWT claims mapping; mock IdP harness; agentized validators for JWT and SCIM payloads.
- Investor team: Implement or integrate IdP (Okta/Azure/ADFS) using a bridge (e.g., BoxyHQ Jackson); operate SCIM directory sync; LMS user/role sync.
- Joint: End-to-end SSO user journeys; JIT provisioning; deprovisioning signals; recovery flows.
- Reinforcement: Automated SSO smoke tests; SCIM contract tests in CI; periodic pen-test of SSO endpoints.
- Qualitative asks: Access to IdP sandbox; SCIM enablement; admin consent flows.
- Business value: Enterprise onboarding speed, reduced IT friction, lower support load.

### P2. Observability & SLA Evidence (Traces, Metrics, Logs)

- Baseline: Not instrumented with OTel yet; BullMQ metrics available at dashboard; logs via platform defaults.
- Gaps: OTel traces/metrics/logs; OTLP exporter; SLI/SLO definitions; evidence packs for SLA verification.
- Our team: Implement OTel SDK in API and workers; define service.name and resource attrs; add HTTP/Express/Next.js instrumentation; collectors/exporters; SLA evidence dashboards.
- Investor team: Operational runbooks, alerting thresholds, on-call SLO budget; incident response.
- Joint: Uptime and latency SLIs; auditability of generation pipeline durations.
- Reinforcement: Load testing with trace sampling; error budget policy rollouts.
- Qualitative asks: Collector endpoint, storage backend, dashboard access.
- Business value: Faster incident resolution, contractual SLA proof.

### P3. Export & Interoperability (PDF/DOCX/HTML/SCORM, LMS API)

- Baseline: API for generation; integration guide for LMS via tRPC HTTP. See: docs/LMS-INTEGRATION-ROADMAP.md; docs/API.md.
- Gaps: Export formats and quotas by tier; SCORM 1.2/2004; HTML standalone; API export; watermarking; LMS push flows.
- Our team: Export generators (PDF/DOCX/HTML/SCORM); validators for package structure; quota enforcement per PRICING-TIERS.md.
- Investor team: LMS backend endpoints for import/sync, user/course mapping, gradebook hooks.
- Joint: End-to-end export/import tests on target LMS; acceptance criteria and packaging schema.
- Reinforcement: Automated SCORM lints; HTML offline checks; watermark verification.
- Qualitative asks: Target LMS versions and test tenants.
- Business value: Faster course rollout and LMS compatibility.

### P4. Analytics & Reporting (Engagement, Time-on-Task, Outcomes)

- Baseline: Planned in pricing tiers; not yet implemented.
- Gaps: Event taxonomy, tracking plan, pipelines, dashboards; ROI metrics (Phillips 3–5) per legacy roadmap.
- Our team: Define analytics schema/events; emit events from API; ETL to warehouse; standard dashboards.
- Investor team: LMS-side events and joins (enrollments, completions); stakeholder reporting.
- Joint: Consent and privacy alignment; KPI definitions per tier.
- Reinforcement: Data tests and anomaly detection.
- Qualitative asks: Warehouse destination and BI tool.
- Business value: Demonstrable impact for buyers and renewal confidence.

### P5. Compliance Ops & Audit (Audit Logs, Retention, Evidence)

- Baseline: Audit scope defined in pricing; not yet instrumented.
- Gaps: Audit-event schema; retention per tier; exportable audit trails; reviewer workflows; SLA evidence linkage.
- Our team: Implement audit logging (append-only); retention policies; evidence bundling per job.
- Investor team: Ops processes for reviews, escalations, data requests.
- Joint: Audit exports and legal review checklist.
- Reinforcement: Periodic audit drills; integrity checksums.
- Qualitative asks: Legal requirements per buyer; retention durations by tier.
- Business value: Trust, enterprise readiness, and risk reduction.

### P6. Data Protection & Residency (Tenancy, Region, Backups)

- Baseline: RLS-based isolation; Supabase region control supported; backups present.
- Gaps: Residency posture declaration; cross-region routing; backup/restore drills; DSRs.
- Our team: Region profiles; data flow maps; restore runbooks; DSR automation hooks.
- Investor team: Regional deployment infra and monitoring.
- Joint: Residency in buyer-required regions and controls mapping.
- Reinforcement: Quarterly restore tests; DLP scans for exports.
- Qualitative asks: Target regions; residency clauses.
- Business value: Regulatory compliance and deal unblocker.

---

## Compliance Evidence Packs

For each pillar/workstream, produce an Evidence Pack with:
- Artifacts: reports, exported packages, OTel traces dashboards, audit logs, SCIM logs.
- Tests: unit/contract (SCIM/SSO), SCORM validators, export lints, API e2e, data tests.
- Verification Owner: role accountable for sign-off (see below per pack).
- Sign-off Checklist: pre-agreed checklist per pack.

Verification Owners (by default):
- Identity (P1): Integration Engineer (Investor), Security Lead (Our team) co-sign.
- Observability (P2): SRE/Infra (Investor) with Our team review.
- Export (P3): QA Lead (Joint).
- Analytics (P4): Data Eng (Investor) with Our team schema review.
- Compliance Ops (P5): Compliance Ops (Investor) with Our team tooling.
- Data Protection (P6): Infra Lead (Investor) with Our team policy mapping.

---

## Assumptions & Excluded Scope

- Assumptions: STANDARD tier remains primary focus (docs/PRICING-TIERS.md); LMS integrates via HTTP tRPC; IdP sandbox access provided; OTLP collector available.
- Excluded (for launch): Canvas/Blackboard deep integrations beyond import; multi-agent generation (PREMIUM) unless S3 selected; advanced predictive analytics; full cross-region failover automation.

---

## Decision Log Delta + Impact of Changes

Source decisions: docs/decisions/adoption-20251023.md.

- Delta: Adopt skills (`acceptance-criteria-checker`, `audit-event-schema`, `c4-diagram-template`) and commands (`audit-setup`, `arch-c4`, `ac-check`).
- Gaps identified: Dedicated identity-integrations agent (simple), rbac-abac-designer (simple), SLA instrumentation ownership.

Impact on our backlog:
- Add schema-compliant simple agents (identity-integrations, rbac-abac-designer) following meta-agent-v3 patterns.
- Build export validators and SCORM packaging for STANDARD.
- Add OTel instrumentation and SLA evidence pack generation.

Impact on investor backlog:
- IdP/SCIM enablement (BoxyHQ Jackson or equivalent), LMS backend endpoints for import/export sync, analytics pipelines, compliance ops procedures.

---

## Partner Readiness Matrix

- Identity & Access: IdP sandbox readiness? SCIM enabled? Admin consent flows?  
- Observability: OTLP collector in place? Alerting stack? On-call rotation?  
- Export & Interop: LMS import endpoints maturity? SCORM support?  
- Analytics: Warehouse + BI tool selection? Data governance?  
- Compliance Ops: Audit review process? Evidence storage?  
- Data Protection: Region decision? Backup/restore SLA?

Mark per partner: Ready / Partial / Not ready (captured in scenario tables below).

---

## Roadmap Scenarios

Monthly checkpoints from Nov 2025 → Mar 2026. All scenarios share core foundation; differ by depth and reinforcement cadence.

### S1-Core

- Intent: Minimum viable enterprise posture for early pilots on STANDARD tier.
- Timeline (monthly checkpoints):
  - Nov 2025: OTel baseline (HTTP, API traces), Export PDF/DOCX, SCIM schema agreed.
  - Dec 2025: SSO pilot (OIDC or SAML via bridge), HTML export, audit-event schema live.
  - Jan 2026: SCORM 1.2, SLA dashboards (p50/p95 latency), audit retention (90d STANDARD).
  - Feb 2026: End-to-end LMS import flows, SCIM create/deprovision, DSR hooks.
  - Mar 2026: Launch readiness drill, evidence packs finalized.
- Coverage status table (intended):
  - P1 Identity: Pilot SSO; SCIM basic (users). Readiness: Partial.
  - P2 Observability: Traces+basic metrics; SLO draft. Readiness: Partial.
  - P3 Export: PDF/DOCX/HTML + SCORM 1.2. Readiness: Ready.
  - P4 Analytics: Core events + basic dashboards. Readiness: Partial.
  - P5 Compliance Ops: Audit logs + 90d retention. Readiness: Partial.
  - P6 Data Protection: Residency profile + backup drills. Readiness: Partial.
- Responsibilities:
  - Our team: Export generators; OTel SDK; audit-event schema; SCIM contract tests; CI gates.
  - Investor team: IdP+SCIM pilot; LMS import endpoints; basic analytics pipeline; on-call setup.
  - Joint: E2E SSO, LMS import, SCORM validation, SLA dashboards review.
- Resource asks (qualitative): Low→Medium; investor focus on IdP+LMS endpoints.
- Risks/Mitigations:
  - IdP delays → Use OIDC-first fallback; defer SCIM groups.
  - SCORM packaging issues → Early validators; sample courses.
  - Collector unready → Local dev exporter; switch to logs-only fallback.
- Assumptions & Exclusions: No SCORM 2004; limited analytics; no deep Canvas integration.
- Early warnings:
  - P1: Missing IdP sandbox by Dec 2025.
  - P2: Trace coverage <70% by Jan 2026.
  - P3: SCORM validator fails twice in CI by Feb 2026.
  - P4: No warehouse chosen by Jan 2026.

### S2-Plus

- Intent: Strengthened compliance posture; fuller analytics; broader exports.
- Timeline:
  - Nov 2025: Same as S1 + SCIM group schema;
  - Dec 2025: SAML enterprise pilot via Jackson; OTLP metrics; SLA p95 targets.
  - Jan 2026: SCORM 1.2 + HTML offline; API export; audit export bundles.
  - Feb 2026: Canvas/Moodle import pilots; analytics dashboards v1; incident runbooks.
  - Mar 2026: Launch readiness with customer evidence review.
- Coverage (intended):
  - P1 Identity: SSO SAML/OIDC; SCIM users+groups. Readiness: Ready.
  - P2 Observability: Traces+metrics+logs; SLO policy. Readiness: Ready.
  - P3 Export: PDF/DOCX/HTML + SCORM 1.2 + API export. Readiness: Ready.
  - P4 Analytics: Engagement/time dashboards. Readiness: Partial→Ready.
  - P5 Compliance Ops: Audit exports; reviewer workflows. Readiness: Partial.
  - P6 Data Protection: Residency posture + restore test. Readiness: Ready.
- Responsibilities:
  - Our team: Everything in S1 + API export; audit bundle tooling; OTel logs.
  - Investor team: SCIM groups; Canvas/Moodle pilots; runbooks and alerts.
  - Joint: Evidence pack dry‑runs; buyer review.
- Resource asks: Medium; investor needs dedicated IAM and LMS engineers.
- Risks/Mitigations: SCIM mapping complexity → staged mapping; logs volume → sampling.
- Early warnings: 
  - P1: SCIM group sync error rate >1% in CI.
  - P2: p95 > target for two sprints.
  - P3: API export rate limits unmodeled by Feb 2026.

### S3-Enterprise

- Intent: Maximum coverage including SCORM 2004, predictive analytics, premium polish.
- Timeline:
  - Nov 2025: Identity design reviews; OTel full plan; export backlog vetted.
  - Dec 2025: SAML GA; SCIM groups+entitlements; traces+metrics+logs complete.
  - Jan 2026: SCORM 1.2 + 2004; HTML+API export GA; audit reviewers UI.
  - Feb 2026: Analytics v2 (predictions optional); Canvas/Blackboard pilots.
  - Mar 2026: Launch review with enterprise buyers.
- Coverage:
  - P1: SSO GA + SCIM users/groups/entitlements. Ready.
  - P2: Full OTel stack; SLOs and error budgets enforced. Ready.
  - P3: All exports including SCORM 2004 + API export. Ready.
  - P4: Advanced analytics (optional predictive). Partial→Ready.
  - P5: Compliance Ops: reviewer workflows + evidence UI. Partial→Ready.
  - P6: Residency + restore + DSR automation. Ready.
- Responsibilities:
  - Our team: All S2 + SCORM 2004; compliance UI scaffolding.
  - Investor team: Deep LMS integrations, predictive analytics infra, compliance ops staffing.
  - Joint: Buyer compliance reviews and sign‑off.
- Resource asks: Medium→High; cross‑team squads.
- Risks/Mitigations: Scope creep → guardrails by tier; analytics complexity → phase optional.
- Early warnings: Missed Feb pilots; backlog churn >20% month‑over‑month.

---

## Global Risk Register

- Identity integration slippage → affects onboarding; EWI: missed IdP sandbox milestone.
- SCORM packaging defects → affects export; EWI: validator failures in CI.
- Telemetry gaps → affects SLA evidence; EWI: traces coverage <70%.
- Analytics data quality → affects buyer value; EWI: failed data tests >2%.
- Residency ambiguity → affects compliance; EWI: region decision pending into Jan 2026.
- Team capacity contention → affects delivery; EWI: spillover >15% each sprint.

Responsibilities: Identity (Joint), Observability (Our + Investor Ops), Export (Joint), Analytics (Investor-led), Compliance Ops (Joint), Data Protection (Investor-led with Our mapping).

Dependencies: Identity→Audit/Export; Observability→SLA evidence; LMS endpoints→Export acceptance; Warehouse→Analytics dashboards.

---

## Highlighted Workstreams

- Identity (P1): SSO bridge, SCIM sync, JWT claims mapping, test matrices.
- Observability (P2): OTel SDK, OTLP exporter, SLI dashboards, runbooks.
- Export (P3): PDF/DOCX/HTML/SCORM packaging, validators, quotas.
- Analytics (P4): Event schema, pipelines, dashboards.
- Compliance Ops (P5): Audit logs, retention, evidence bundling.
- Data Protection (P6): Residency profiles, backup/restore drills, DSR automation.

---

## Dependency Mapping

- P1 → P5/P3: SCIM roles feed export scopes and audit trails.
- P2 → SLA packs: Traces/metrics/logs roll into evidence packs and early warnings.
- P3 ← LMS endpoints: Import APIs and SCORM support are investor prerequisites.
- P4 ← P1/P2: Identity attributes and telemetry correlate to engagement views.
- P6 ↔ P3: Export storage and region policies co‑govern data residency.

---

## Story Guidance (Structure Only)

For each Epic/Story include:
- Labels, Priority, Scenario ID (S1/S2/S3), Component, Environment.
- Blocked-by: Quality Gate name (from QUALITY-GATES-SPECIFICATION.md).
- Evidence Required: artifact path (e.g., docs/evidence/p3-export/2026-02-scorm-bundle.md).
- Acceptance Anchors: stable section anchors (e.g., #p3-export-and-interoperability).
- Verification Owner: role (see Evidence Packs section).
- Risk Linkage: early warning indicators referenced.
- Responsibility: Our team | Investor team | Joint.
- Workstream tag: Identity | Observability | Export | Analytics | Compliance Ops | Data Protection.
- Dependency notes: what this depends on, and what depends on it.

---

## Cross-References

- Agents Architecture: docs/Agents Ecosystem/ARCHITECTURE.md#return-control-pattern
- Meta-Agent Schema: .claude/agents/meta-agent-v3.md#agent-types
- Quality Gates: docs/Agents Ecosystem/QUALITY-GATES-SPECIFICATION.md#quality-gates
- API & Auth: docs/API.md#authentication, docs/API.md#authorization
- LMS Integration: docs/LMS-INTEGRATION-ROADMAP.md#current-architecture-stage-1
- Technical Spec: docs/TECHNICAL_SPECIFICATION_PRODUCTION_EN.md#3-target-production-architecture
- Pricing Tiers (Export scope): docs/PRICING-TIERS.md#📤-course-export--integrations

