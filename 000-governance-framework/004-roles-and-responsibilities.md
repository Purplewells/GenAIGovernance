---
title: Telleion Hospitals NHS Foundation Trust - AI Governance Roles and Responsibilities
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: Trust Board, on recommendation from the AI Governance Committee
review_date: 2026-12-11
scope: All AI systems proposed, acquired, developed, used, changed, monitored, or retired by the Trust
---

# AI Governance Roles and Responsibilities

## 1. Purpose

This document defines accountability and decision rights for AI governance at Telleion Hospitals NHS Foundation Trust. It supports the AI Governance Framework, Policy, Principles, risk appetite, and RACI matrix.

The Trust remains accountable for AI used in its services, including where capability is supplied by a vendor, cloud platform, model provider, subprocessor, or integrator.

## 2. Accountability Rules

- Each AI system must have a named executive sponsor, system owner, risk owner, and operational owner.
- The person who operates a control must not be the sole person deciding that the control is effective for a material risk.
- Specialist roles provide challenge within their competence; they do not automatically accept business or clinical risk unless expressly authorised.
- Risk acceptance must be within delegated authority and supported by evidence, rationale, date, review date, and status.
- Delegated limits and reserved matters are defined in [009-delegated-authorities.md](009-delegated-authorities.md); where authority is unclear, the decision escalates and the higher-risk position applies.
- Duties must be reassigned when a role is vacant, conflicted, or lacks the competence or authority required.
- A committee may recommend a decision, but the authorised decision-maker remains accountable for the decision.

## 3. Role Charters

### Trust Board

**Accountable for:** organisational direction and material AI risk decisions.

**Responsibilities:**

- Approve this framework, policy, principles, and organisational AI risk appetite.
- Approve material high-impact AI deployment or residual-risk acceptance within its authority.
- Require evidence of benefits, harms, control operation, assurance, and incidents.
- Review portfolio risks outside tolerance, major incidents, recurring findings, and resource constraints.
- Ensure AI governance is integrated with wider clinical, operational, information, and corporate governance.

### AI Governance Committee

**Accountable for:** operational governance oversight and recommendations to authorised executives or the Board.

**Responsibilities:**

- Review and classify proposed AI use cases.
- Review risk assessments, impact assessments, controls, assurance plans, vendor assessments, and decision gates.
- Challenge unsupported claims, missing evidence, inconsistent records, and unowned residual risk.
- Recommend approval, conditional approval, restriction, pause, rejection, or retirement.
- Review incidents, exceptions, monitoring results, complaints, appeals, benefits, and remediation.
- Maintain a clear decision log and escalate matters beyond delegated authority.

### Head of AI Governance

**Accountable for:** the AI governance operating model and portfolio record.

**Responsibilities:**

- Maintain the AI inventory, governance process, templates, records, and reporting.
- Coordinate GOVERN, MAP, MEASURE, and MANAGE activities.
- Ensure use cases reach the correct review and approval gate.
- Monitor evidence quality, document consistency, overdue actions, and risks outside tolerance.
- Coordinate committee papers, escalation, policy review, and continual improvement.
- Ensure specialist review is obtained where required.

### Executive Sponsor

**Accountable for:** the business or service outcome and resources for a use case.

**Responsibilities:**

- Define the problem, intended benefits, alternatives, budget, and operational context.
- Ensure a capable system owner and risk owner are appointed.
- Provide resources for controls, assurance, monitoring, training, incidents, and exit.
- Sponsor remediation and accept business accountability for conditional decisions.
- Report when benefits, use, or operating conditions change materially.

### System Owner

**Accountable for:** safe operation and lifecycle management of a specific AI system.

**Responsibilities:**

- Maintain the approved purpose, boundaries, configuration, versions, users, and dependencies.
- Implement controls and ensure operating procedures are followed.
- Maintain system documentation, monitoring, incident, change, and retirement arrangements.
- Ensure human oversight is meaningful and users are trained.
- Escalate incidents, drift, harmful outputs, control failures, and material changes.
- Prevent use outside the approved scope.

### Risk Owner

**Accountable for:** treatment or acceptance of residual risk.

**Responsibilities:**

