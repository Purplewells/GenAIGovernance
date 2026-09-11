---
title: Telleion Hospitals NHS Foundation Trust - AI Governance Framework
version: 0.1
date: 2026-09-11
lifecycle_stage: Governance framework and portfolio operating model
scope: AI systems proposed, acquired, developed, deployed, monitored, changed, or retired by the Trust
jurisdiction: United Kingdom
owner: Head of AI Governance
approval_authority: Trust Board, supported by the AI Governance Committee and relevant executive owners
review_date: 2026-12-11
status: Draft for consultation
---

# Telleion Hospitals NHS Foundation Trust
# AI Governance Framework

## 1. Executive Purpose and Decision

This document is the master description of how Telleion Hospitals NHS Foundation Trust governs artificial intelligence. It establishes the operating model for adopting AI safely, lawfully, ethically, and effectively while delivering measurable benefits to patients, staff, and the organisation.

**Decision requested:** The AI Governance Committee and Trust Board are asked to endorse this framework as the operating basis for AI governance, subject to completion of the evidence, approval, and implementation actions identified in this document.

**Important status:** This framework does not approve any individual AI system. Use-case approval remains conditional on system-specific risk assessment, privacy and security review, assurance evidence, human-oversight arrangements, and authorised residual-risk acceptance.

## 2. Portfolio Context and Evidence Boundary

Telleion Hospitals NHS Foundation Trust is a fictional NHS-style organisation used solely for portfolio and learning purposes.

| Attribute | Scenario detail |
|---|---|
| Organisation | Telleion Hospitals NHS Foundation Trust |
| Employees | Approximately 1,500 |
| Patients | Approximately 50,000 annually |
| Technology environment | EPR, LIS, RIS, PACS, Microsoft 365, Azure, Data Warehouse, Power BI, and third-party SaaS platforms |
| Governance context | Departments have begun proposing AI solutions, prompting a formal AI Governance Programme |

The organisation, workforce, patient volume, systems, proposals, approvals, controls, test results, and regulatory outcomes in this portfolio are scenario inputs. They are not evidence of a real NHS organisation or real-world compliance.

## 3. Board Assurance Objective

The Board requires assurance that AI is:

- Safe for patients, staff, and other affected people
- Lawful and appropriately governed
- Ethical, fair, transparent, and human-centred
- Secure, resilient, and operationally controlled
- Supported by measurable benefits
- Subject to effective oversight throughout its lifecycle

The Board should receive evidence of decisions and control operation, not only policies, committee terms of reference, vendor claims, or framework mappings.

## 4. Framework Hierarchy and Standards

### Primary framework

Use **NIST AI Risk Management Framework 1.0** as the primary risk-management framework:

- **GOVERN:** accountability, policy, risk tolerance, roles, oversight, resources, and escalation
- **MAP:** purpose, context, stakeholders, benefits, impacts, harms, dependencies, data, and lifecycle boundaries
- **MEASURE:** trustworthy-AI characteristics, risks, controls, evidence, performance, uncertainty, and outcomes
- **MANAGE:** treatment, ownership, residual risk, monitoring, incidents, change, restriction, suspension, and retirement

### Supporting sources

Use these sources where relevant and state the edition, version, publication date, and applicability:

- ISO/IEC 42001 for an AI management-system perspective
- ISO/IEC 27001 for information-security governance and controls
- UK GDPR and Data Protection Act 2018 for personal-data processing
- ICO AI and data-protection guidance
- OWASP GenAI Security guidance for generative-AI threats and mitigations
- NIST Cybersecurity Framework where it supports security risk management
- Equality Act 2010 and relevant NHS, clinical-safety, accessibility, employment, or sector requirements where the use case requires them

These sources must not be treated as interchangeable. Legal duties, contractual obligations, certifiable management-system requirements, voluntary frameworks, regulator guidance, and security best practices must remain distinct.

## 5. Governance Principles

Telleion AI governance is:

- Risk-based
- Proportionate
- Evidence-based
- Auditable
- Transparent
- Accountable
- Human-centred

Governance decisions must consider benefits as well as risks, including patient outcomes, staff experience, access, equality, vulnerable groups, environmental effects, and routes to recourse.

## 6. Governance Operating Model

### 6.1 Accountable roles

