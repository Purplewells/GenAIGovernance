---
title: AI-003 Generative AI Patient Service Assistant — Risk Assessment
date: 2026-09-11
lifecycle_stage: Design
scope: Patient-facing generative AI chatbot for routine enquiries at Telleion Hospitals NHS Foundation Trust
decision_requested: Whether the patient service assistant chatbot can proceed to detailed design and pre-deployment testing
owner: AI Governance Lead
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Draft for consultation
---

# AI-003 Generative AI Patient Service Assistant — Risk Assessment

## Executive Summary

Telleion Hospitals NHS Foundation Trust proposes deploying a generative AI patient service assistant chatbot to handle routine patient and carer enquiries. The chatbot would be accessible via the Trust website, patient portal, and SMS, and would escalate complex, clinical, or safeguarding-related queries to human staff.

This assessment evaluates the inherent risks of generative AI in a patient-facing, healthcare context, identifies key controls required to mitigate those risks, and determines whether residual risk is acceptable given the organisation's risk tolerance.

**Risk rating: HIGH (inherent) → MEDIUM (with mitigating controls)**

**Decision:** The use case can proceed to detailed design and pre-deployment testing, conditional on:
1. Implementation of security, data protection, and clinical-safety controls outlined in this assessment
2. Completion of prompt-injection security testing and RAG assurance assessment
3. Formalisation of human-escalation procedure and monitoring plan
4. Board approval of residual risk and accountability

## Risk Assessment Method

This assessment uses the NIST AI Risk Management Framework 1.0 (NIST AI RMF 1.0, Version 1.0, January 2024) and the OWASP Top 10 for Large Language Model Applications (OWASP LLM Top 10, 2024) as reference frameworks.

- **Inherent risk** = Risk prior to controls
- **Residual risk** = Risk after controls are implemented and operating effectively
- **Risk tolerance** = The level of risk the organisation is willing to accept for this use case

---

## Risk Register

### INHERENT RISK: Hallucinated Information

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-001 |
| **Description** | The LLM generates plausible-sounding but factually incorrect information (hallucination) in response to patient enquiries, potentially misleading patients about appointments, medications, test results, symptoms, or clinical advice. |
| **Risk Category** | Accuracy; Patient Safety; Information Integrity |
| **Likelihood** | High — LLMs are known to hallucinate, particularly when trained on general internet data without healthcare-specific grounding. |
| **Impact** | High — Patient harm from incorrect medical information, missed clinical appointments, medication errors, delayed treatment, patient distress, reputational damage, regulatory concern, liability exposure. |
| **Inherent Risk** | **High** (High likelihood × High impact) |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **RAG (Retrieval-Augmented Generation)** | Ground LLM responses in verified Trust information only. | Clinical Informatics Lead |
| **Response Validation & Filtering** | Screen responses for hallucination patterns and medical misinformation before delivery. | Clinical Safety Officer |
| **Clinician Review of Approved Content** | Subject-matter expert reviews all source information before ingestion. | Chief Medical Officer |
| **Human Escalation for Clinical Enquiries** | Escalate enquiries containing clinical symptoms or concerns to clinicians. | PALS Manager |

**Residual Risk:** Medium (escalation and RAG reduce risk; monitoring provides safety net)

---

### INHERENT RISK: Outdated Information

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-002 |
| **Description** | Information becomes stale as the Trust updates policies, procedures, appointment systems, or visiting arrangements. Patients receive outdated guidance. |
| **Risk Category** | Information Integrity; Operational Risk |
| **Likelihood** | Medium-High |
| **Impact** | Medium — Patient inconvenience, operational disruption, reputational damage. |
| **Inherent Risk** | **Medium-High** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Information Maintenance Schedule** | Quarterly review of all approved information; automated tracking of retention dates. | Clinical Informatics Lead |
| **Change Notification Integration** | Receive alerts when key systems (EPR, policies) change; trigger immediate review. | System Administrators |
| **Patient Feedback Loop** | Monitor patient feedback for outdated-information reports; weekly review. | PALS Manager |

