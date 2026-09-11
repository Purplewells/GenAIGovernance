---
title: Telleion Hospitals NHS Foundation Trust - AI Approval Process
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: Trust Board and AI Governance Committee within delegated authority
review_date: 2026-12-11
scope: All AI systems proposed, acquired, developed, used, changed, monitored, or retired by the Trust
---

# AI Approval Process

## 1. Purpose

This process defines how Telleion Hospitals NHS Foundation Trust decides whether an AI use case may be registered, designed, piloted, deployed, changed, continued, restricted, paused, or retired.

Approval is a governance decision, not a technical sign-off. It must be based on evidence proportionate to the classification and must preserve the Trust's ability to challenge, restrict, pause, replace, or retire the system.

## 2. Approval Principles

- No AI system may be used on Trust data without registration and an assigned owner.
- Approval applies only to the stated purpose, data, users, configuration, geography, autonomy, version, and lifecycle stage.
- Approval is conditional on residual risk being within authorised tolerance.
- A policy, certificate, vendor assertion, questionnaire, or framework mapping is not sufficient evidence of effective control.
- Open critical findings, missing evidence, or unresolved contradictions must prevent approval or make it explicitly conditional.
- Material changes require reassessment before release or continued operation.
- The approval record must include owner, rationale, evidence, date, review date, status, conditions, and authority.

## 3. Approval Outcomes

| Outcome | Meaning |
|---|---|
| Register only | Proposal is recorded but may not process operational or personal data |
| Proceed to design | The use case may be designed or procured within stated boundaries; no operational deployment |
| Proceed to controlled pilot | Limited, time-bound testing is approved with defined population, controls, monitoring, and stop criteria |
| Approve deployment | Operational use is approved within the recorded scope and conditions |
| Approve with conditions | Use is restricted until specified, owned, measurable conditions are met |
| Defer | Decision cannot be made because evidence, review, or clarification is insufficient |
| Restrict | Existing or proposed use is limited by data, users, decisions, autonomy, geography, volume, or duration |
| Pause | Use must stop pending incident response, remediation, investigation, or reassessment |
| Reject | Use may not proceed because risk, purpose, evidence, or controls are unacceptable |
| Retire | Use ends and transition, data, access, records, contracts, and residual risk are closed |

## 4. Approval Stages

### Stage 1 - Registration and triage

**Owner:** Executive Sponsor and Head of AI Governance.

Record:

- Business problem, intended benefit, alternatives, and proposed purpose
- System, model, provider, users, affected people, data, environment, and lifecycle stage
- Initial harms, dependencies, autonomy, scale, and likely classification
- Executive sponsor, system owner, risk owner, and required specialist reviewers

**Gate:** Register the proposal, reject it as unsuitable, or request further information. Registration is not approval.

### Stage 2 - Classification and scope confirmation

**Owner:** Head of AI Governance; AI Governance Committee approval is required for Tier 3, Tier 4, disputed, overridden, or materially changed classifications. Authority follows [009-delegated-authorities.md](009-delegated-authorities.md).

Complete the AI Classification Standard and confirm:

- Tier and rationale
- Scope, exclusions, prohibited use, and intended users
- Data and system boundary
- Required privacy, security, clinical or domain, legal, equality, vendor, assurance, and procurement reviews
- Approval authority, risk tolerance, monitoring, incident, change, and exit requirements
- Applicable delegated authority and reserved-matter route

**Gate:** Authorise design work at the appropriate tier or stop the proposal.

### Stage 3 - Risk and impact assessment

**Owner:** System Owner and Risk Owner.

Complete proportionate assessments using [010-risk-assessment-methodology.md](010-risk-assessment-methodology.md) and covering:

- Benefits, stakeholders, impacts, harms, vulnerable groups, and recourse
- Inherent risk, controls, residual risk, uncertainty, and tolerance
- Privacy, security, clinical or domain safety, fairness, accessibility, human factors, operational, legal, and third-party risks
- Intended use, foreseeable misuse, out-of-scope use, and failure modes
- Human oversight, fallback, monitoring, incidents, changes, and decommissioning

The Risk Owner validates the rating and the Head of AI Governance confirms methodological completeness. Tier 3, Tier 4, disputed, and outside-tolerance assessments require AI Governance Committee review and escalation under the Delegated Authorities Schedule.

**Gate:** Proceed to design or acquisition, restrict, defer, reject, or escalate.

### Stage 4 - Design, acquisition, and control readiness

**Owner:** System Owner, Executive Sponsor, Procurement and Legal.

Before pilot or deployment, establish:

- System architecture, data flows, data minimisation, retention, access, and deletion
- Security, resilience, identity, encryption, logging, and incident controls
- Model, data, performance, fairness, safety, explainability, and human-oversight controls
- Vendor assessment, DPA, confidentiality, training-use, subprocessor, audit, change, liability, and exit terms where applicable
- DPIA status and completion evidence in accordance with [011-dpia-completion-criteria.md](011-dpia-completion-criteria.md), where personal or special-category data is processed
- Operating procedures, training, user communications, complaints, appeals, and recourse
- Monitoring measures, thresholds, owners, alert routes, and stop criteria
- Assurance plan with test methods, evidence, pass criteria, samples, independence, and limitations
- Monitoring plan conforming to [013-monitoring-and-alert-standard.md](013-monitoring-and-alert-standard.md)
- Control-effectiveness evidence conforming to [012-assurance-control-effectiveness-standard.md](012-assurance-control-effectiveness-standard.md)

**Gate:** Confirm control design adequacy and readiness for testing. No live operational use.