| Role | Accountability |
|---|---|
| Trust Board | Approves the governance framework, risk appetite, material risk acceptance, and high-impact deployment decisions |
| AI Governance Committee | Reviews use cases, risk assessments, controls, assurance evidence, exceptions, incidents, and material changes; recommends decisions to the authorised executive or Board |
| Head of AI Governance | Owns the AI governance process, portfolio reporting, escalation, document consistency, and governance records |
| Executive sponsor | Owns the business outcome, resources, benefits, and operational accountability for a use case |
| System owner | Owns the AI system, intended use, configuration, lifecycle, operational controls, and safe operation |
| Risk owner | Accepts or treats residual risk within delegated authority |
| Data Protection Officer | Advises on UK GDPR, DPIAs, data rights, data sharing, transfers, retention, and privacy risk |
| Chief Information Security or security lead | Oversees security architecture, access, resilience, vulnerabilities, incidents, and assurance |
| Clinical or domain safety lead | Reviews clinical or domain harms, safe use, escalation, and professional accountability where relevant |
| Procurement and Legal | Assess suppliers, contracts, liability, audit rights, data-processing terms, intellectual property, regulatory duties, and exit |
| Internal Audit or independent assurance | Provides proportionate independent review of design, implementation, operating effectiveness, and evidence |
| Front-line users | Apply approved procedures, exercise human oversight, report issues, and support safe escalation |

Named individuals must be recorded in each use-case decision. A team name alone is not sufficient for material risk acceptance.

### 6.2 Decision rights

The Trust must record who can:

- Register and classify a proposed AI use case
- Approve design or pilot activity
- Approve processing of personal or special-category data
- Accept residual risk
- Approve a material model, data, vendor, user, or purpose change
- Restrict, pause, roll back, or retire an AI system
- Authorise restart after an incident
- Approve decommissioning and closure of outstanding obligations

A decision is valid only when the owner, rationale, evidence, date, review date, and status are recorded.

## 7. AI Lifecycle and Stage Gates

Every AI system must be tracked through the following lifecycle:

1. Idea
2. Use-case assessment
3. Risk assessment
4. Impact assessment
5. Design
6. Development or acquisition
7. Testing
8. Governance approval
9. Deployment
10. Monitoring
11. Review
12. Incident management
13. Decommissioning

### Gate requirements

| Gate | Minimum evidence | Decision |
|---|---|---|
| Idea and use-case assessment | Purpose, benefit, alternatives, intended users, affected people, initial risk and prohibited-use check | Register, reject, or request further assessment |
| Risk and impact assessment | Context, harms, stakeholders, data, risk rating, tolerance, privacy and specialist questions | Proceed to design, restrict, or reject |
| Design and acquisition | Control design, security and privacy architecture, vendor terms, human oversight, monitoring, exit | Approve build or procurement subject to conditions |
| Testing | Validation, safety, fairness, security, privacy, usability, resilience, and assurance results | Approve pilot, remediate, restrict, or reject |
| Governance approval | Complete evidence pack, open findings, residual risk, named owners, operating procedures | Approve deployment, approve with conditions, or do not proceed |
| Operation | Monitoring, incidents, complaints, benefits, control evidence, changes, and review results | Continue, restrict, pause, or reassess |
| Material change | Change impact, updated risks, testing, vendor evidence, and decision record | Approve change, require further testing, or reject |
| Retirement | Transition, data and access disposition, records, contracts, incidents, and closure evidence | Retire and close, or extend controlled operation |

## 8. Strategy and Portfolio Management

The Trust should maintain an AI portfolio that links each proposal to a business or patient outcome and prevents uncoordinated adoption.

For each proposal, record:

- Business problem and measurable benefit
- Alternatives to AI and consequences of not proceeding
- Executive sponsor, system owner, risk owner, and approval authority
- Intended use, prohibited use, users, affected people, and operating context
- Lifecycle stage, technology and vendor dependencies, and data boundary
- Risk tier, required assurance, and decision gate
- Benefits-realisation measures and review cadence
- Exit, replacement, or decommissioning assumptions

Portfolio reporting to the Board should include active systems, proposals by lifecycle stage, risks outside tolerance, overdue remediation, incidents, vendor dependencies, benefits achieved, and decisions required.

## 9. Policy and Standards Architecture

The Trust should maintain a controlled hierarchy of AI governance artefacts:

1. AI Governance Framework: this master operating model
2. AI Policy: mandatory principles, prohibited uses, responsibilities, and escalation
3. AI Standard and procedures: minimum requirements for data, security, privacy, human oversight, testing, monitoring, incidents, vendors, and retirement
4. Use-case records: system context, risks, controls, approvals, and lifecycle status
5. Risk registers and control matrices: traceability from risk to treatment and evidence
6. Assurance Plans and reports: tests of design, operation, and effectiveness
7. Incident and corrective-action records: evidence of response and learning

Policies must be version-controlled, approved, reviewed, communicated, and linked to operating procedures. A policy does not demonstrate that a control operates.

