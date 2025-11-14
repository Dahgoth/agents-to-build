---
report_type: evidence-index
generated: 2025-11-06T06:52:54+03:00
version: 2025-11-06
status: success
agent: integration-research-agent
duration: 9m 30s
jurisdictions_analyzed: ["Russia", "UAE", "EU", "US", "Canada"]
scenarios_evaluated: 3
compliance_frameworks: ["GDPR", "152-FZ", "UAE-PDPL", "SOC2", "ISO27001", "NIST-CSF", "PCI-DSS"]
repository_integration: true
---

# Evidence Index (External and Canonical Sources)

This index consolidates authoritative external regulatory sources alongside canonical repository files. All external references are marked as EXTERNAL-STANDARD with official URLs.

## Canonical Repository Sources

- [docs/TECHNICAL_SPECIFICATION_PRODUCTION_EN.md]
- [docs/IMPLEMENTATION_ROADMAP_EN.md]
- [docs/PROJECT_ROADMAP_EN_2025-10-31_0929.md] (not found in repo – replaced by REQUIREMENTS.md where applicable)
- [docs/API.md]
- [docs/SUPABASE-DATABASE-REFERENCE.md]
- [docs/ARCHITECTURE-DIAGRAM.md]
- [docs/Agents Ecosystem/REPORT-TEMPLATE-STANDARD.md]

## EXTERNAL-STANDARD — Multi-Jurisdictional Privacy & Transfers

- EXTERNAL-STANDARD GDPR (EU) — Regulation (EU) 2016/679 (eur-lex): <https://eur-lex.europa.eu/eli/reg/2016/679/oj>
- EXTERNAL-STANDARD EDPB Recommendations 01/2020 (supplementary measures post-Schrems II): <https://edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplementary-transfer_en>
- EXTERNAL-STANDARD Standard Contractual Clauses 2021 — Commission Implementing Decision (EU) 2021/914: <https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj>
- EXTERNAL-STANDARD Schrems II — CJEU Case C‑311/18 (CURIA): <https://curia.europa.eu/juris/liste.jsf?num=C-311/18>
- EXTERNAL-STANDARD EU Data Governance Act (Reg. 2022/868): <https://eur-lex.europa.eu/eli/reg/2022/868/oj>
- EXTERNAL-STANDARD EU Data Act (Reg. 2023/2854): <https://eur-lex.europa.eu/eli/reg/2023/2854/oj>

## EXTERNAL-STANDARD — UK, US (California), Canada

- EXTERNAL-STANDARD UK GDPR (ICO Guide): <https://ico.org.uk/for-organisations/guide-to-data-protection/uk-gdpr/>
- EXTERNAL-STANDARD UK IDTA & Addendum (ICO): <https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/international-data-transfer-agreement-and-addendum/>
- EXTERNAL-STANDARD CCPA/CPRA Statute (California Legislature): <https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&division=3.&title=1.81.5.&part=4>.
- EXTERNAL-STANDARD CPPA Regulations (California Privacy Protection Agency): <https://cppa.ca.gov/regulations/index.html>
- EXTERNAL-STANDARD PIPEDA (Justice Laws Canada): <https://laws-lois.justice.gc.ca/eng/acts/P-8.6/>
- EXTERNAL-STANDARD OPC Guidance on Cross-Border Processing (Canada): <https://www.priv.gc.ca/en/privacy-topics/privacy-laws-in-canada/the-personal-information-protection-and-electronic-documents-act-pipeda/pipeda-compliance-help/pipeda-compliance-and-training-tools/gl_dpo_090127/>

## EXTERNAL-STANDARD — Russian Federation

- EXTERNAL-STANDARD Federal Law No. 152‑FZ (Personal Data) — official portal (pravo.gov.ru): <https://pravo.gov.ru/proxy/ips/?docbody=&prevDoc=102109567&backlink=1&&nd=102108778>
- EXTERNAL-STANDARD Roskomnadzor — Operators and Localization Requirements: <https://rkn.gov.ru/personal-data/authority/pd-operators/>
- EXTERNAL-STANDARD Sovereign Internet Law (Federal Law No. 90‑FZ amendments): <https://pravo.gov.ru/proxy/ips/?docbody=&nd=102197110>
- EXTERNAL-STANDARD Foreign Agent Registry (Ministry of Justice): <https://minjust.gov.ru/ru/documents/7756/>
- EXTERNAL-STANDARD GOST R 34.10‑2012 (digital signature): <https://protect.gost.ru/v.aspx?control=7&id=179085>
- EXTERNAL-STANDARD GOST R 34.12‑2015 (block ciphers incl. "Kuznyechik"): <https://protect.gost.ru/v.aspx?control=7&id=197237>

Notes:

- Enhanced administrative fines for personal data violations are governed by the Code of Administrative Offences (Art. 13.11). Exact penalty bands must be verified against the current consolidated text on the official portal (pravo.gov.ru). Treat amounts like 18M RUB as jurisdiction‑specific and subject to amendment; escalate to counsel for confirmation.

## EXTERNAL-STANDARD — UAE / DIFC

- EXTERNAL-STANDARD UAE PDPL — Federal Decree‑Law No. 45 of 2021 (u.ae): <https://u.ae/en/information-and-services/justice-safety-and-the-law/personal-data-protection-law>
- EXTERNAL-STANDARD DIFC Data Protection Law and Regulations: <https://www.difc.ae/business/operating/data-protection/>
- EXTERNAL-STANDARD UAE Cybercrime/Cybersecurity Legal Framework: <https://u.ae/en/about-the-uae/digital-uae/cyberlaws>

## EXTERNAL-STANDARD — Education-Sector (US)

- EXTERNAL-STANDARD FERPA — U.S. Dept. of Education: <https://studentprivacy.ed.gov/ferpa>
- EXTERNAL-STANDARD COPPA — FTC Rule: <https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa>

## EXTERNAL-STANDARD — Security & Audit Frameworks

- EXTERNAL-STANDARD SOC 2 — AICPA SOC for Service Organizations: <https://us.aicpa.org/interestareas/frc/assuranceadvisoryservices/socforserviceorganizations>
- EXTERNAL-STANDARD ISO/IEC 27001 — ISMS Requirements (ISO): <https://www.iso.org/standard/27001>
- EXTERNAL-STANDARD NIST Cybersecurity Framework 2.0: <https://www.nist.gov/cyberframework>
- EXTERNAL-STANDARD PCI DSS 4.0 — PCI SSC Documents Library: <https://www.pcisecuritystandards.org/document_library?category=pcidss&document=pci_dss>

---

## Cross-Reference Map to Canonical Capabilities

- RLS/JWT tenancy enforcement present but lacks region-based residency tags — see [docs/SUPABASE-DATABASE-REFERENCE.md:Overview:20-32] and [docs/SUPABASE-DATABASE-REFERENCE.md:RLS Policies:639-707]. Gap vs. 152‑FZ and EU/UAE residency controls.
- JWT claims present (`role`, `organization_id`), region missing — see [docs/API.md:Authentication Method:137-176] and [docs/SUPABASE-DATABASE-REFERENCE.md:Custom JWT Claims:729-746].
- API supports LMS integration (webhooks, generation/jobs) — see [docs/API.md:Multi-Client Integration:60-122] and [docs/API.md:API Endpoints…].

Each scenario’s compliance mapping in the consolidated report references this index for EXTERNAL-STANDARD anchors.
