---
title: Telleion Hospitals NHS Foundation Trust - AI Governance Principles
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: Trust Board, on recommendation from the AI Governance Committee
review_date: 2026-12-11
scope: All AI systems proposed, acquired, developed, used, changed, monitored, or retired by the Trust
jurisdiction: United Kingdom
---

# Telleion Hospitals NHS Foundation Trust
# AI Governance Principles

## 1. Purpose

These principles describe how Telleion Hospitals NHS Foundation Trust expects AI to be governed and used. They apply the NIST AI Risk Management Framework 1.0 in a form that can guide Board decisions, procurement, system design, clinical and operational use, assurance, and retirement.

The principles sit below the **AI Governance Framework** and inform the mandatory **AI Governance Policy**. They are not a substitute for a risk assessment, DPIA, clinical-safety review, security assessment, assurance plan, contract, or approval decision.

**Decision requested:** The AI Governance Committee and Trust Board are asked to endorse these principles as the organisation's common standard for responsible AI decision-making.

**Status:** Draft for consultation. The principles do not approve any individual AI system.

## 2. Context and Evidence Boundary

Telleion Hospitals NHS Foundation Trust is a fictional NHS-style organisation used solely for portfolio and learning purposes. The organisation, systems, proposals, controls, approvals, test results, and regulatory outcomes described in this portfolio are scenario inputs, not evidence of a real organisation or compliance position.

These principles apply to AI used in clinical, patient-service, recruitment, operational, administrative, analytical, research, and support activities, including AI supplied by third parties or embedded in wider products.

## 3. Relationship to Frameworks and Law

NIST AI RMF 1.0 is the primary risk-management framework. The principles support its continuous functions:

- **GOVERN:** make accountability, authority, policy, resources, and risk tolerance explicit.
- **MAP:** understand purpose, context, stakeholders, benefits, impacts, harms, data, and dependencies.
- **MEASURE:** test trustworthy-AI characteristics, controls, evidence, performance, uncertainty, and outcomes.
- **MANAGE:** treat risk, assign owners, monitor operation, respond to incidents, and govern change or retirement.

Supporting sources are applied where relevant, including ISO/IEC 42001, ISO/IEC 27001, UK GDPR, Data Protection Act 2018, ICO guidance, OWASP GenAI Security guidance, NIST Cybersecurity Framework, Equality Act 2010, and relevant NHS, clinical-safety, accessibility, employment, or sector requirements.

The Trust must distinguish legal duties, contractual obligations, certifiable management-system requirements, voluntary frameworks, regulator guidance, and security best practices. No framework mapping by itself demonstrates compliance or control effectiveness.

## 4. The Principles

### Principle 1 - Public and patient benefit comes first

AI must have a clear, legitimate purpose and a demonstrable benefit for patients, staff, service users, or the organisation. The Trust must consider alternatives to AI and the consequences of not proceeding.

**Application:** Define intended benefits, affected stakeholders, measures of success, unintended effects, and whether benefits remain proportionate to risks and harms.

**Evidence:** Business case, benefits measures, stakeholder input, outcome data, and review decision.

### Principle 2 - Accountability is explicit

Every AI system must have an accountable executive sponsor, system owner, risk owner, operational owner, and appropriate specialist reviewers. Decision rights must identify who can approve, restrict, pause, restart, accept residual risk, or retire the system.

**Application:** Record named individuals, authority, rationale, evidence, date, review date, and status for every material decision.

**Evidence:** AI inventory, role assignment, approval record, decision log, committee minutes, and risk acceptance.

### Principle 3 - Risk is proportionate and actively managed

The Trust must assess AI according to its potential impact, harm, uncertainty, autonomy, affected people, and reversibility. High-impact clinical, patient-safety, employment, safeguarding, access-to-service, and rights-affecting uses require enhanced review.

**Application:** Distinguish inherent risk, controls, and residual risk. Compare residual risk with documented tolerance and ensure acceptance is authorised.

**Evidence:** Risk assessment, risk register, control matrix, treatment plan, tolerance decision, and review date.

### Principle 4 - People remain at the centre

AI must support, not obscure, professional and organisational accountability. Human oversight must be meaningful: reviewers need appropriate competence, time, information, authority, and ability to challenge or change an outcome.

**Application:** Define human decisions, review points, override rights, prohibited automation, training, workload, escalation, complaints, appeals, and routes to recourse.

**Evidence:** Operating procedure, training records, override logs, approval records, complaint records, and assurance tests of human intervention.

### Principle 5 - Privacy and confidentiality are designed in

The Trust must process personal, health, confidential, and special-category data only for a clear, necessary, proportionate, and lawful purpose. Privacy and confidentiality must be considered before data is collected or shared.

**Application:** Address lawful basis, transparency, data minimisation, accuracy, retention, deletion, transfers, processors, subprocessors, training use, access, DPIA requirements, and individual rights.

**Evidence:** Data map, DPIA, privacy notice, data-processing agreement, retention schedule, access records, deletion evidence, and DPO advice.

### Principle 6 - Security and resilience are non-negotiable

AI systems must be protected against unauthorised access, manipulation, disclosure, loss, misuse, and disruption. They must fail safely and have proportionate continuity and recovery arrangements.

