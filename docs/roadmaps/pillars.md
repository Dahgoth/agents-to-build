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
