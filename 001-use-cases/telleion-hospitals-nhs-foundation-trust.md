# AI Governance Portfolio - Case Scenarios

## 1. Portfolio Organisation

### Telleion Hospitals NHS Foundation Trust

**Status:** Fictional NHS-style organisation used solely for portfolio and learning purposes.

**Evidence boundary:** The details below are scenario facts provided for this portfolio. They are not evidence of a real organisation, system, approval, control, incident, or regulatory decision.

| Attribute | Scenario detail |
|---|---|
| Organisation | Telleion Hospitals NHS Foundation Trust |
| Employees | Approximately 1,500 |
| Patients | Approximately 50,000 annually |
| Environment | Electronic Patient Record (EPR), Laboratory Information System (LIS), Radiology Information System (RIS), PACS, Microsoft 365, Azure, Data Warehouse, Power BI, and third-party SaaS platforms |

The Trust has established a formal **AI Governance Programme** because different departments have begun proposing AI solutions.

## Board Assurance Objective

The Board wants assurance that:

> AI is adopted safely, lawfully, ethically, and effectively while delivering measurable benefits to patients, staff, and the organisation.

## Scenario 1 - AI Clinical Documentation Assistant

**Risk level:** High

### Business Problem

Clinicians spend significant time documenting consultations, reducing the amount of time available for direct patient care.

### Proposed Solution

The Trust is considering an AI-powered clinical documentation assistant. The system listens to a consultation and produces a draft clinical note for clinician review before the note is entered into the Electronic Patient Record (EPR).

**Scenario status:** Proposed. This scenario does not constitute approval for deployment.

### Processing Flow

```text
Clinician and patient
	|
	v
Conversation
	|
	v
Speech-to-text
	|
	v
AI / LLM
	|
	v
Draft clinical note
	|
	v
Clinician review
	|
	v
EPR
```

### Data Involved

Potentially processed data includes:

- Patient name
- NHS number
- Symptoms
- Diagnosis
- Medications
- Clinical history
- Clinician observations
- Treatment plans

The exact data flow, processing purposes, retention, locations, access, deletion, and training use remain governance questions to evidence.

### Third Party

The AI model is supplied by an external technology provider. The provider boundary, subprocessors, model hosting, support access, data use, service changes, incident obligations, and exit arrangements require assessment before approval.

### Governance Questions

The AI Governance team must determine:

1. What personal data is processed?
2. Where is the data processed?
3. Is the vendor permitted to retain the information?
4. Is the data used for model training?
5. What happens when the AI hallucinates?
6. How accurate is the transcription?
7. Can clinicians override the output?
8. How is clinician approval recorded?
9. What happens if the AI system becomes unavailable?
10. How are incidents reported?
11. What happens when the vendor changes the underlying model?

### Initial Governance Scope

Assess this use case through the portfolio workflows for:

- High-impact clinical, patient-safety, privacy, security, fairness, accuracy, reliability, human-factors, and third-party risks
- Speech-to-text accuracy, clinical-note hallucination, omission, alteration, and unsafe suggestion risks
- Human oversight, clinician review, override, approval evidence, accountability, and routes to correction
- Data processing, retention, model training, data location, subprocessors, confidentiality, and UK GDPR considerations
- Vendor security, identity, access control, encryption, incident management, availability, resilience, audit rights, model changes, and exit strategy
- Pre-deployment testing, monitoring, incident response, change control, rollback, suspension, and decommissioning

The decision requested is whether the use case can proceed to the next governance gate, and under what evidence, controls, assurance conditions, and risk-tolerance decision.

## Governance Application

Use this scenario with the portfolio skills to assess proposed AI systems across the full lifecycle:

- [AI risk assessment](../.github/skills/ai-risk-assessment/SKILL.md)
- [AI control matrix](../.github/skills/ai-control-matrix/SKILL.md)
- [AI vendor assessment](../.github/skills/ai-vendor-assessment/SKILL.md)
- [AI assurance](../.github/skills/ai-assurance/SKILL.md)
- [AI incident](../.github/skills/ai-incident/SKILL.md)
- [AI governance review](../.github/skills/ai-governance-review/SKILL.md)
- [AI document review](../.github/skills/ai-document-review/SKILL.md)

## Scenario Assumptions

- The organisation, workforce, patient volume, systems, and programme are fictional scenario inputs.
- No AI use case is approved by this scenario alone.
- System, data, vendor, legal, clinical-safety, privacy, security, equality, accessibility, and operational facts must be established for each proposed use case.
- Any Board recommendation must identify its owner, rationale, evidence, date, review date, and status.