**Residual Risk:** Low (quarterly review + change notifications reduce risk significantly)

---

### INHERENT RISK: Inappropriate Medical Advice

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-003 |
| **Description** | Chatbot provides medical advice, diagnostic guidance, or treatment recommendations outside scope of patient information service; may delay appropriate clinical assessment. |
| **Risk Category** | Patient Safety; Clinical Risk; Liability |
| **Likelihood** | High |
| **Impact** | High — Patient harm from missed diagnosis, delayed treatment, adverse drug interactions, liability. |
| **Inherent Risk** | **High** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Explicit Scope & Disclaimer** | Clear statement chatbot is information only, not clinical advice. | Communications; Legal |
| **Symptom & Clinical Concern Detection** | Detect symptoms; escalate immediately without medical response. | Clinical Safety Officer |
| **Approved FAQ Scope** | Restrict source information to non-clinical topics only. | Chief Medical Officer |
| **Human Escalation to Clinician** | Route escalations to qualified clinician for clinical concerns. | Chief Medical Officer |

**Residual Risk:** Medium (escalation + detection reduce risk; monitoring essential)

---

### INHERENT RISK: Prompt Injection Attacks

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-004 |
| **Description** | Malicious user crafts prompt to manipulate LLM: bypass safety instructions, disclose confidential information, generate harmful content, impersonate staff. |
| **Risk Category** | Security; Information Disclosure; System Integrity |
| **Likelihood** | Medium-High — Attack techniques are published; attack surface large. |
| **Impact** | Medium-High — Information disclosure, reputational damage, patient harm, regulatory concern. |
| **Inherent Risk** | **Medium-High** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Input Sanitisation & Validation** | Clean enquiries; remove/escape injection-attack patterns. | Lead Developer |
| **LLM Prompt Hardening** | Resilient system prompt with explicit boundaries and repeated safety instructions. | Lead Developer + Clinical Safety Officer |
| **Output Filtering for Malicious Content** | Detect and block outputs showing successful injection (confidential data, harmful advice, impersonation). | Clinical Safety Officer + Security Lead |
| **Security Testing & Red-Teaming** | Formal security testing, including prompt-injection attack simulation, before deployment and annually. | Information Security Lead |

**Residual Risk:** Low-Medium (security testing confirms controls; ongoing vigilance required)

---

### INHERENT RISK: Personal Information Disclosure

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-005 |
| **Description** | Patient personal or health information submitted to chatbot is inadvertently disclosed, shared with unauthorised parties, used without consent, or retained longer than necessary. |
| **Risk Category** | Data Protection; Privacy; Security; Regulatory Compliance |
| **Likelihood** | Medium — LLMs can memorise training data; vendor access to data increases risk. |
| **Impact** | High — GDPR/Data Protection Act breach, patient privacy violation, regulatory investigation, penalties, reputational damage. |
| **Inherent Risk** | **Medium-High** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Data Processing Agreement (DPA)** | Compliant DPA with every vendor/platform; forbid model training on patient data. | Chief Data Protection Officer + Legal |
| **Encryption in Transit & at Rest** | TLS 1.2+ in transit; AES-256 at rest. | Information Security Lead |
| **Access Control & Identity Management** | RBAC; MFA for admins; monthly audit of access logs. | Information Security Lead |
| **Data Retention & Deletion** | 90-day retention; automated deletion; patient right to request deletion. | Chief Data Protection Officer |
| **Data Privacy Impact Assessment (DPIA)** | DPIA per UK GDPR Article 35; annual review; consultation with patient advocates. | Chief Data Protection Officer |
| **No Use of Patient Data for Model Training** | Contractual and technical prohibition; annual vendor audit. | Chief Data Protection Officer |

**Residual Risk:** Low (strong data-protection controls; DPA critical)

