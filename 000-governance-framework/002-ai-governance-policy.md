---
title: Telleion Hospitals NHS Foundation Trust - AI Governance Policy
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
# AI Governance Policy

## 1. Policy Statement

Telleion Hospitals NHS Foundation Trust will adopt and use artificial intelligence only where it can demonstrate that the use is safe, lawful, ethical, secure, proportionate, accountable, and capable of delivering measurable benefits to patients, staff, and the organisation.

AI must not be introduced because it is available or because a supplier claims that it is accurate, compliant, certified, or safe. The Trust must establish evidence, assign accountability, control residual risk, and maintain the ability to restrict, pause, replace, or retire an AI system.

This policy is mandatory for all Trust departments, employees, contractors, temporary staff, volunteers, suppliers, and partners using or supporting Trust AI systems.

**Policy status:** Draft for consultation. This policy does not approve any specific AI system.

## 2. Purpose and Objectives

This policy establishes mandatory requirements to:

- Align AI governance to NIST AI Risk Management Framework 1.0.
- Protect patients, staff, applicants, service users, and other affected people.
- Ensure AI use is lawful, ethical, transparent, secure, and human-centred.
- Prevent uncontrolled or undocumented AI adoption.
- Ensure risks, benefits, impacts, harms, controls, evidence, and decisions are traceable.
- Demonstrate that governance operates in practice, not only on paper.
- Support proportionate assurance, monitoring, incident response, and continual improvement.

## 3. Framework and Authority

NIST AI Risk Management Framework 1.0 is the Trust's primary AI risk-management framework:

- **GOVERN:** accountability, policy, risk tolerance, oversight, resources, and escalation.
- **MAP:** purpose, context, stakeholders, benefits, impacts, harms, dependencies, data, and lifecycle boundaries.
- **MEASURE:** trustworthy-AI characteristics, risks, controls, evidence, performance, uncertainty, and outcomes.
- **MANAGE:** treatment, ownership, residual risk, monitoring, incidents, change, restriction, suspension, and retirement.

Supporting sources must be applied where relevant and identified by edition, version, date, and source:

- ISO/IEC 42001
- ISO/IEC 27001
- UK GDPR
- Data Protection Act 2018
- ICO AI and data-protection guidance
- OWASP GenAI Security guidance
- NIST Cybersecurity Framework
- Equality Act 2010 and relevant clinical-safety, accessibility, employment, NHS, or sector requirements

This policy does not provide legal advice, certify compliance, or replace specialist review.

## 4. Policy Principles

All Trust AI activity must be:

- Risk-based
- Proportionate
- Evidence-based
- Auditable
- Transparent
- Accountable
- Human-centred

The Trust must consider benefits as well as risks, including patient outcomes, staff experience, access, equality, vulnerable groups, environmental effects, and routes to recourse.

## 5. Scope and Definitions

### 5.1 In scope

This policy applies to AI that is:

- Developed internally or acquired from a supplier
- Embedded in clinical, operational, administrative, analytical, recruitment, patient-service, or research workflows
- Used through software, APIs, cloud platforms, devices, models, agents, chatbots, decision-support tools, or automated processes
- Used for prediction, classification, recommendation, generation, transcription, optimisation, monitoring, or decision support
- Processing Trust, patient, staff, applicant, supplier, or other personal, confidential, or operational data

It applies across idea, design, development, acquisition, testing, approval, deployment, operation, monitoring, change, incident management, and decommissioning.

### 5.2 Key definitions

- **AI system:** A machine-based system that generates predictions, content, recommendations, or decisions influencing real or virtual environments.
- **AI use case:** A defined purpose, workflow, user group, data boundary, and operating context for an AI system.
- **System owner:** The person accountable for the approved system's safe operation and lifecycle.
- **Risk owner:** The person authorised to accept or treat residual risk.
- **Human oversight:** Meaningful human ability, competence, authority, time, and information to understand, challenge, override, or stop an AI-supported outcome.
- **Material change:** A change to model, data, vendor, purpose, users, geography, autonomy, integration, threshold, risk, or operating environment that could alter benefits, impacts, harms, or controls.

## 6. Mandatory Governance Requirements

### 6.1 Registration and approval

The Trust must maintain an authoritative AI inventory. No department may deploy or materially test an AI system on Trust data without registration and an assigned system owner, executive sponsor, and risk owner.

Every use case must have:

- Purpose, intended use, prohibited or out-of-scope use, and alternatives
- Intended users, affected people, vulnerable groups, benefits, impacts, harms, and recourse
- Data sources, processing purposes, locations, retention, access, and dependencies
- Lifecycle stage, risk tier, applicable obligations, and decision authority
- Risk assessment, controls, assurance, monitoring, incident, change, and exit arrangements

### 6.2 Risk and impact assessment

Before approval, the use-case owner must complete proportionate risk and impact assessments. Assessments must distinguish:

- **Inherent risk:** risk before controls
- **Controls:** preventive, detective, corrective, compensating, and human-oversight measures
- **Residual risk:** risk after controls, including uncertainty and comparison with tolerance

