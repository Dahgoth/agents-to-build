# Integration Implementation Phase — Russia–Dubai Split

## Objectives

- Introduce `region_code` claim in JWT and propagate through API layer
- Implement region‑aware RLS and data models (RU vs AE)
- Deploy split infrastructure (RU, AE) with region‑scoped logging and audit
- Prepare SCC 2021 + TIA pack and breach runbooks (GDPR + UAE PDPL)

## Tasks

1. Token Layer
   - Extend `custom_access_token_hook` to include `region_code`
   - Validate claim in API gateway and enforce checks
2. Database & RLS
   - Add `region_code` to tenant tables and enforce via unified policies
   - Add helper functions to avoid RLS recursion
3. Infrastructure
   - Provision RU and AE stacks; segregate storage and networking
   - Configure BullMQ orchestration per region
4. Compliance
   - Prepare SCC 2021 + TIA templates for EU users
   - Draft and test breach runbooks (GDPR Art. 33/34, UAE PDPL)
5. Observability
   - Implement region‑scoped compliance logs and alerts

## Anchors

- [docs/API.md:137-176]
- [docs/SUPABASE-DATABASE-REFERENCE.md:639-707]
- [docs/Agents Ecosystem/REPORT-TEMPLATE-STANDARD.md]
