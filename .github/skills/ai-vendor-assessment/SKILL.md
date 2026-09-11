---
name: ai-vendor-assessment
description: 'Assess third-party AI vendors and suppliers using a structured AI risk management workflow. Use for AI vendor due diligence, model provider reviews, supplier risk assessments, procurement gates, contract controls, assurance evidence, ongoing monitoring, incidents, concentration risk, and exit planning.'
argument-hint: '[AI vendor, product, service, contract, or supplier assessment scope]'
user-invocable: true
disable-model-invocation: false
---

# AI Vendor Assessment

## Purpose

Assess and manage third-party AI risk across the supplier lifecycle. Produce a decision-ready assessment of whether an AI vendor, model provider, data supplier, platform, integrator, or managed service can be approved, approved with conditions, restricted, paused, or rejected.

Apply NIST AI RMF consistently:

- **GOVERN**: define accountability, procurement gates, risk tolerance, contract authority, escalation, and oversight.
- **MAP**: understand the vendor, AI service, data flows, stakeholders, use context, dependencies, concentration, and lifecycle boundary.
- **MEASURE**: evaluate vendor evidence, trustworthy-AI characteristics, security, privacy, resilience, performance, and control effectiveness.
- **MANAGE**: treat gaps, impose conditions, monitor changes and incidents, and plan suspension, transition, or exit.

This skill supports governance and procurement decisions. It does not provide legal advice, certify a vendor, or replace security, privacy, legal, safety, financial, or domain-specialist review.

## When to Use

Use this skill for:

- Third-party AI vendor and model-provider due diligence
- Procurement and pre-approval assessments
- Vendor renewals, material changes, and service reviews
- SaaS, API, foundation model, hosted model, data, agent, plugin, and integrator assessments
- Contract and data-processing agreement control reviews
- Supplier assurance and evidence requests
- AI supply-chain and concentration-risk analysis
- Vendor incidents, service degradation, model changes, or exit planning

## Working Principles

- Treat the vendor and its downstream providers as part of the AI system risk boundary.
- Verify claims with evidence; distinguish vendor assertions from independently validated evidence.
- Do not treat SOC reports, ISO certificates, questionnaires, or policies as proof that every relevant AI risk is controlled.
- Assess the specific service configuration and intended use, not only the vendor brand or enterprise reputation.
- Preserve customer accountability: outsourcing a capability does not automatically outsource the organization’s legal, ethical, or operational responsibility.
- Identify information the vendor cannot or will not disclose and record the resulting uncertainty.
- Prefer contractual and technical controls that are measurable, testable, enforceable, and linked to a remedy.
- Consider benefits and alternatives as well as risks, including the consequences of vendor failure or non-use.
- Apply heightened scrutiny to high-impact decisions, sensitive data, vulnerable groups, autonomous actions, and irreversible harms.

## Required Assessment Domains

Assess every domain below for every vendor. Mark a domain `Not Applicable` only with a documented rationale. Mark it `To Be Confirmed` when evidence or scope information is missing. Do not silently omit a domain.

- Data Processing
- Data Retention
- Model Training
- Data Location
- Subprocessors
- Security
- Encryption
- Identity
- Access Control
- Incident Management
- Availability
- Resilience
- Intellectual Property (IP)
- Confidentiality
- Audit Rights
- Regulatory Compliance
- Model Changes
- Exit Strategy

For each domain, record the vendor claim, required control or contractual position, evidence reviewed, assessment status, gap or finding, accountable owner, treatment, and review cadence. Assess both the vendor's control environment and the customer's configuration and responsibilities.

## Procedure

### 1. GOVERN: set the approval boundary

Establish:

- Business sponsor, accountable risk owner, procurement owner, service owner, and technical owner
- Privacy, security, legal, compliance, safety, resilience, and subject-matter reviewers
- Intended decision: approve, approve with conditions, restrict, reject, renew, pause, or retire
- Risk appetite, prohibited uses, minimum control requirements, and approval thresholds
- Required procurement stage, exception process, review cadence, and escalation route
- Applicable policies, contracts, standards, regulations, and customer commitments
- Whether the vendor may subcontract, train on customer data, change models, or use data for other purposes

Define who can accept residual risk, approve a material service change, require remediation, suspend use, notify affected parties, and authorize exit.

### 2. MAP: understand the vendor and AI service

Document:

- Legal entity, service name, product version, model or component providers, and service regions
- AI capability, intended purpose, users, affected people, decisions supported, and autonomy level
- Inputs, outputs, prompts, retrieval sources, training or fine-tuning data, telemetry, and metadata
- Data classification, personal data, special-category data, confidential data, retention, deletion, and locations
- System architecture, integrations, tools, plugins, agents, subprocessors, open-source components, and downstream dependencies
- Human oversight, intervention points, fallback process, and routes for appeal or recourse
- Benefits, alternatives, foreseeable misuse, out-of-scope use, and consequences of outage or vendor withdrawal
- Lifecycle stage and vendor change model, including model versioning, deprecation, and release notices

