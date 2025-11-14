# ADR-003: Integration Scenario Selection (v2.3.0)
## Status
Proposed
## Context
Dubai March 2026 requires a Russia–Dubai split with RU localization (152‑FZ) and UAE PDPL for global markets, followed by EU/US expansion. Prioritizing summit conversions and investor‑grade compliance evidence, the team must choose a delivery model that enables enforceable region controls, fast iteration, and clear accountability.
## Decision
Select Scenario B (AI Team Infrastructure — Ownership Model) as the primary path. Maintain Scenario C (OSS LMS Integration) as a pilot engine feeding production into Scenario B. Scenario A (Guided Integration) is conditional on partner SLAs and audit commitments.
## Consequences
### Positive
- Enforceable region controls (tokens + policies + partitions)
- Clean audit trail supporting SOC2/ISO 27001 alignment
- Predictable delivery independent of partner bandwidth
### Negative
- Higher infra/ops overhead across RU/AE
- Requires rigorous runbooks and monitoring
## References
- Executive Summary: docs/reports/executive/2025-11/2025-11-06-0857-MSK-executive-summary.md
- Consolidated Report: docs/reports/integration/2025-11/2025-11-06-0857-MSK-consolidated-report.md
- Compliance Analysis: docs/reports/compliance/2025-11/2025-11-06-0857-MSK-compliance-analysis.md
- Technical Validation: docs/reports/security/2025-11/2025-11-06-0857-MSK-technical-validation.md
- Evidence Index: docs/reports/integration/2025-11/2025-11-06-0857-MSK-evidence-index.md