---

### INHERENT RISK: Malicious Users / Misuse

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-006 |
| **Description** | Malicious actors test attacks, generate spam, impersonate patients, access other patients' data, stress-test system. High-volume attacks degrade service. |
| **Risk Category** | Security; Availability; Information Integrity |
| **Likelihood** | Medium — Public-facing system; large attack surface. |
| **Impact** | Medium — Service degradation, operational disruption, reputational damage. |
| **Inherent Risk** | **Medium** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Rate Limiting & DDoS Protection** | Limit enquiries per user/IP; implement DDoS protection. | Information Security Lead |
| **Anomaly Detection & Alerting** | Monitor for unusual patterns; alert security team within 5 minutes. | Information Security Lead |
| **Content Moderation & Filtering** | Flag/filter abusive language, spam, attack patterns. | Information Security Lead |
| **Authentication for Sensitive Operations** | Require NHS login for personal data access. | Clinical Informatics Lead |

**Residual Risk:** Low (rate limiting + monitoring prevent most attacks)

---

### INHERENT RISK: Incorrect Escalation

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-007 |
| **Description** | Chatbot fails to escalate queries requiring escalation (false negative) — e.g. urgent symptoms not escalated — OR escalates routine queries unnecessarily (false positive). |
| **Risk Category** | Patient Safety; Operational Efficiency |
| **Likelihood** | Medium-High — LLM escalation decisions inherently uncertain. |
| **Impact** | High (false negatives: delayed care) / Low (false positives: staff burden) |
| **Inherent Risk** | **Medium-High** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Escalation Rule Set** | Explicit, clinically-validated rules for what must escalate. | Chief Medical Officer + Clinical Safety Officer |
| **Hybrid Escalation: Rules + LLM** | Combine rule-based (deterministic) + LLM confidence scoring. Escalate if rule triggered OR confidence low. | Lead Developer + Clinical Safety Officer |
| **Human Escalation Procedure** | Formalised routing, SLA, documentation. | PALS Manager + Chief Medical Officer |
| **Monitoring of Escalation Effectiveness** | Track false-negative/positive rates; monitor patient outcomes; adjust rules monthly. | Clinical Safety Officer |

**Residual Risk:** Low-Medium (rules + hybrid approach reduce risk; ongoing monitoring)

---

### INHERENT RISK: Accessibility Issues

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-008 |
| **Description** | Chatbot not accessible to patients with disabilities (visual, hearing, cognitive, motor, literacy). Excludes vulnerable patients; breaches Equality Act 2010. |
| **Risk Category** | Equity; Accessibility; Regulatory Compliance |
| **Likelihood** | Medium-High |
| **Impact** | Medium — Exclusion of vulnerable patients, regulatory action, reputational damage. |
| **Inherent Risk** | **Medium** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Accessibility Compliance (WCAG 2.1 AA)** | Design and test to meet WCAG 2.1 Level AA. | Digital Accessibility Officer |
| **Plain Language & Adjustable Text Size** | Flesch Reading Ease >60; font adjustment; simple-language option. | Communications Lead |
| **Captions & Audio Description** | Full captions for audio/video; audio descriptions for visual content. | Digital Accessibility Officer |
| **Multiple Access Channels** | Accessible via website, mobile app, SMS, voice (if applicable). | Digital Services Lead |
| **Accessibility Audit & Testing** | Professional audit (WCAG 2.1 AA) + testing with disabled users before deployment and annually. | Digital Accessibility Officer |

**Residual Risk:** Low (WCAG compliance + professional audit + user testing ensure accessibility)

---

### INHERENT RISK: Patient Misunderstanding