## 10. Risk Management

Risk management uses the NIST AI RMF continuous loop:

- **GOVERN:** set risk appetite, tolerance, decision rights, escalation, and prohibited uses.
- **MAP:** identify purpose, stakeholders, benefits, impacts, harms, dependencies, data, misuse, and lifecycle boundaries.
- **MEASURE:** evaluate trustworthy-AI characteristics, performance, uncertainty, controls, incidents, and real-world outcomes.
- **MANAGE:** treat, accept, restrict, pause, transfer, or retire risk with accountable ownership.

Every risk record must distinguish:

- **Inherent risk:** exposure before considering controls
- **Controls:** preventive, detective, corrective, compensating, and human-oversight measures
- **Residual risk:** exposure after controls, with uncertainty and comparison to tolerance

Risk scores must show the method, rationale, evidence, limitations, affected stakeholders, and authorised risk acceptor. Missing evidence is not evidence of low risk.

## 11. Privacy and Data Protection

Privacy governance must be proportionate to the data and use case. For relevant systems, assess:

- Purpose, necessity, proportionality, and lawful basis
- Special-category and health data processing
- Transparency, privacy notices, rights, access, rectification, erasure, objection, and recourse
- Automated decision-making and profiling implications
- Data minimisation, accuracy, provenance, retention, deletion, and legal hold
- Data locations, international transfers, processors, subprocessors, and data-processing agreements
- DPIA requirements, residual privacy risk, and DPO advice
- Training, product improvement, analytics, and secondary use of customer data
- Access, confidentiality, encryption, logging, incident response, and breach assessment

A DPIA marked Draft must not be described elsewhere as complete. Privacy conclusions must be based on the actual processing design and qualified review.

## 12. Security and Resilience

AI systems must be assessed within the Trust's information-security and operational-resilience boundaries. Controls should address:

- Identity, authentication, least privilege, privileged access, segregation of duties, and access reviews
- Secure configuration, tenant isolation, secrets, keys, encryption, and network protection
- Data and model integrity, provenance, supply-chain security, and dependency management
- Prompt injection, data leakage, insecure output handling, excessive agency, malicious tool use, and other GenAI threats where applicable
- Vulnerability management, secure development, penetration testing, logging, detection, and response
- Availability, backup, recovery, failover, degraded operation, and service-level dependencies
- Vendor, subprocessor, cloud, and concentration risks
- Evidence of operating effectiveness and tested recovery or rollback procedures

Security certifications and vendor questionnaires are supporting evidence only. They do not replace system-specific testing or risk assessment.

## 13. Human Oversight and Accountability

Human oversight must be meaningful, competent, and capable of changing the outcome. Each use case must define:

- Which decisions remain human decisions
- What the human reviewer can see, challenge, override, and record
- Required competence, training, workload, independence, and escalation route
- Prohibited automation, including decisions that may not be delegated without appropriate authority
- How overrides, approvals, dissent, complaints, appeals, and recourse are recorded
- How automation bias and over-reliance are monitored
- How affected people can request human review or correction

A nominal human in the loop is insufficient if the reviewer lacks time, information, authority, or practical ability to intervene.

## 14. Assurance

The Trust must maintain an AI Assurance Plan for material systems. Each assurance activity should specify:

- Objective and linked risk, control, obligation, or decision
- Test method, population or sample, evidence, and pass criteria
- Performer, independent reviewer, competence, cadence, trigger, and limitations
- Result, finding, uncertainty, remediation, owner, due date, retest, and closure authority

Assurance must test design adequacy, implementation, operating effectiveness, and independent assurance separately. Use decision gates for design, build, pre-deployment, material change, operation, pause, and retirement.

A control marked Effective without current supporting evidence is a finding. Accuracy and uptime alone do not demonstrate trustworthy AI.

## 15. Monitoring and Benefits

Monitoring must demonstrate that the system remains within approved boundaries and continues to deliver intended benefits. Define:

- Performance, validity, reliability, calibration, drift, and out-of-scope use indicators
- Safety, privacy, security, fairness, accessibility, human-oversight, and operational indicators
- Alert thresholds, owners, response times, escalation, and review cadence
- Complaints, appeals, incidents, near misses, harmful outputs, and affected-person outcomes
- Vendor and model-version changes, subprocessors, outages, and regulatory developments
- Benefits, unintended effects, distributional impacts, and whether benefits remain proportionate to harms
- Triggers for re-entering MAP and MEASURE, restriction, pause, rollback, or retirement

Monitoring outputs must be retained as evidence and reviewed by accountable owners. Suppressed alerts, missed incidents, or overdue responses must be reported.