**Application:** Assess identity, access, encryption, secrets, logging, vulnerability management, model and data integrity, supply chain, availability, recovery, fallback, and incident response. Address prompt injection, data leakage, insecure output handling, and excessive agency where relevant.

**Evidence:** Security assessment, architecture, test results, access reviews, logs, recovery exercise, supplier evidence, incident records, and remediation.

### Principle 7 - AI must be fair and must not create avoidable harm

The Trust must identify and manage bias, discrimination, unequal performance, unsafe outputs, exclusion, and disproportionate impacts on vulnerable groups. Fairness must be assessed in the actual context of use, not assumed from generic vendor or model claims.

**Application:** Test relevant groups and use cases, assess proxy variables, monitor outcomes, provide recourse, investigate complaints, and pause or adjust systems when harm is detected.

**Evidence:** Fairness methodology, subgroup results, impact analysis, monitoring metrics, complaint trends, corrective actions, and independent review.

### Principle 8 - AI must be transparent and explainable enough for its context

People must understand when AI is used, what it is intended to do, its limitations, who is accountable, and how to challenge or correct an outcome. Explanations must be appropriate for patients, staff, applicants, professionals, and other affected people.

**Application:** Provide proportionate notices, explain relevant outputs and limitations, document material model and data changes, and ensure reviewers can challenge results.

**Evidence:** Privacy and user notices, system documentation, model or system card, sample explanations, user testing, appeal records, and change logs.

### Principle 9 - Evidence matters more than assertion

The Trust must not claim that AI is safe, compliant, fair, accurate, secure, effective, or approved without appropriate evidence. Vendor claims, certificates, policies, questionnaires, and framework mappings are inputs to assessment, not conclusions.

**Application:** Label material statements as **Evidence**, **Assumption**, **Recommendation**, or **Unknown**. Record evidence scope, date, confidence, limitations, owner, and what would change the conclusion.

**Evidence:** Test results, operating records, assurance reports, decision records, monitoring data, incident evidence, and independent challenge.

### Principle 10 - Governance must operate throughout the lifecycle

AI governance begins at the idea stage and continues through use-case assessment, risk and impact assessment, design, development or acquisition, testing, approval, deployment, monitoring, review, incident management, and decommissioning.

**Application:** Use stage gates and reassess when the system, data, model, vendor, users, purpose, thresholds, or operating environment materially changes.

**Evidence:** Lifecycle record, gate decisions, change assessments, release approvals, monitoring reports, incident records, and retirement evidence.

### Principle 11 - Third-party accountability remains with the Trust

The Trust must govern suppliers, model providers, cloud platforms, subprocessors, fourth parties, data suppliers, integrators, open-source components, and downstream dependencies as part of the risk boundary.

**Application:** Assess data processing, retention, model training, location, security, identity, access, incident management, availability, resilience, confidentiality, intellectual property, audit rights, regulatory duties, model changes, liability, and exit strategy.

**Evidence:** Vendor assessment, contract, DPA, subprocessor list, independent assurance, service records, change notices, incident cooperation, and exit test.

### Principle 12 - Governance learns and responds

AI governance must respond to evidence, incidents, complaints, near misses, audit findings, changes, and emerging harms. A system must be capable of restriction, pause, rollback, replacement, or retirement when its risks exceed tolerance or its benefits no longer justify its harms.

**Application:** Define monitoring, alert thresholds, incident routes, remediation, independent review, restart criteria, exception expiry, and decommissioning arrangements.

**Evidence:** Assurance plan, monitoring dashboard, incident and corrective-action records, retest results, management review, pause or restart decisions, and retirement records.

## 5. Decision Test

Before approving a material AI decision, the decision-maker should be able to answer:

1. What outcome or benefit is the Trust pursuing?
2. Who may be affected, and what harms or inequalities could result?
3. What is the intended use, boundary, lifecycle stage, and alternative?
4. What are the inherent risks, controls, and residual risks?
5. What evidence supports the claims, and what remains unknown?
6. Who is accountable, who can challenge the outcome, and who can stop the system?
7. What privacy, security, clinical-safety, equality, accessibility, legal, vendor, and operational reviews are required?
8. How will the Trust know whether the system remains safe, effective, fair, and beneficial?
9. What happens after an incident, material change, loss of service, or unacceptable outcome?
10. What decision is authorised, on what date, until when, and subject to which conditions?

If these questions cannot be answered sufficiently for the risk, the decision must be conditional, deferred, restricted, or rejected.

## 6. Accountability and Review

The Head of AI Governance owns implementation of these principles and reports material exceptions, risks outside tolerance, incidents, overdue actions, and emerging issues to the AI Governance Committee.

The AI Governance Committee will review the principles at least annually and after material changes to law, standards, Trust strategy, risk appetite, operating model, or the AI portfolio. Specialist review must be obtained where the subject matter requires legal, privacy, security, safety, clinical, equality, accessibility, audit, regulatory, or domain expertise.

| Decision field | Value |
|---|---|
| Owner | Head of AI Governance |
| Rationale | Establish a common, human-centred, evidence-based standard for AI decisions |
| Evidence | AI Governance Framework and AI Governance Policy; implementation evidence to be developed |
| Date | 2026-09-11 |
| Review date | 2026-12-11 |
| Status | Draft for consultation |