Risk ratings must use [010-risk-assessment-methodology.md](010-risk-assessment-methodology.md) and state their method, rationale, evidence, limitations, affected stakeholders, and authorised risk acceptor. Missing evidence must not be treated as low risk.

### 6.3 Prohibited or restricted activity

The Trust must not proceed where:

- The purpose is prohibited by law, policy, contract, or an authorised Trust decision.
- The system cannot be bounded sufficiently to understand material harms or accountability.
- Required evidence is unavailable and the risk cannot be controlled proportionately.
- The supplier will not provide minimum information, contractual protections, incident cooperation, or exit arrangements required for the risk.
- Human oversight is nominal, unavailable, unqualified, or unable to change the outcome.
- A material risk exceeds tolerance and no authorised decision permits restricted operation.

High-impact use cases, including clinical, patient-safety, employment, access-to-service, safeguarding, or rights-affecting use, require enhanced review and approval before pilot or deployment.

## 7. Roles and Responsibilities

| Role | Mandatory responsibility |
|---|---|
| Trust Board | Approve this policy, risk appetite, material risk acceptance, and high-impact decisions within its authority |
| AI Governance Committee | Review use cases, risk assessments, controls, assurance, exceptions, incidents, changes, and retirement recommendations |
| Head of AI Governance | Maintain the governance process, inventory, portfolio reporting, records, escalation, and policy implementation |
| Executive sponsor | Own the business case, resources, intended benefits, and operational sponsorship |
| System owner | Maintain the system boundary, approved use, controls, monitoring, documentation, changes, and safe operation |
| Risk owner | Accept, reduce, restrict, transfer, pause, or retire residual risk within delegated authority |
| Data Protection Officer | Advise on privacy, UK GDPR, DPIAs, data rights, transfers, retention, and data-processing arrangements |
| Security lead | Review security architecture, identity, access, encryption, resilience, vulnerabilities, incidents, and testing |
| Clinical or domain safety lead | Review domain harms, safe use, professional accountability, escalation, and clinical or specialist risks where relevant |
| Procurement and Legal | Review suppliers, contracts, liability, audit rights, data-processing terms, IP, regulatory obligations, and exit |
| Assurance or Internal Audit | Provide proportionate independent review and verify remediation where required |
| Managers and users | Ensure trained staff use approved systems, follow procedures, report concerns, and exercise human oversight |

Individuals, not only teams, must be named for material decisions and risk acceptance.

## 8. Lifecycle Requirements

AI use cases must pass the following controls:

1. **Idea:** Register the proposal, business problem, benefit, alternatives, and initial prohibited-use check.
2. **Use-case assessment:** Define purpose, context, users, affected people, data, dependencies, harms, and lifecycle boundary.
3. **Risk assessment:** Assess inherent risk, controls, residual risk, tolerance, and approval requirements.
4. **Impact assessment:** Assess privacy, equality, human rights, safety, accessibility, clinical, societal, and operational impacts where relevant.
5. **Design:** Define architecture, data governance, security, privacy, human oversight, monitoring, incident, and exit controls.
6. **Development or acquisition:** Apply secure development, procurement, vendor assessment, contractual controls, and evidence requirements.
7. **Testing:** Test validity, reliability, safety, security, privacy, fairness, explainability, usability, resilience, human factors, and failure modes.
8. **Governance approval:** Confirm evidence, open findings, residual risk, owners, assurance, monitoring, procedures, and authorised decision.
9. **Deployment:** Release only within the approved scope, configuration, users, data, geography, autonomy, and version.
10. **Monitoring:** Monitor performance, drift, harms, incidents, complaints, appeals, controls, benefits, vendors, and changes.
11. **Review:** Reassess periodically and after material changes, incidents, adverse outcomes, or regulatory developments.
12. **Incident management:** Detect, contain, investigate, communicate, remediate, test, and authorise restart, restriction, pause, or retirement.
13. **Decommissioning:** Manage transition, access removal, data disposition, records, contracts, dependencies, outstanding cases, and closure evidence.

## 9. Privacy and Data Protection

Before processing personal or special-category data, the use-case owner must establish:

- Purpose, necessity, proportionality, and lawful basis
- Data minimisation, accuracy, provenance, retention, deletion, and legal hold
- Transparency, privacy notices, rights, objection, rectification, erasure, and recourse
- Automated decision-making and profiling implications
- Data locations, international transfers, processors, subprocessors, and data-processing agreements
- DPIA requirements and DPO advice
- Restrictions on model training, product improvement, analytics, and secondary use
- Access, confidentiality, encryption, logging, incident response, and breach handling

A DPIA or privacy assessment marked Draft must not be described as complete in another artefact.
For AI processing of personal or special-category data, completion status and sign-off must meet [011-dpia-completion-criteria.md](011-dpia-completion-criteria.md).

## 10. Security, Resilience, and Third Parties

System owners must implement proportionate controls for:

