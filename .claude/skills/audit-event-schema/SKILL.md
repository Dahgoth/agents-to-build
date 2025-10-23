---
name: audit-event-schema
description: Define audit event taxonomy and JSON schema with retention and access controls. Use to standardize security/compliance logging across the platform.
---

# Audit Event Schema

Design a privacy-aware audit taxonomy with consistent fields, retention, and access rules.

## When to Use

- Establish or revise audit logging standards
- Prepare for compliance or incident response needs
- Align services on a single event schema

## Inputs

Provide event categories and domain examples (optional):

```json
{
  "categories": ["auth", "role_change", "data_export", "payment", "policy_change"],
  "defaults": {
    "retention_days": {"auth": 365, "role_change": 1825, "data_export": 1825, "payment": 2555, "policy_change": 1825},
    "access": {"analyst": ["auth"], "security": ["*"], "ops": ["auth","payment"], "compliance": ["*"]}
  }
}
```

## Instructions

1. Define Canonical Fields
   - `event_id` (UUID), `timestamp` (ISO-8601), `actor_id`, `actor_role`, `action`, `object_type`, `object_id`, `org_id`, `tenant_id`, `result` (success|failure), `reason`, `request_id`, `correlation_id`, `source_ip`, `user_agent`, `severity`, `pii` (none|hashed|truncated), `metadata` (object).
2. Redaction & Classification
   - Mark fields as Sensitive/PII and specify redaction rules.
3. Category Matrix
   - For each category: typical actions, fields required/optional, retention days, access roles.
4. JSON Schema
   - Provide a base schema (draft-07 compatible) to validate events.
5. Verification
   - Include example events; ensure they validate and respect redaction rules.

## Output

- Markdown tables for fields and category matrix
- JSON schema block for events
- Example events for common categories

## Examples

### Fields Table (excerpt)

| Field | Type | Required | Sensitivity | Notes |
| :--- | :--- | :---: | :--- | :--- |
| event_id | string(uuid) | ✓ | none | Unique per event |
| timestamp | string(date-time) | ✓ | none | ISO-8601 |
| actor_id | string | ✓ | Sensitive | Hash in logs, full in audit store |
| action | string | ✓ | none | e.g., login, export_requested |
| object_type | string | ✓ | none | e.g., course, user |
| pii | string(enum) | ✓ | none | none|hashed|truncated |

### JSON Schema (base)

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "AuditEvent",
  "type": "object",
  "required": ["event_id","timestamp","actor_id","action","object_type","pii"],
  "properties": {
    "event_id": {"type":"string","format":"uuid"},
    "timestamp": {"type":"string","format":"date-time"},
    "actor_id": {"type":"string"},
    "actor_role": {"type":"string"},
    "action": {"type":"string"},
    "object_type": {"type":"string"},
    "object_id": {"type":"string"},
    "org_id": {"type":"string"},
    "tenant_id": {"type":"string"},
    "result": {"type":"string","enum":["success","failure"]},
    "reason": {"type":"string"},
    "request_id": {"type":"string"},
    "correlation_id": {"type":"string"},
    "source_ip": {"type":"string"},
    "user_agent": {"type":"string"},
    "severity": {"type":"string","enum":["info","warning","critical"]},
    "pii": {"type":"string","enum":["none","hashed","truncated"]},
    "metadata": {"type":"object"}
  },
  "additionalProperties": false
}
```

## Report / Response

Return:
- Fields table and category matrix
- JSON schema block
- Example events and retention/access summary

