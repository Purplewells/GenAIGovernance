---
name: ai-governance-review
description: 'Conduct a structured AI governance review to test whether governance is current, effective, risk-proportionate, and operating in practice. Use for periodic governance reviews, management reviews, NIST AI RMF assessments, ISO/IEC 42001 readiness, policy reviews, control maturity, and improvement planning.'
argument-hint: '[AI governance scope, review period, system portfolio, or decision]'
user-invocable: true
disable-model-invocation: false
---

# AI Governance Review

## Purpose

Conduct a structured review of whether an organization’s AI governance is working in practice. Evaluate not only whether policies and committees exist, but whether people make accountable decisions, controls operate, evidence is available, risks are managed, affected stakeholders have recourse, and governance changes outcomes.

Apply the NIST AI RMF functions as a continuous operating model:

- **GOVERN**: review accountability, policy, culture, roles, authority, resources, and risk tolerance.
- **MAP**: review whether the AI inventory, context, purpose, stakeholders, benefits, impacts, harms, dependencies, and lifecycle boundaries are understood.
- **MEASURE**: review evidence, trustworthy-AI evaluations, control effectiveness, monitoring, incidents, and uncertainty.
- **MANAGE**: review prioritization, treatment, residual-risk decisions, escalation, change, suspension, and retirement.

This skill supports governance review and improvement. It does not certify compliance or replace legal, privacy, security, audit, safety, accessibility, or domain-specialist advice.

## When to Use

Use this skill for:

- Periodic AI governance and management reviews
- AI governance maturity and effectiveness assessments
- NIST AI RMF GOVERN, MAP, MEASURE, and MANAGE reviews
- ISO/IEC 42001 readiness or continual-improvement reviews
- AI policy, committee, risk appetite, and operating-model reviews
- Portfolio, use-case inventory, vendor, assurance, and incident governance reviews
- Pre-audit, post-incident, post-change, and annual governance evaluations

## Review Principles

- Test governance outcomes and decisions, not only the existence of documents.
- Sample real AI use cases, approvals, incidents, controls, monitoring records, and decisions.
- Separate design adequacy, implementation, operating effectiveness, and assurance.
- Look for evidence of challenge, escalation, dissent, exceptions, and learning.
- Evaluate whether governance is proportionate to risk and impact, including vulnerable groups.
- Identify paper controls, stale inventories, duplicate forums, unclear accountability, and unowned residual risk.
- Distinguish verified evidence, stakeholder claims, assumptions, and unknowns.
- Avoid maturity theatre: a higher process score is not improvement unless it reduces risk or improves accountable outcomes.
- Make recommendations actionable with owners, measures, due dates, dependencies, and verification.

## Procedure

### 1. Frame the review

Define:

- Review objective, audience, decision required, and review period
- Organizational, portfolio, system, vendor, geography, and lifecycle scope
- AI inventory population and sampling approach
- Applicable laws, contracts, standards, policies, risk tolerance, and assurance commitments
- Review team, independence, specialist skills, interviewees, and approval authority
- Known incidents, changes, audit findings, complaints, exceptions, and priority concerns

State exclusions, evidence cutoff, limitations, and assumptions. Ask a focused question if scope or decision authority is materially unclear.

### 2. Review GOVERN

Assess whether governance has:

- A current AI strategy, policy hierarchy, prohibited-use position, and risk appetite
- Clear accountability, decision rights, escalation, approval, and residual-risk acceptance
- Competent and sufficiently independent oversight with adequate resources
- A complete AI inventory, use-case classification, lifecycle ownership, and change control
- Effective procurement, third-party, data, security, privacy, safety, fairness, and human-oversight requirements
- Training, incentives, speak-up routes, protection from retaliation, and management attention
- Records, reporting, committee terms, management review, audit, exceptions, and corrective action

Test decisions and minutes, not just terms of reference. Look for evidence that governance can stop, restrict, or retire an AI system.

### 3. Review MAP

Assess whether the organization can explain for sampled systems:

- Purpose, intended use, alternatives, users, affected people, vulnerable groups, and operating context
- Benefits, impacts, harms, foreseeable misuse, out-of-scope use, and routes to recourse
- Data sources, provenance, quality, rights, retention, location, and downstream use
- Model, system, vendor, subprocessor, open-source, and integration dependencies
- Lifecycle stage, decision authority, human oversight, fallback, monitoring, and retirement plan

Compare approved documentation with actual configurations, workflows, users, and observed use.

### 4. Review MEASURE

Evaluate whether the organization measures and evidences:

- Validity, reliability, accuracy, calibration, robustness, drift, and limitations
- Safety, resilience, security, privacy, fairness, harmful bias, transparency, explainability, and interpretability
- Human factors, automation bias, contestability, accessibility, complaints, appeals, and affected-person outcomes
- Control design and operating effectiveness, including third-party controls
- Monitoring quality, thresholds, alert response, incident trends, near misses, and unresolved uncertainty
- Benefits and positive outcomes alongside risks and harms

Sample test results, logs, metrics, evaluations, red-team work, assurance reports, incident records, and remediation evidence. Check whether measures are decision-relevant rather than merely convenient.

### 5. Review MANAGE

Assess whether governance reliably turns evidence into action:

- Risks are prioritized against documented tolerance and affected-person impact
- Controls and treatments have accountable owners, due dates, evidence, and verification
- Exceptions are time-bound, approved, visible, and not becoming permanent workarounds
- Material changes trigger reassessment before release or continued operation
- Incidents trigger containment, notification assessment, root-cause analysis, remediation, and learning
- Vendors and subprocessors are monitored, challenged, and subject to enforceable remedies
- Systems can be restricted, paused, rolled back, transitioned, or decommissioned safely
- Management reviews outcomes, recurring findings, resource needs, and changes to risk appetite

### 6. Sample and gather evidence

Use a risk-based sample across lifecycle stages, business areas, risk categories, vendors, and system types. Request:

- Policies, standards, roles, committee records, decisions, exceptions, and training records
- AI inventory, use-case assessments, risk registers, impact assessments, system cards, and model documentation
- Data and model evaluations, monitoring dashboards, logs, test results, assurance plans, and audit reports
- Contracts, vendor assessments, subprocessors, incidents, complaints, appeals, and communications
- Change records, release approvals, rollback exercises, continuity tests, retirement records, and lessons learned

For each evidence item, record owner, date, scope, source, confidence, limitation, and whether it demonstrates design, operation, or effectiveness.

### 7. Rate findings and governance effectiveness

Classify findings as Critical, High, Moderate, Low, Observation, or Good Practice. Explain the rating based on risk, harm, likelihood, control failure, uncertainty, affected stakeholders, and urgency. Do not assign a maturity level without evidence.

For each finding record:

- Condition and expected practice
- Evidence and confidence
- Cause and consequence
- Affected stakeholders and benefits or harms at stake
- NIST AI RMF function and related control or obligation
- Severity, risk tolerance, and whether immediate action is required
- Owner, corrective action, target date, measure of success, and verification method

### 8. Produce the governance review report and improvement plan

Unless another format is requested, include:

1. **Executive conclusion and decision requested**
2. **Scope, methodology, sample, limitations, and review period**
3. **Govern, Map, Measure, and Manage findings**
4. **Evidence and effectiveness assessment**
5. **Strengths and good practices**
6. **Priority findings and residual risks**
7. **AI governance improvement plan**
8. **Metrics, management actions, and review cadence**
9. **Required specialist review and next reassessment trigger**

Use an improvement-plan table with:

| Field | Required content |
|---|---|
| Action ID | Stable identifier such as `AI-GOV-ACT-001` |
| Finding / Risk | Linked finding, risk, harm, or obligation |
| NIST AI RMF Function | GOVERN, MAP, MEASURE, or MANAGE |
| Action | Specific improvement |
| Owner | Accountable role |
| Priority | Critical, High, Moderate, or Low |
| Success Measure | Observable outcome or metric |
| Evidence of Completion | Record, test, decision, or result |
| Due Date | Target completion date |
| Verification | Reviewer and retest method |
| Status | Open, In Progress, Blocked, Accepted, Verified, or Closed |

## Quality Gate

Before finalizing, verify:

- The review tests actual decisions, control operation, and outcomes, not only paperwork.
- Scope, sample, evidence cutoff, independence, limitations, and assumptions are explicit.
- GOVERN, MAP, MEASURE, and MANAGE are each assessed with evidence and findings.
- AI inventory, third parties, incidents, monitoring, human oversight, change, and retirement are considered.
- Benefits, impacts, harms, vulnerable groups, recourse, and residual risk are addressed.
- Findings distinguish missing design, poor implementation, ineffective operation, and insufficient assurance.
- Every material finding has an owner, action, success measure, due date, verification method, and status.
- Recommendations are proportionate, measurable, and tied to risk or governance outcomes.
- The report states the decisions, approvals, resources, specialist reviews, and next reassessment trigger required.