- Identity, authentication, least privilege, privileged access, segregation of duties, and access reviews
- Secure configuration, tenant isolation, secrets, keys, encryption, network protection, and data integrity
- Model, data, software, open-source, cloud, supplier, and supply-chain risks
- Generative-AI threats such as prompt injection, data leakage, insecure output handling, excessive agency, and malicious tool use where applicable
- Vulnerability management, secure development, logging, detection, response, backup, recovery, failover, and degraded operation
- Vendor and subprocessor changes, audit rights, evidence access, incident obligations, liability, service levels, and exit

Supplier certifications, policies, questionnaires, and attestations are supporting evidence only. They do not prove that a control operates for the Trust's configured use.

## 11. Human Oversight, Transparency, and Recourse

Each AI system must define and communicate:

- Which decisions remain with authorised humans
- What information reviewers receive and how they challenge or override outputs
- Required competence, training, time, workload, independence, and escalation
- Prohibited automation and circumstances requiring human review
- How approvals, overrides, dissent, complaints, appeals, and corrections are recorded
- How affected people are informed about AI use and can request human review or recourse
- How automation bias, over-reliance, and ineffective oversight are detected

A human reviewer must have genuine authority and practical ability to change the outcome.

## 12. Assurance and Monitoring

Material AI systems must have an AI Assurance Plan. Assurance activities must define:

- Objective and linked risk, control, obligation, or decision
- Test method, population or sample, evidence, and pass criteria
- Performer, independent reviewer, competence, cadence, trigger, and limitations
- Result, finding, uncertainty, remediation, owner, due date, retest, and closure authority

Monitoring must cover relevant performance, safety, privacy, security, fairness, accessibility, reliability, human-oversight, operational, vendor, incident, complaint, appeal, and benefit indicators.

A control marked Effective without current evidence is a finding. Accuracy or uptime alone does not demonstrate trustworthy AI.

## 13. Incident Management and Escalation

Users must report suspected AI incidents, harmful outputs, privacy or security events, discrimination, unsafe advice, control failures, material vendor issues, and unexplained performance changes through the approved incident route.

Incident response must:

1. Detect, record, classify, and escalate.
2. Assign authority and specialist roles.
3. Map affected systems, data, stakeholders, harms, and dependencies.
4. Preserve evidence with integrity, access control, retention, and legal-hold considerations.
5. Contain unsafe behaviour and provide support or recourse.
6. Assess notification obligations with qualified specialists.
7. Remediate, test, recover, and authorise restart, restriction, pause, or retirement.
8. Update risks, controls, assurance, monitoring, vendor oversight, and lifecycle decisions.

The system owner must not restart a paused or restricted system without authorised evidence that the restart criteria are met.

## 14. Records, Evidence, and Accountability

The Trust must retain proportionate records showing:

- Use-case registration, scope, purpose, owners, decisions, approvals, dates, and review dates
- Risk and impact assessments, risk tolerance, controls, treatments, exceptions, and residual risk
- DPIAs, data maps, vendor terms, security reviews, testing, assurance, monitoring, incidents, complaints, appeals, and retirement evidence
- Material changes, model and vendor versions, configuration, training, user access, and human approvals
- Evidence source, date, scope, confidence, limitations, and reviewer conclusion

Material statements must be labelled as **Evidence**, **Assumption**, **Recommendation**, or **Unknown**. The Trust must not invent evidence, test results, approvals, certifications, regulatory decisions, or organisational facts.

Every major governance decision must include:

- Owner
- Rationale
- Evidence
- Date
- Review date
- Status

## 15. Exceptions and Enforcement

Exceptions must be:

- Documented with the requirement being waived and the reason
- Time-limited and assigned to an accountable owner
- Supported by compensating controls and residual-risk assessment
- Approved by the authorised risk owner and escalated where outside delegated tolerance
- Reviewed before expiry and closed with evidence

An exception requires a maximum duration of 90 days, may be renewed once only after reassessment, and expires automatically if it is not renewed or closed. Approval authority and escalation follow [009-delegated-authorities.md](009-delegated-authorities.md).

Failure to comply may result in restricted access, suspension, withdrawal of approval, incident escalation, corrective action, supplier remediation, disciplinary action under applicable Trust procedures, or referral to the appropriate authority.

No employee will be penalised for raising a good-faith AI safety, privacy, security, fairness, or governance concern through the approved route.

## 16. Policy Review and Approval

The Head of AI Governance will review this policy at least annually and after material changes to law, standards, Trust strategy, risk appetite, operating model, AI systems, vendors, or incidents.

The policy must be approved by the Trust Board on recommendation from the AI Governance Committee. It must be communicated to relevant staff, embedded in procurement and change processes, and supported by standards, procedures, training, and assurance.

| Decision field | Value |
|---|---|
| Owner | Head of AI Governance |
| Rationale | Establish mandatory requirements for safe, lawful, ethical, secure, and accountable AI use |
| Evidence | AI Governance Framework and supporting portfolio artefacts; implementation evidence to be developed |
| Date | 2026-09-11 |
| Review date | 2026-12-11 |
| Status | Draft for consultation |
