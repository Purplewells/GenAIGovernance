---
title: Telleion Hospitals NHS Foundation Trust - AI Classification Standard
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: AI Governance Committee, with Trust Board escalation where required
review_date: 2026-12-11
scope: All AI systems proposed, acquired, developed, used, changed, monitored, or retired by the Trust
---

# AI Classification Standard

## 1. Purpose

This standard defines how the Trust classifies AI use cases so that governance, assurance, approval, monitoring, and evidence are proportionate to risk.

Classification is an initial governance decision, not a statement that a system is safe, lawful, compliant, or approved. A classification must be revisited when purpose, data, model, vendor, users, autonomy, geography, thresholds, integration, or operating context changes.

## 2. Classification Principles

- Classify the use case, not only the underlying model or product.
- Consider the actual context, affected people, decisions, data, autonomy, and foreseeable misuse.
- Use the highest applicable tier where risk dimensions differ.
- Escalate where uncertainty, missing evidence, vulnerable groups, irreversible harm, or public-interest impact increases the risk.
- Classification does not reduce legal, professional, clinical, privacy, security, or contractual duties.
- The system owner must document the rationale and evidence for the classification.

## 3. Assessment Dimensions

Assess each use case against:

- **Impact:** potential severity of harm to patients, staff, applicants, service users, communities, the organisation, or the public.
- **Decision significance:** whether the system informs or determines care, safety, access, employment, safeguarding, rights, benefits, or other material outcomes.
- **Autonomy:** degree to which outputs act without meaningful human review or can trigger action automatically.
- **Data sensitivity:** health, special-category, personal, confidential, financial, security-sensitive, or otherwise restricted data.
- **Scale and reach:** number of people, services, sites, decisions, and duration affected.
- **Vulnerability:** whether affected people may be children, patients, disabled people, applicants, people in crisis, or otherwise unable to avoid or challenge the system.
- **Uncertainty:** quality and completeness of evidence about data, model, performance, harms, controls, vendor, and operating environment.
- **Reversibility:** ability to detect, correct, undo, or provide redress for an adverse outcome.
- **Dependency:** criticality, concentration, lock-in, vendor dependence, availability, and exit capability.
- **Change potential:** likelihood that model, data, provider, users, or context will change materially.

## 4. Proposed Classification Tiers

### Tier 1 - Low impact

AI supports low-impact internal or administrative activity and does not make or materially influence decisions about individuals. It uses non-sensitive, synthetic, anonymised, or low-risk data in an approved environment.

**Examples:** drafting generic internal text, summarising non-confidential material, or low-impact analysis with human checking.

**Minimum governance:**

- Register the use case and assign an owner.
- Confirm approved purpose, data boundary, acceptable use, and prohibited use.
- Complete proportionate privacy and security checks.
- Provide user guidance and basic human review.
- Record decision, evidence, review date, and status.
- Monitor for scope expansion or unintended sensitive-data use.

**Approval:** Executive sponsor and system owner, subject to AI Governance Committee sampling or escalation criteria.

### Tier 2 - Moderate impact

AI supports operational, analytical, service, or workforce activity and may process personal or confidential data, influence decisions, or affect service experience, but a trained human remains able to review and correct outcomes before material harm occurs.

**Examples:** patient-service information support with escalation, workforce analytics, operational forecasting, or administrative recommendations.

**Minimum governance:**

- All Tier 1 requirements.
- Proportionate risk and impact assessment.
- Data map, retention, access, transparency, and privacy assessment.
- Security and resilience review.
- Defined human review, override, complaint, and escalation procedures.
- Performance and outcome measures with monitoring thresholds.
- Vendor and contract assessment where applicable.
- Assurance plan for material controls and a documented fallback.

**Approval:** AI Governance Committee or authorised delegate, with specialist review as required.

### Tier 3 - High impact

AI materially influences clinical, patient-safety, employment, recruitment, access-to-service, safeguarding, rights-affecting, or other high-impact decisions, or processes sensitive data at meaningful scale. Failure may cause significant harm, discrimination, loss of rights, or serious operational impact.