### Stage 5 - Testing and assurance

**Owner:** System Owner; independent reviewer proportionate to risk.

Test relevant characteristics and controls, including:

- Validity, reliability, accuracy, calibration, uncertainty, and limitations
- Safety, clinical or domain performance, fairness, bias, accessibility, and explainability
- Privacy, security, resilience, availability, fallback, and recovery
- Human oversight, override, decision recording, training, workload, and automation bias
- Vendor performance, model changes, data use, incident support, and exit capability

Record evidence, samples, pass criteria, results, limitations, findings, remediation, and retest. Apply [012-assurance-control-effectiveness-standard.md](012-assurance-control-effectiveness-standard.md); a control cannot be marked Effective without current design, implementation, operating-effectiveness, and proportionate independent-review evidence.

**Gate:** Approve controlled pilot, require remediation, restrict, defer, reject, or escalate.

### Stage 6 - Pilot approval

**Owner:** AI Governance Committee; Trust Board escalation where required.

A pilot submission must state:

- Population, duration, sites, users, data, version, purpose, and exclusions
- Pilot objectives, benefit measures, safety and harm indicators, and success criteria
- Human oversight, support, incident, complaints, appeals, and fallback procedures
- Monitoring cadence, thresholds, stop criteria, and escalation route
- Open findings, conditions, residual risk, risk acceptance, and review date
- Delegated authority and evidence that the risk appetite and methodology are approved or explicitly marked as consultation criteria
- Independent reviewer and final production decision authority

**Gate:** Approve pilot with conditions, defer, restrict, reject, or require Trust Board approval.

### Stage 7 - Production deployment approval

**Owner:** AI Governance Committee recommendation; authorised executive or Trust Board according to authority and risk.

The deployment pack must demonstrate:

- Pilot or validation results meet approved criteria
- Critical and high findings are closed or formally accepted within authority
- DPIA, security, clinical or domain safety, legal, equality, vendor, and assurance reviews are complete where required
- DPIA is Approved or has documented Conditions Outstanding that are permitted by delegated authority and the approval conditions
- Users are trained and human oversight operates in practice
- Monitoring, incident response, fallback, rollback, and exit are operational
- Benefits and harms are understood and residual risk is within tolerance
- The deployment scope, version, conditions, owners, review date, and status are recorded

**Gate:** Approve deployment, approve with conditions, restrict, defer, reject, or escalate.

### Stage 8 - Operational review and continuation

**Owner:** System Owner and Risk Owner; oversight by the AI Governance Committee.

Review:

- Performance, drift, safety, privacy, security, fairness, reliability, availability, and human factors
- Benefits, unintended impacts, complaints, appeals, incidents, near misses, and harmful outputs
- Control effectiveness, assurance findings, overdue actions, and exceptions
- Vendor, model, subprocessor, service, regulatory, and operational changes
- Whether residual risk remains within tolerance

**Gate:** Continue, renew conditions, restrict, require change assessment, pause, or retire.

### Stage 9 - Material change approval

A new approval is required before material changes to model, data, vendor, subprocessor, purpose, users, geography, autonomy, threshold, integration, or operating environment.

The change submission must include impact analysis, updated classification, risk and privacy assessment, testing, vendor evidence, monitoring changes, rollback, communication, and approval authority.

### Stage 10 - Pause, incident, and retirement decisions

The Trust must pause, restrict, or retire an AI system where serious harm, unlawful processing, discrimination, material security exposure, unsafe operation, failed controls, unacceptable drift, or risk outside tolerance is identified.

Restart requires documented containment, remediation, testing, updated risk assessment, monitoring, specialist advice, and authorised approval under [014-ai-incident-management-procedure.md](014-ai-incident-management-procedure.md).

Retirement requires evidence of transition, access removal, data disposition, records retention, contract closure, open decisions and incidents, downstream communication, and residual-risk closure.

## 5. Required Approval Pack

Every material approval pack must include:

- Decision requested and proposed outcome
- Scope, exclusions, audience, date, lifecycle stage, jurisdiction, and assumptions
- Use-case record, classification, business case, benefits, alternatives, and affected stakeholders
- Risk and impact assessments with inherent risk, controls, residual risk, tolerance, and uncertainty
- Privacy, security, safety, equality, accessibility, legal, vendor, and operational reviews as relevant
- Control matrix and operating procedures
- Assurance plan, test results, findings, remediation, and independent review
- Human-oversight, training, transparency, complaint, appeal, and recourse arrangements
- Monitoring, incident, change, fallback, rollback, and exit plans
- Named owners, approval authority, conditions, evidence, date, review date, and status

## 6. Decision Record and Conditions

The decision record must identify:

- Decision ID and AI system or use case
- Outcome and approved scope
- Owner, rationale, evidence, date, review date, and status
- Risk owner and residual-risk acceptance
- Conditions, control owners, due dates, measures, and verification method
- Open findings, limitations, assumptions, and specialist advice
- Escalation route and triggers for reassessment, restriction, pause, or retirement

Conditions must be specific, measurable, time-bound, owned, and linked to consequences if not met. Conditions cannot silently convert an unapproved use into an approved one.

## 7. Governance Records and Review

The Head of AI Governance maintains the approval register and ensures decisions are traceable to the AI inventory, risk register, controls, assurance, incidents, vendors, delegated authorities, and lifecycle records.

The AI Governance Committee reviews this process at least annually and after material changes to risk appetite, delegation, law, standards, operating model, or the AI portfolio.

**Status:** Draft for consultation. Formal delegated authorities must be confirmed by the Trust Board and recorded before this process is used as binding approval authority.