- Confirm risk descriptions, ratings, tolerance, affected stakeholders, and uncertainty.
- Ensure treatments have owners, due dates, evidence, dependencies, and success measures.
- Accept residual risk only within delegated authority and for a defined period.
- Escalate risks outside tolerance or where evidence is insufficient.
- Review risk after incidents, changes, new evidence, or expiry of acceptance.

Risk owners may accept residual risk only where the Delegated Authorities Schedule confirms their authority for the classification and risk domain. Otherwise they must escalate to the AI Governance Committee or Trust Board.

### Data Protection Officer

**Accountable for:** independent privacy advice and challenge.

**Responsibilities:**

- Advise on UK GDPR, Data Protection Act 2018, lawful basis, transparency, rights, DPIAs, transfers, retention, and data sharing.
- Review processing of health, special-category, confidential, or vulnerable-person data.
- Challenge secondary use, model training, vendor access, and unsupported privacy claims.
- Advise on data incidents and regulatory notification assessment.
- Record advice, limitations, and unresolved privacy risks.

### Security Lead

**Accountable for:** information-security and resilience advice and challenge.

**Responsibilities:**

- Review identity, access, encryption, secrets, logging, vulnerability, architecture, and supply-chain controls.
- Assess availability, recovery, fallback, resilience, and incident response.
- Review vendor and cloud security evidence and testing.
- Set or advise on security thresholds and escalation triggers.
- Support containment, investigation, remediation, and recovery after incidents.

### Clinical or Domain Safety Lead

**Accountable for:** domain-specific safety and professional-risk advice where relevant.

**Responsibilities:**

- Define harms, safe intended use, contraindications, failure modes, and escalation.
- Review clinical or domain validation, human oversight, training, workload, and recourse.
- Challenge unsafe automation, alert fatigue, over-reliance, and unclear accountability.
- Recommend restrictions, pause, remediation, or retirement where safety evidence is insufficient.

### Procurement and Legal

**Accountable for:** supplier, contract, and legal-risk review.

**Responsibilities:**

- Assess vendor capability, evidence, subcontractors, financial and concentration risks.
- Negotiate data processing, confidentiality, training-use, security, audit, incident, liability, change, and exit terms.
- Ensure contract commitments are measurable, testable, enforceable, and linked to remedies.
- Flag legal, intellectual-property, regulatory, employment, clinical, and contractual review requirements.
- Maintain supplier and contract records.

### Assurance or Internal Audit

**Accountable for:** proportionate independent assurance.

**Responsibilities:**

- Review design adequacy, implementation, operating effectiveness, and evidence quality.
- Define test method, sample, pass criteria, limitations, and reviewer independence.
- Report findings and verify remediation or retesting.
- Escalate recurring, overdue, or material findings.
- Avoid relying solely on policy, certificate, questionnaire, or management assertion.

### Managers and Front-line Users

**Accountable for:** approved use in practice and prompt escalation.

**Responsibilities:**

- Use only approved systems, purposes, data, versions, and workflows.
- Complete required training and follow human-oversight procedures.
- Check outputs, exercise judgement, record decisions, and challenge or override results.
- Report incidents, harmful outputs, bias, privacy concerns, security events, and unexpected behaviour.
- Do not enter unauthorised confidential or personal data into AI systems.

## 4. Responsibility Boundaries

| Boundary | Rule |
|---|---|
| Business benefit | Executive sponsor remains accountable for intended value and resources |
| System operation | System owner remains accountable for approved operation and lifecycle |
| Residual risk | Risk owner must accept, treat, restrict, pause, or escalate risk |
| Privacy | DPO advises and challenges; authorised business roles remain accountable for lawful processing decisions |
| Security | Security lead advises and challenges; system owner remains accountable for system controls |
| Clinical or domain safety | Specialist lead advises and challenges; professional and executive accountability remains explicit |
| Supplier performance | Vendor may be contractually responsible, but the Trust retains governance accountability |
| Independent assurance | Assurance provides an opinion or findings; it does not own the control or accept risk |

## 5. Review and Decision Records

Role assignments must be reviewed at each lifecycle gate, after material change, after an incident, and at least annually. Conflicts of interest, vacancies, capability gaps, and temporary delegations must be recorded.

Every material decision must record owner, rationale, evidence, date, review date, status, conditions, and escalation route.