Create a data-flow and dependency view when the service boundary is unclear. Include concentration and single-provider risks where multiple business processes depend on the same vendor or model family.

### 3. MEASURE: request and assess evidence

Request evidence proportional to risk. Typical evidence includes:

- AI system documentation, model cards, system cards, intended-use limits, and known limitations
- Independent evaluations, validation results, safety testing, red-team results, bias and fairness testing, and performance metrics
- Security architecture, penetration tests, vulnerability management, access controls, encryption, logging, incident response, and resilience testing
- Privacy notices, data-processing terms, lawful-basis responsibilities, DPIA support, rights handling, retention, deletion, and international-transfer information
- ISO/IEC 27001 or 42001 certificates and scope, SOC reports, audit reports, and corrective-action records
- Subprocessor list, supply-chain controls, provenance, licensing, open-source governance, and material provider dependencies
- Change-management policy, release notes, model-version controls, notification periods, rollback, and customer testing rights
- Service levels, support model, business-continuity plans, recovery objectives, outage history, and financial or operational viability
- Contract, DPA, confidentiality, use restrictions, audit rights, breach obligations, indemnities, liability, insurance, and exit terms

Classify evidence as `Verified`, `Vendor Reported`, `Independently Assured`, `Partially Verified`, `Outdated`, `Missing`, or `Not Applicable`. Record the evidence date, scope, limitation, and reviewer conclusion.

Assess trustworthy-AI characteristics relevant to the use case:

- Validity and reliability
- Safety and resilience
- Security and robustness
- Accountability and transparency
- Explainability and interpretability
- Privacy enhancement and data governance
- Fairness and harmful-bias management

### 4. Analyze third-party AI risks

Evaluate each required assessment domain and connect it to the relevant risk categories below. Use the domain names in the final assessment even when several domains share one risk or control.

| Assessment domain | Minimum questions to answer |
|---|---|
| Data Processing | What data is processed, for what purpose, under whose instructions, and through which locations and systems? |
| Data Retention | How long are inputs, outputs, prompts, logs, backups, and derived data retained, and how is deletion verified? |
| Model Training | Is customer data used for training, fine-tuning, evaluation, abuse monitoring, or product improvement, and can that use be restricted? |
| Data Location | Where are data, backups, support access, and model-processing activities located, and what transfer safeguards apply? |
| Subprocessors | Which subprocessors and fourth parties are involved, what do they do, and how are changes notified and controlled? |
| Security | What security architecture, testing, vulnerability management, secure development, and supply-chain safeguards exist? |
| Encryption | Is data encrypted in transit, at rest, in backups, and where appropriate during processing, and who controls the keys? |
| Identity | How are workforce, customer, service, and machine identities established, federated, verified, and removed? |
| Access Control | How are least privilege, privileged access, segregation of duties, tenant isolation, and access reviews enforced? |
| Incident Management | How are incidents detected, triaged, contained, investigated, reported, and remediated, including harmful AI outputs? |
| Availability | What service levels, capacity controls, support commitments, outage history, and dependency limits apply? |
| Resilience | What continuity, backup, recovery, failover, disaster-recovery, and degraded-operation capabilities are tested? |
| Intellectual Property (IP) | Who owns inputs, outputs, fine-tuned artifacts, prompts, evaluation data, and improvements, and what license restrictions apply? |
| Confidentiality | How are confidential, personal, regulated, and customer-specific data protected from disclosure or secondary use? |
| Audit Rights | What inspection, evidence, testing, independent assurance, regulator cooperation, and remediation rights are available? |
| Regulatory Compliance | Which laws, regulations, sector rules, contractual duties, and records obligations apply, and how is compliance evidenced? |
| Model Changes | How are model, data, feature, subprocessor, and policy changes assessed, notified, tested, approved, and rolled back? |
| Exit Strategy | Can the customer export data and configuration, transition safely, revoke access, delete data, and verify decommissioning? |

Evaluate at least the relevant risk categories:

- Privacy, confidentiality, data retention, secondary use, training use, and data-location risk
- Security, prompt injection, sensitive-information disclosure, insecure output handling, excessive agency, and supply-chain compromise
- Safety, harmful outputs, unsafe automation, inadequate human oversight, and failure to support recourse
- Fairness, bias, representativeness, performance variation, and impacts on vulnerable groups
- Accuracy, reliability, drift, hallucination, reproducibility, explainability, and model limitations
- Legal, regulatory, contractual, intellectual-property, licensing, and records-management exposure
- Operational resilience, availability, scalability, service degradation, model retirement, and portability
- Subprocessor, fourth-party, open-source, data-provider, and geographic-jurisdiction risk
- Concentration, lock-in, substitutability, financial viability, and systemic dependency
- Reputational, accountability, human-factor, misuse, and downstream decision risk

For each material risk, identify cause, event, impact, affected stakeholders, inherent likelihood and impact, existing controls, control effectiveness, residual risk, tolerance, owner, treatment, and status.

