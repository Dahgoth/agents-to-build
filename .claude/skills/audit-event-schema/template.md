# Audit Event Taxonomy Template

## Canonical Fields

| Field | Type | Required | Sensitivity | Notes |
| :--- | :--- | :---: | :--- | :--- |
| event_id | string(uuid) | ✓ | none | Unique ID |
| timestamp | string(date-time) | ✓ | none | ISO-8601 |
| actor_id | string | ✓ | Sensitive | Hash in logs |
| actor_role | string |  | none | e.g., admin, instructor |
| action | string | ✓ | none | e.g., login, role_changed |
| object_type | string | ✓ | none | e.g., user, course |
| object_id | string |  | Sensitive | Truncate in logs |
| org_id | string |  | none | Organization/tenant |
| tenant_id | string |  | none | Tenant context |
| result | enum |  | none | success|failure |
| reason | string |  | none | Optional human reason |
| request_id | string |  | none | Trace correlation |
| correlation_id | string |  | none | Cross-service id |
| source_ip | string |  | Sensitive | Redact or geo-only |
| user_agent | string |  | none |  |
| severity | enum |  | none | info|warning|critical |
| pii | enum | ✓ | none | none|hashed|truncated |
| metadata | object |  | Sensitive | Free-form payload |

## Category Matrix (example)

| Category | Typical Actions | Retention (days) | Access Roles |
| :--- | :--- | ---: | :--- |
| auth | login, logout, password_reset | 365 | security, ops |
| role_change | role_assigned, role_revoked | 1825 | security, compliance |
| data_export | export_requested, export_delivered | 1825 | security, compliance |
| payment | invoice_created, payment_succeeded | 2555 | finance, security |
| policy_change | policy_updated | 1825 | compliance, security |

## JSON Schema (insert from SKILL.md)

```json
{ /* ... */ }
```

