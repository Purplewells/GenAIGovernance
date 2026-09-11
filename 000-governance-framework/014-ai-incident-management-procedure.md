---
title: Telleion Hospitals NHS Foundation Trust - AI Incident Management Procedure
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: AI Governance Committee and relevant incident authority
review_date: 2026-12-11
scope: AI incidents, near misses, harmful outputs, control failures, and material AI events
---

# AI Incident Management Procedure

## 1. Purpose

This procedure operationalises response to AI incidents and near misses. It works with the Trust's security, clinical, privacy, safeguarding, complaints, business-continuity, and major-incident procedures.

## 2. Incident Categories

Classify one or more: patient or clinical safety, harmful or inaccurate output, privacy or confidentiality, security, fairness or discrimination, availability or resilience, vendor or supply chain, legal or regulatory, human oversight, intellectual property, or control failure.

## 3. Severity

- **Critical:** actual or imminent serious harm, widespread exposure, material rights impact, major security or clinical event, or risk outside tolerance.
- **High:** significant harm or credible recurrence, material breach, systemic bias, or control failure requiring urgent containment.
- **Moderate:** contained impact, near miss, material degradation, or repeated control failure.
- **Low:** limited impact or isolated issue managed within normal operation.

Severity must be reassessed as evidence develops.

## 4. Response Steps

1. **Detect and report:** create an incident record with ID, time, reporter, system, version, description, evidence, and status.
2. **Triage and escalate:** assign severity, Incident Manager, System Owner, Risk Owner, and required privacy, security, clinical, legal, vendor, or communications specialists.
3. **Contain:** stop unsafe actions, restrict users or data, disable integrations, add human review, roll back, switch to fallback, or pause the system.
4. **Preserve evidence:** protect prompts, inputs, outputs, versions, configurations, logs, access records, data lineage, communications, and decisions with integrity, retention, access control, and legal-hold consideration.
5. **Assess impact:** identify affected people, vulnerable groups, data, systems, harms, benefits lost, dependencies, and recourse.
6. **Assess notification:** qualified privacy, legal, security, clinical, and regulatory specialists determine notification duties and communications.
7. **Investigate:** identify direct, contributing, and systemic causes across model, data, code, vendor, process, policy, human factors, and controls.
8. **Remediate and test:** define actions, owners, dates, success measures, compensating controls, retest, and independent review.
9. **Recover or retire:** restart only after authorised evidence confirms containment, remediation, monitoring, residual risk, and support for affected people. Retire where safe operation cannot be demonstrated.
10. **Close and learn:** record closure authority, lessons, updates to risks, controls, assurance, vendor oversight, monitoring, training, and lifecycle decisions.

## 5. Authority and Escalation

- System Owner coordinates initial operational response.
- Head of AI Governance coordinates governance escalation and records.
- DPO leads privacy advice and notification assessment for personal-data events.
- Security Lead leads security response for security events.
- Clinical or Domain Safety Lead leads specialist safety advice where relevant.
- Risk Owner decides treatment or escalates acceptance.
- AI Governance Committee reviews material incidents, restart, restriction, and lessons.
- Trust Board is informed or approves reserved matters according to the Delegated Authorities Schedule.

No system may restart after a Critical or High incident without documented approval by the authorised risk owner and AI Governance Committee, with Trust Board escalation where required.

## 6. Records and Closure

The incident record must retain timeline, evidence, severity, decisions, notifications, impact assessment, root cause, remediation, retest, residual risk, affected-person support, communications, owner, closure authority, date, review date, and status.

A closure decision must not erase unresolved risk. Open actions remain tracked in the risk register, assurance plan, control matrix, vendor record, or governance improvement plan.
