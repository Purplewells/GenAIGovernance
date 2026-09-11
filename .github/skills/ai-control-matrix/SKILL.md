---
name: ai-control-matrix
description: 'Create and maintain an AI control matrix mapping governance and technical controls to NIST AI RMF, ISO/IEC 42001, ISO/IEC 27001, UK GDPR, relevant ICO guidance, and OWASP GenAI guidance where applicable. Use for AI governance crosswalks, control inventories, audit readiness, gap assessments, implementation roadmaps, and evidence mapping.'
argument-hint: '[AI system, control scope, framework set, or assessment question]'
user-invocable: true
disable-model-invocation: false
---

# AI Control Matrix

## Purpose

Create a practical, evidence-based control matrix for AI systems and their supporting governance. Map each control to the requested sources without implying that one framework satisfies another automatically:

- **NIST AI RMF**: GOVERN, MAP, MEASURE, and MANAGE outcomes and practices
- **ISO/IEC 42001**: AI management-system requirements and applicable controls or processes
- **ISO/IEC 27001**: information-security management requirements and applicable Annex A controls, using the stated edition
- **UK GDPR**: applicable principles, rights, controller or processor duties, and lawful-processing obligations
- **ICO guidance**: relevant UK data-protection and AI guidance, with title, topic, and current version or date
- **OWASP GenAI guidance**: applicable generative-AI security risks and mitigations, such as prompt injection, sensitive-information disclosure, supply-chain risk, excessive agency, and improper output handling

The matrix is an implementation and assurance aid. It is not legal advice, an ISO certification opinion, or a claim that a control is effective merely because it is mapped to a framework.

## When to Use

Use this skill for:

- AI governance control inventories and crosswalks
- NIST AI RMF, ISO 42001, ISO 27001, UK GDPR, ICO, or OWASP readiness reviews
- Control design and ownership assignment
- Audit and assurance evidence planning
- Gap assessments and remediation roadmaps
- AI management-system scope and policy design
- Generative-AI security control reviews

## Working Rules

- Confirm the AI system, organizational boundary, geography, data, lifecycle stage, and intended assurance outcome before mapping.
- Record the exact framework edition, regulation version, guidance title, publication date, and source location when available.
- Distinguish mandatory law, certifiable management-system requirements, voluntary frameworks, regulator guidance, and security best-practice guidance.
- Map a control because its intent and evidence are materially related, not because keywords look similar.
- Use `Not Applicable` only with a rationale. Use `To Be Confirmed` when the scope or evidence is insufficient.
- Do not invent clause numbers, control identifiers, legal conclusions, or ICO recommendations. Quote or link the authoritative source when precision matters.
- Preserve traceability from risk or obligation to control, owner, evidence, test, finding, and remediation.
- One control may map to multiple sources, but each mapping needs a concise rationale.
- A mapping is not coverage. Mark implementation, design, operating effectiveness, and assurance status separately.
- Treat third parties, model providers, data suppliers, integrators, open-source dependencies, and downstream users as part of the risk boundary where relevant.

## Procedure

### 1. Establish scope and authority

Capture:

- AI system, use case, model or provider, business process, and lifecycle stage
- Organization, legal entities, locations, processing activities, and UK GDPR applicability
- Controller, processor, joint-controller, or other relevant roles
- Information-security and AI management-system boundaries
- Intended users, affected people, vulnerable groups, and downstream recipients
- Framework editions and authoritative sources being used
- Assessment purpose: design, implementation, audit readiness, certification preparation, incident response, or risk treatment
- Risk tolerance, approval authority, and required specialist reviewers

If a missing fact changes applicability, ask a focused question. Otherwise state the assumption in the matrix header.

### 2. Build the control population

Start from risks, obligations, and lifecycle outcomes rather than copying every framework item. Consider controls for:

- Governance, accountability, roles, decision rights, and risk acceptance
- AI inventory, use-case approval, prohibited use, and change management
- Data governance, provenance, quality, minimization, retention, and deletion
- Privacy, lawful basis, transparency, rights handling, DPIA, and privacy by design
- Security architecture, access control, secrets, logging, monitoring, incident response, and resilience
- Model validity, reliability, safety, robustness, fairness, bias, explainability, and human oversight
- Testing, red teaming, evaluation datasets, drift, performance thresholds, and release gates
- Generative-AI risks including prompt injection, data leakage, insecure output handling, excessive agency, model or plugin supply chain, and unbounded consumption
- Third-party due diligence, contracts, service changes, subprocessors, assurance reports, and exit planning
- User training, acceptable use, complaints, appeals, recourse, and stakeholder engagement
- Records, evidence retention, internal audit, management review, corrective action, and continual improvement
- Suspension, rollback, retirement, decommissioning, data disposition, and downstream transition

Give each control a stable identifier such as `AI-CTRL-001`. Keep controls atomic enough that one owner can implement and one test can assess them.

### 3. Map each control to authoritative sources

For every control, assess each source independently:

- **NIST AI RMF**: identify the relevant function and outcome or practice; explain how the control supports trustworthy and responsible AI risk management.
- **ISO/IEC 42001**: identify the applicable management-system clause, annex guidance, or process area from the selected edition; distinguish requirement from guidance.
- **ISO/IEC 27001**: identify the selected edition and applicable ISMS requirement or Annex A control; explain the information-security relationship and avoid treating Annex A as an AI-specific catalogue.
- **UK GDPR**: identify the relevant principle, right, role, or obligation only when the processing facts support applicability; note when the Data Protection Act 2018 or another instrument also needs review.
- **ICO guidance**: cite the specific guidance document or topic and its date or version; explain whether it is regulatory guidance, practical guidance, or another source.
- **OWASP GenAI**: map only when the system uses generative models, LLMs, agents, retrieval, tools, plugins, or related components; identify the relevant risk and mitigation rather than forcing a mapping.