### 5. Review contractual and technical controls

Check whether the proposed arrangement clearly addresses:

- Permitted purpose, prohibited use, customer instructions, and change approval
- Data ownership, confidentiality, no-training or restricted-training terms, retention, deletion, and return
- Controller/processor roles, subprocessor approval, assistance with data-subject rights, DPIAs, and incident response
- Security baseline, access control, encryption, logging, vulnerability disclosure, and evidence obligations
- Model and service changes, version pinning or testing, notice periods, rollback, and deprecation support
- Performance, safety, fairness, availability, recovery, support, service levels, and reporting metrics
- Audit, inspection, independent assurance, testing rights, regulator cooperation, and remediation timelines
- Breach notification, harmful-output escalation, cooperation, liability, indemnity, insurance, and remedies
- Portability, interoperability, transition assistance, data and model disposition, termination, and exit verification

Call out clauses that are vague, non-negotiable, inconsistent with the use case, or unenforceable in practice.

### 6. MANAGE: decide and treat risk

Use one of these decisions:

- **Approve**: evidence and controls meet tolerance.
- **Approve with conditions**: use is permitted only with dated remediation, restrictions, or compensating controls.
- **Restrict**: limit data, users, geographies, decisions, autonomy, volume, or integrations.
- **Reject**: risk, uncertainty, or contract terms exceed tolerance and cannot be corrected.
- **Pause**: suspend use pending investigation, incident response, or remediation.
- **Exit or retire**: end the service and manage data, decisions, dependencies, and transition.

Every treatment needs an accountable owner, action, due date or cadence, acceptance authority, success measure, evidence of completion, and residual-risk decision.

Define ongoing monitoring for:

- Vendor control attestations, certificates, audits, and material findings
- Model and service versions, performance, drift, safety, fairness, privacy, and security events
- Incidents, complaints, appeals, harmful outputs, near misses, breaches, and regulatory changes
- Subprocessor changes, acquisitions, outages, financial distress, concentration, and geopolitical exposure
- SLA performance, support responsiveness, recovery tests, and exit-readiness evidence

Set triggers for reassessment, contract renegotiation, restricted use, rollback, suspension, notification, or exit.

### 7. Produce the assessment

Unless another format is requested, include:

1. **Executive decision and recommendation**
2. **Vendor, service, scope, data, and dependency profile**
3. **GOVERN and MAP findings**
4. **Evidence inventory and confidence assessment**
5. **Required domain coverage table** for all 18 domains
6. **Third-party AI risk register**
7. **Contractual and technical control review**
8. **Residual risk, conditions, and approval authority**
9. **Monitoring, incident, renewal, and reassessment plan**
10. **Exit and decommissioning plan**
11. **Open questions and required specialist review**

For a concise register, use these fields:

| Field | Required content |
|---|---|
| Vendor Risk ID | Stable identifier such as `VENDOR-RISK-001` |
| Vendor / Service | Legal entity, product, version, and provider role |
| Risk Category | Privacy, Security, Safety, Operational, Third Party, Legal, or other relevant category |
| Risk Description | Cause, event, and consequence |
| Affected Stakeholders | People, groups, systems, or organizations affected |
| Evidence / Confidence | Evidence source, date, limitation, and confidence |
| Inherent Risk | Likelihood, impact, score, and rationale before controls |
| Existing Controls | Vendor, customer, contractual, and technical controls |
| Control Effectiveness | Effective, Partially Effective, Ineffective, Not Tested, or Unknown |
| Residual Risk | Post-control score, uncertainty, and tolerance decision |
| Risk Owner | Accountable role |
| Treatment / Contract Action | Required remediation, restriction, clause, or decision |
| Due Date / Review Cadence | Target date or reassessment trigger |
| Status | Proposed, Open, Conditional Approval, Monitoring, Paused, Rejected, Accepted, or Closed |

## Quality Gate

Before finalizing, verify:

- The assessed service and provider boundary are explicit, including relevant subprocessors and fourth parties.
- All 18 required assessment domains are present, each with status, evidence, finding, owner, treatment, and review cadence, or a justified `Not Applicable` or `To Be Confirmed` result.
- The recommendation matches the evidence, intended use, risk tolerance, and decision authority.
- Vendor claims are separated from independent assurance and customer validation.
- Data flows, training use, retention, deletion, jurisdiction, and controller/processor responsibilities are addressed.
- Model changes, outages, incidents, harmful outputs, and deprecation are covered.
- Contract controls are specific, testable, enforceable, and linked to remedies.
- Residual risk is explicit and formally accepted only by an authorized owner.
- Monitoring, renewal, reassessment, suspension, portability, and exit criteria are defined.
- High-impact decisions, vulnerable groups, irreversible harms, concentration, and lock-in receive appropriate attention.
- No certification, legal, privacy, or security conclusion is overstated beyond the evidence.
- Open evidence requests and specialist review requirements are clearly listed.