## 16. Third-Party AI and Procurement

Vendors, model providers, subprocessors, fourth parties, data suppliers, integrators, open-source components, and downstream users form part of the risk boundary where relevant.

Assess and contract for:

- Data processing, retention, model training, location, transfers, and deletion
- Subprocessors and fourth-party visibility
- Security, encryption, identity, access control, incident management, availability, resilience, confidentiality, and IP
- Audit rights, independent assurance, regulatory cooperation, and evidence access
- Model and service changes, notice periods, testing, rollback, and deprecation
- Liability, indemnity, insurance, remedies, service levels, and breach obligations
- Portability, transition support, termination, exit strategy, and decommissioning verification

Separate vendor assertions from independent assurance and customer validation. A supplier approval does not transfer the Trust's accountability.

## 17. Incident Management

AI incidents include harmful or unsafe outputs, privacy breaches, security events, discrimination, model drift, control failure, vendor incidents, availability failures, and loss of approved control.

The Trust response is to:

1. Detect, record, classify, and escalate.
2. Assign incident authority and specialist roles.
3. Map affected systems, data, stakeholders, harms, and dependencies.
4. Preserve evidence with integrity, access control, retention, and legal-hold considerations.
5. Contain unsafe behaviour and provide support or recourse.
6. Assess notification obligations with qualified specialists.
7. Remediate, test, recover, and authorise restart, restriction, pause, or retirement.
8. Update risks, controls, assurance, monitoring, vendor oversight, and lifecycle decisions.

Closure requires evidence of remediation, residual-risk treatment, authorised decision, communications, and lessons learned.

## 18. Governance Records and Document Consistency

The Head of AI Governance maintains the authoritative portfolio record and document register. Artefacts must be reconciled for:

- Risk IDs, descriptions, categories, scores, inherent and residual risk, tolerance, and status
- Owners, approval authorities, dates, versions, lifecycle states, and review dates
- DPIAs, data maps, retention and transfer records, vendor terms, policies, control matrices, assurance results, incidents, and retirement records
- Claims of completion, effectiveness, approval, compliance, or acceptance

Contradictions must be recorded as findings. For example, a risk register stating that a DPIA is complete while the DPIA remains Draft must be resolved before relying on the claim for approval.

## 19. Current Portfolio Evidence and Known Dependencies

The AI-004 recruitment-screening artefacts currently indicate the following scenario status:

| Artefact | Current status | Governance implication |
|---|---|---|
| Risk assessment | Draft for consultation | Risk analysis requires review and approval |
| Control matrix | Draft for consultation | Controls are proposed and not yet demonstrated effective |
| Fairness assessment framework | Draft for consultation | Methodology requires approval before fairness evidence is relied upon |
| Governance review and approval decision | Ready for Governance Committee review | Conditional pilot recommendation is not final approval |

For AI-004, the current decision position is conditional: pilot testing must not begin until the required fairness validation, DPIA, human-oversight procedure, monitoring plan, vendor assessment where applicable, incident procedure, and authorised approval evidence are complete.

This table is a document-status summary, not evidence that any listed control has been implemented or tested.

## 20. Reporting and Review

The AI Governance Committee should review the portfolio at least quarterly and more frequently for high-risk systems or material changes. Reporting should include:

- New and active use cases by lifecycle stage and risk tier
- Decisions required and approvals due
- Risks outside tolerance and overdue treatments
- Control and assurance results, failed tests, and retests
- Privacy, security, safety, fairness, incident, complaint, and appeal trends
- Vendor changes, concentration risks, and exit readiness
- Benefits achieved and unintended impacts
- Resources, competence, and policy changes required

This framework should be reviewed on the stated review date and after material changes to law, standards, Trust strategy, risk tolerance, operating model, or AI portfolio.

## 21. Framework Completion Standard

A governance decision is complete only when:

- The requested decision is clear.
- Scope, exclusions, audience, date, lifecycle stage, jurisdiction, and assumptions are recorded.
- GOVERN, MAP, MEASURE, and MANAGE are addressed.
- Benefits, risks, impacts, harms, affected people, and recourse are considered.
- Owners, decision rights, controls, evidence, assurance, monitoring, and escalation are explicit.
- Inherent risk, controls, and residual risk are distinguished.
- Legal, privacy, security, safety, accessibility, audit, regulatory, and domain-specialist review is flagged where required.
- The decision includes owner, rationale, evidence, date, review date, and status.

**Approval status:** Draft for consultation. Final approval authority: Trust Board, on recommendation from the AI Governance Committee and relevant accountable executives.