**Examples:** clinical documentation assistants, patient deterioration prediction, recruitment screening, clinical decision support, or systems using health data to influence care.

**Minimum governance:**

- All Tier 2 requirements.
- Enhanced risk, impact, clinical or domain-safety, privacy, equality, and security assessment.
- Local validation and testing across relevant groups and operating conditions.
- Independent assurance proportionate to the risk.
- Meaningful human oversight with trained users, recorded decisions, and override capability.
- Pre-deployment assurance and formal pilot or deployment gate.
- Monitoring of performance, harms, fairness, incidents, complaints, benefits, and drift.
- Tested fallback, rollback, incident response, change control, and exit arrangements.
- Formal residual-risk decision by the authorised risk owner and committee review.

**Approval:** AI Governance Committee recommendation and authorised executive or Trust Board approval according to [009-delegated-authorities.md](009-delegated-authorities.md). Trust Board escalation is required for material risks outside delegated tolerance or with significant patient, rights, or public-interest implications.

### Tier 4 - Critical or prohibited

AI may create or contribute to severe, widespread, irreversible, or difficult-to-remedy harm; operate with unacceptable autonomy; affect fundamental rights without adequate safeguards; or cannot be sufficiently understood, controlled, monitored, or exited.

**Examples:** uncontrolled autonomous action affecting patient safety, unlawful or discriminatory use, material processing without lawful basis, concealed high-impact decisions, or systems with no viable human oversight or safe fallback.

**Decision:** Do not proceed, or pause, restrict, or retire if already operating. Any proposed exception requires explicit Trust Board consideration, specialist advice, compelling evidence, and documented authority; some uses may be prohibited and not eligible for exception.

## 5. Classification Overrides

Regardless of initial score, classify at least as Tier 3 where the use case:

- Influences diagnosis, treatment, triage, deterioration response, safeguarding, or patient safety.
- Influences recruitment, employment, access to services, eligibility, rights, or material opportunities.
- Uses health or special-category data in a way that creates material privacy or rights risk.
- Makes or triggers decisions without meaningful human review.
- Affects vulnerable groups or may create irreversible or difficult-to-remedy harm.
- Has material unresolved bias, fairness, security, safety, vendor, or explainability concerns.
- Has insufficient evidence to establish a lower classification defensibly.

A use case must be escalated to Tier 4 consideration where serious harm is plausible, lawful authority is absent or unclear, required controls cannot operate, or the system cannot be safely paused or exited.

## 6. Classification Record

The classification record must include:

- AI system, use case, version, owner, sponsor, and lifecycle stage
- Intended purpose, users, affected people, benefits, impacts, harms, and alternatives
- Data types, locations, retention, vendors, subprocessors, integrations, and dependencies
- Assessment of each dimension in Section 3 and the classification rationale
- Inherent risk, controls, residual risk, uncertainty, and risk tolerance
- Required reviews, approval authority, assurance, monitoring, incident, change, and exit requirements
- Classification decision, conditions, evidence, date, review date, and status

## 7. Review Triggers

Reclassify when there is:

- A material model, data, vendor, subprocessor, user, purpose, threshold, autonomy, or integration change.
- A new population, geography, service, decision, or vulnerable group.
- A significant incident, complaint, appeal, near miss, drift, control failure, or adverse outcome.
- New evidence that changes performance, harms, benefits, legal applicability, or risk tolerance.
- Expansion from pilot, internal use, or decision support into operational or external use.
- A change in law, regulatory guidance, policy, contract, or professional requirements.

## 8. Governance Decision

The Head of AI Governance performs the initial classification and maintains the register. The AI Governance Committee approves all Tier 3, Tier 4, disputed, overridden, and materially changed classifications. If there is disagreement, the higher classification applies until resolved. Classification authority is subject to [009-delegated-authorities.md](009-delegated-authorities.md).

This standard is Draft for consultation and must be approved before it is used as formal delegated authority.