| Attribute | Assessment |
|---|---|
| **Risk ID** | GEN-AI-009 |
| **Description** | Patients misinterpret chatbot responses: don't realise it's AI (not clinician), assume response is clinical advice, don't understand need for human care, incorrectly act on information. |
| **Risk Category** | Patient Safety; Communication; Liability |
| **Likelihood** | Medium-High — LLMs appear authoritative; vulnerable patients may not fully understand limitations. |
| **Impact** | Medium — Patient confusion, delayed care-seeking, inappropriate self-treatment, liability. |
| **Inherent Risk** | **Medium** |

**Mitigating Controls:**

| Control | Objective | Owner |
|---|---|---|
| **Clear Disclaimer & Labelling** | Prominent statement before each interaction: "AI chatbot, information only, not clinical advice." | Communications Lead |
| **Explicit Guidance on When to Seek Help** | Clear guidance: "Contact GP if you have symptoms, health concerns, medication questions, emergencies." | Communications Lead + Clinical Safety Officer |
| **Conversational Design: Humility & Uncertainty** | Appropriate uncertainty in responses; avoid overconfident tone; acknowledge limitations. | Lead Developer + Communications Lead |
| **Educate Patients About Chatbot Capability** | Website page, posters, FAQ explaining what chatbot does/doesn't do. | Communications Lead + Digital Services Lead |

**Residual Risk:** Low-Medium (disclaimers help but not foolproof; requires ongoing monitoring and patient education)

---

## Summary Table: Residual Risk

| Risk ID | Risk | Inherent | Residual | Acceptable? |
|---|---|---|---|---|
| GEN-AI-001 | Hallucinated Information | High | Medium | Yes (with monitoring) |
| GEN-AI-002 | Outdated Information | Medium-High | Low | Yes |
| GEN-AI-003 | Inappropriate Medical Advice | High | Medium | Yes (with escalation & monitoring) |
| GEN-AI-004 | Prompt Injection | Medium-High | Low-Medium | Yes |
| GEN-AI-005 | Personal Information Disclosure | Medium-High | Low | Yes |
| GEN-AI-006 | Malicious Users | Medium | Low | Yes |
| GEN-AI-007 | Incorrect Escalation | Medium-High | Low-Medium | Yes |
| GEN-AI-008 | Accessibility Issues | Medium | Low | Yes |
| GEN-AI-009 | Patient Misunderstanding | Medium | Low-Medium | Yes (with ongoing monitoring) |

---

## Conditions for Proceeding

The patient service assistant can proceed to detailed design and pre-deployment testing on condition that:

1. **Security testing completed:** Prompt-injection and security assessment completed; zero critical findings.
2. **Data protection approved:** DPIA completed; DPA with vendor signed (if applicable); model-training prohibition confirmed.
3. **Escalation procedure formalised:** Human-escalation procedure documented; roles assigned; staff trained; SLA defined and tested.
4. **Monitoring plan approved:** Dashboard designed; metrics defined; responsibility assigned; incident escalation pathway established.
5. **Board approval:** Board approves residual risk, governance arrangements, and accountability for outcomes.

---

## Next Steps

| Activity | Owner | Due |
|---|---|---|
| Prompt-injection security test | Information Security Lead | 2026-10-31 |
| DPIA completion | Chief Data Protection Officer | 2026-10-31 |
| Vendor DPA negotiation | Chief Data Protection Officer + Procurement | 2026-10-31 |
| Formalise escalation procedure | PALS Manager + Chief Medical Officer | 2026-10-31 |
| Design monitoring dashboard | Clinical Safety Officer + Data Analytics | 2026-10-31 |
| AI Governance Committee review | AI Governance Lead | 2026-11-30 |
| Board approval (if High-risk) | CEO + Chief Medical Officer | 2026-12-15 |

---

## Document Control

| Item | Value |
|---|---|
| Document ID | AI-003-RISK-ASSESSMENT-20260911 |
| Version | 1.0 (Draft) |
| Classification | Internal Governance |
| Owner | AI Governance Lead |
| Last Updated | 2026-09-11 |
| Next Review | 2026-12-11 or upon material change |