Use `Direct`, `Partial`, `Supporting`, `Not Applicable`, or `To Be Confirmed` for mapping strength. Explain partial mappings and gaps.

### 4. Define implementation and evidence

For each control, specify:

- Control objective and concise control statement
- Accountable owner and operational owner
- Lifecycle stage and affected assets or processes
- Implementation status: Not Started, Planned, In Progress, Implemented, or Retired
- Design status: Adequate, Partial, Inadequate, or Not Assessed
- Operating effectiveness: Effective, Partially Effective, Ineffective, Not Tested, or Unknown
- Required evidence, evidence owner, source location, retention period, and review cadence
- Test method, test frequency, sample or metric, and pass criteria
- Exceptions, compensating controls, residual risk, and approval authority
- Dependencies, target date, priority, and remediation action

Evidence must demonstrate that a control is designed, performed, and effective. A policy document alone does not prove operation.

### 5. Produce the control matrix

Use these canonical columns in this order:

| Field | Required content |
|---|---|
| Control ID | Stable identifier such as `AI-CTRL-001` |
| Control Domain | Governance, Privacy, Security, Data, Model, Human Oversight, Third Party, Operations, or Lifecycle |
| Control Objective | Risk or outcome the control addresses |
| Control Statement | Specific behavior or requirement |
| Risk / Obligation | Linked risk, harm, legal duty, or business requirement |
| Owner | Accountable role |
| Lifecycle Stage | Relevant AI lifecycle stage(s) |
| NIST AI RMF | GOVERN, MAP, MEASURE, or MANAGE mapping and rationale |
| ISO/IEC 42001 | Clause or process mapping, edition, and rationale |
| ISO/IEC 27001 | Requirement or Annex A mapping, edition, and rationale |
| UK GDPR | Applicable principle, right, role, or obligation and rationale |
| ICO Guidance | Specific guidance source, topic, date/version, and rationale |
| OWASP GenAI | Applicable risk or mitigation and rationale, or Not Applicable |
| Applicability | Applicable, Partially Applicable, Not Applicable, or To Be Confirmed |
| Mapping Strength | Direct, Partial, Supporting, or None |
| Implementation Status | Not Started, Planned, In Progress, Implemented, or Retired |
| Control Effectiveness | Effective, Partially Effective, Ineffective, Not Tested, or Unknown |
| Evidence | Evidence required or available |
| Test Method | How operation and effectiveness are assessed |
| Gap / Finding | Missing or deficient element |
| Treatment / Action | Remediation or accepted treatment |
| Due Date / Cadence | Target date or review frequency |
| Status | Open, In Progress, Accepted, Blocked, Monitoring, Closed, or Retired |

For readability, split the matrix into domain-specific tables or separate source-mapping tables when the full matrix becomes too wide. Do not drop the canonical fields; preserve them in an exportable version.

### 6. Analyze coverage and gaps

Summarize:

- Controls mapped to multiple sources and the common evidence they can support
- Framework-specific requirements with no equivalent control
- Controls that exist only on paper or lack operating evidence
- Risks or obligations without an owner or treatment
- Third-party, generative-AI, privacy, human-rights, fairness, and lifecycle gaps
- Duplicate controls that can be consolidated without losing obligations
- Applicability decisions requiring legal, privacy, security, audit, or certification review

Do not report a high mapping count as high maturity. Explain the difference between coverage, implementation, effectiveness, and assurance.

### 7. Create the remediation roadmap

Prioritize gaps using risk severity, legal or contractual urgency, harm reversibility, affected stakeholders, risk tolerance, implementation effort, and dependency order. For each action, include the control IDs, accountable owner, target date, evidence of completion, validation method, and residual risk.

Where a control supports several sources, identify the shared implementation benefit. Where one source has a stricter or different requirement, preserve the source-specific action.

## Default Output

Unless the user requests another format, produce:

1. **Executive summary and decision requested**
2. **Scope, assumptions, framework editions, and authority hierarchy**
3. **Control matrix**
4. **Coverage, applicability, and evidence analysis**
5. **Priority gaps and residual risks**
6. **Remediation roadmap**
7. **Specialist review and approval requirements**

## Quality Gate

Before finalizing, verify:

- Every control has a stable ID, objective, statement, owner, applicability, and status.
- Each framework mapping includes a rationale or an explicit `Not Applicable` or `To Be Confirmed` decision.
- ISO/IEC 42001 and ISO/IEC 27001 editions are stated and clause/control references are not fabricated.
- UK GDPR mappings are tied to actual processing facts and do not overstate legal conclusions.
- ICO sources include identifiable titles or topics and current date/version information where available.
- OWASP GenAI mappings are used only where the architecture and threat model make them relevant.
- Design, implementation, operating effectiveness, evidence, and assurance are reported separately.
- Third-party, lifecycle, monitoring, incident, and decommissioning controls are considered.
- Gaps have owners, actions, due dates or cadence, validation criteria, and residual-risk decisions.
- The matrix distinguishes mandatory requirements from voluntary frameworks and guidance.
- Sensitive information is minimized and specialist review is clearly flagged.
