---
report_type: evidence-index
generated: 2025-11-06T08:57:00+03:00
version: 2.3.0
status: success
agent: integration-research-agent
duration: ~22m
jurisdictions_analyzed: ["Russia", "UAE", "EU", "US", "Canada"]
scenarios_evaluated: 3
compliance_frameworks: ["GDPR", "152-FZ", "UAE-PDPL", "SOC2", "ISO27001", "NIST-CSF", "PCI-DSS"]
repository_integration: true
follows_report_standard: "REPORT-TEMPLATE-STANDARD.md"
executive_ready: true
presentation_optimized: true
mcp_enhanced: true
anti_contamination_verified: true
fresh_analysis_certified: true
---

# Evidence Index — Citations & MCP Usage

Declaration: No previous analysis files referenced or consulted.

## Pre‑Execution Quarantine

- Quarantine Manifest: docs/reports/integration/2025-11/2025-11-06-0857-MSK-quarantine-manifest.md

## EXTERNAL‑STANDARD Citations (Authoritative)

- GDPR: <https://eur-lex.europa.eu/eli/reg/2016/679/oj>
- UK GDPR/IDTA: <https://ico.org.uk/for-organisations/sccs-idta-addendum/international-data-transfer-agreement-and-guidance/>
- CCPA/CPRA: <https://cppa.ca.gov/regulations/>
- PIPEDA: <https://priv.gc.ca/en/privacy-topics/privacy-laws-in-canada/the-personal-information-protection-and-electronic-documents-act-pipeda/>
- RU 152‑FZ: <https://rkn.gov.ru/personal-data/>
- Sovereign Internet: <https://pravo.gov.ru/>
- Foreign Agent Registry: <https://minjust.gov.ru/ru/activity/directions/923/>
- UAE PDPL: <https://u.ae/en/information-and-services/justice-safety-and-the-law/personal-data-protection-law>
- DIFC DP Law: <https://www.difc.ae/business/laws-and-regulations/data-protection/>
- UAE Cybersecurity: <https://u.ae/en/information-and-services/justice-safety-and-the-law/cybersecurity>
- FERPA: <https://www2.ed.gov/policy/gen/guid/fpco/ferpa/index.html>
- COPPA: <https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa>
- SOC2: <https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/aicpasoc2report.html>
- ISO 27001: <https://www.iso.org/isoiec-27001-information-security.html>
- NIST CSF 2.0: <https://www.nist.gov/cyberframework>
- PCI DSS: <https://www.pcisecuritystandards.org/document_library>
- EU DGA 2022/868: <https://eur-lex.europa.eu/eli/reg/2022/868/oj>
- EU Data Act 2023/2854: <https://eur-lex.europa.eu/eli/reg/2023/2854/oj>
- SCC 2021/914: <https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj>
- Schrems II C‑311/18: <https://curia.europa.eu/juris/document/document.jsf?docid=228677>

## Canonical Repository Evidence

- README overview and stack: README.md:1
- Technical spec: docs/TECHNICAL_SPECIFICATION_PRODUCTION_EN.md:52
- API capabilities: docs/API.md:1
- Database & RLS/JWT: docs/SUPABASE-DATABASE-REFERENCE.md:27

## MCP Servers Used

- Supabase Docs MCP — researched RLS/JWT policy patterns and guidance.
- Context7 — sourced RLS examples using auth.jwt() for policy design.
