# SentinelAI Governance Project Rules

## Purpose

This repository is an **AI Governance Portfolio** demonstrating practical AI governance capability in a UK enterprise context. Use **NIST AI Risk Management Framework 1.0** as the primary risk-management framework. Produce evidence-based, decision-ready outputs that help an organisation govern AI systems across their full lifecycle. Governance must demonstrate accountability and effective action, not merely generate paperwork.

## Framework Hierarchy

Use NIST AI RMF 1.0 as the primary framework, with these supporting sources where relevant:

- ISO/IEC 42001
- ISO/IEC 27001
- UK GDPR
- Data Protection Act 2018
- ICO AI and data-protection guidance
- OWASP GenAI Security guidance
- NIST Cybersecurity Framework where appropriate

Distinguish legal and regulatory duties, contractual obligations, certifiable management-system requirements, voluntary frameworks, regulator guidance, and security best practices. State the edition, version, publication date, and source when mapping to a framework or guidance document.

## Core Operating Model

Apply the NIST AI Risk Management Framework functions consistently:

- **GOVERN**: establish accountability, decision rights, policy, risk tolerance, oversight, resources, and escalation.
- **MAP**: define purpose, intended use, context, stakeholders, benefits, impacts, harms, dependencies, data, and lifecycle boundaries.
- **MEASURE**: evaluate trustworthy-AI characteristics, risks, controls, evidence, performance, uncertainty, and real-world outcomes.
- **MANAGE**: prioritize treatment, assign owners, monitor residual risk, handle change and incidents, and govern restriction, suspension, or retirement.

Use the functions as a continuous loop. Re-enter MAP and MEASURE after material changes to the system, data, model, vendor, users, purpose, or operating environment.

## Governance Principles

AI governance must be:

- Risk-based
- Proportionate
- Evidence-based
- Auditable
- Transparent
- Accountable
- Human-centred

## Evidence and Reasoning

- Label material statements as **Evidence**, **Assumption**, **Recommendation**, or **Unknown**. Stakeholder and vendor claims must remain clearly identified until verified.
- Never invent evidence, test results, approvals, certifications, regulatory decisions, or organisational facts.
- Never claim a control is effective because a policy, certificate, questionnaire, or framework mapping exists.
- Trace material claims to current evidence, an owner, a decision, and a review date.
- Record evidence scope, date, confidence, limitations, and what would change the conclusion.
- Do not silently resolve contradictory documents. Identify both sources, determine the authoritative record, and state the required resolution.
- Treat missing evidence as a finding when it affects risk, safety, privacy, security, compliance, or approval.
- Avoid false precision in risk scores. Explain the method, uncertainty, affected stakeholders, and risk-tolerance decision.

Always distinguish **inherent risk**, **controls**, and **residual risk**. Show how residual risk compares with documented risk tolerance and who is authorised to accept it.

## AI Lifecycle

Consider and document the following lifecycle stages where relevant:

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

## Governance Deliverables

For assessments, policies, registers, control matrices, assurance plans, vendor reviews, incident records, and governance reviews:

- State the decision requested near the beginning.
- Identify scope, exclusions, audience, date, lifecycle stage, jurisdiction, and assumptions.
- Write for an enterprise AI Governance function using clear tables where appropriate.
- Use British English in prose and labels, including `organisation`, `authorised`, `prioritise`, and `centre`.
- Name accountable owners, approval authority, review cadence, and escalation route.
- Address benefits as well as risks, impacts, harms, vulnerable groups, and routes to recourse.
- Make controls actionable: objective, owner, trigger, procedure, evidence, test method, threshold, exception path, and residual risk.
- Give recommendations a priority, dependency, due date or cadence, success measure, and verification method.
- Distinguish design adequacy, implementation, operating effectiveness, and independent assurance.
- Include monitoring, incidents, change management, third parties, human oversight, and decommissioning where relevant.
- Flag when qualified legal, privacy, security, safety, audit, accessibility, regulatory, or domain-specialist review is required.

Every major governance decision must include:

- Owner
- Rationale
- Evidence
- Date
- Review date
- Status

## Document Consistency

When reviewing multiple governance artefacts, reconcile:

- Risk IDs, descriptions, categories, likelihood, impact, inherent risk, residual risk, and tolerance.
- Owners, approval authorities, statuses, dates, model or vendor versions, and lifecycle states.
- DPIAs, data maps, retention and transfer records, vendor terms, policies, control matrices, assurance results, incidents, and retirement records.

Flag examples such as a risk register stating that a DPIA is complete while the DPIA remains Draft, or a control marked Effective without supporting test evidence.

## AI Assurance

Assurance plans must prove governance operates in practice. Each material assurance activity should specify:

- Assurance objective and linked risk or control
- Test method, population or sample, evidence, and pass criteria
- Performer, independent reviewer, cadence, trigger, and limitations
- Result, finding, remediation, owner, due date, retest, and closure authority

Use decision gates for design, build, pre-deployment, material change, operation, pause, and retirement. Do not treat accuracy or uptime alone as evidence of trustworthy AI.

## Third-Party AI

Treat vendors, model providers, subprocessors, fourth parties, data suppliers, integrators, open-source components, and downstream users as part of the risk boundary where relevant. Assess data processing, retention, model training, location, subprocessors, security, encryption, identity, access, incident management, availability, resilience, IP, confidentiality, audit rights, regulatory compliance, model changes, and exit strategy.

Separate vendor assertions from independent assurance and customer validation. Require measurable, testable, enforceable contract controls and an exit plan.

## Incident Handling

For AI incidents, prioritize protection of people and evidence:

1. Detect, record, classify, and escalate.
2. Assign authority and specialist roles.
3. Map affected systems, data, stakeholders, harms, and dependencies.
4. Preserve evidence with integrity, access control, retention, and legal-hold considerations.
5. Contain unsafe behavior and provide support or recourse.
6. Assess notification obligations with qualified specialists.
7. Remediate, test, recover, and authorize restart, restriction, pause, or retirement.
8. Update risks, controls, assurance, vendor oversight, monitoring, and lifecycle decisions.

## Framework and Regulatory Use

Distinguish mandatory law, contractual obligations, certifiable management-system requirements, voluntary frameworks, regulator guidance, and security best practices. Do not invent clause numbers, legal conclusions, regulatory requirements, or source references. State the framework edition and source date when mapping to NIST AI RMF, ISO/IEC 42001, ISO/IEC 27001, UK GDPR, ICO guidance, or OWASP GenAI guidance.

This project does not provide legal advice or certify compliance.

## File and Editing Rules

- Keep changes focused and preserve existing style and public interfaces.
- Do not rewrite unrelated user changes or metadata.
- Prefer small, reviewable edits and validate after each substantive change.
- Use ASCII by default unless the existing file clearly requires other characters.
- Avoid comments that merely narrate obvious code.
- Do not add credentials, secrets, personal data, or unnecessary sensitive information.
- Do not commit or create branches unless explicitly requested.
- For diagrams, follow `.github/instructions/mermaid.instructions.md`; validate Mermaid syntax before presenting it and preview generated diagrams.

## Completion Standard

A task is complete only when the requested outcome is produced, material assumptions and limitations are visible, owners and next steps are explicit, relevant evidence or validation has been checked, and the result states what decision or approval is required. Major decisions must include an owner, rationale, evidence, date, review date, and status.


## Language
Ensure to use British English language 