---
name: ai-assurance
description: 'Generate an AI Assurance Plan that demonstrates governance operates in practice through evidence, control testing, metrics, independent review, findings, and decision gates. Use for AI assurance planning, control effectiveness, audit readiness, model validation, monitoring, release approval, and ongoing governance.'
argument-hint: '[AI system, governance scope, assurance objective, or decision gate]'
user-invocable: true
disable-model-invocation: false
---

# AI Assurance

## Purpose

Generate a practical **AI Assurance Plan** that demonstrates governance is operating, not merely documented. Convert policies, risks, controls, and accountability into observable assurance activities with named owners, evidence, test methods, pass criteria, cadence, independent challenge, remediation, and decisions.

Apply assurance across the NIST AI RMF functions:

- **GOVERN**: assure that accountability, authority, policy, risk tolerance, and oversight operate as designed.
- **MAP**: assure that system purpose, context, stakeholders, benefits, impacts, harms, data, dependencies, and lifecycle boundaries are understood.
- **MEASURE**: test trustworthy-AI characteristics, risks, controls, performance, uncertainty, and evidence quality.
- **MANAGE**: assure that findings lead to treatment, residual-risk decisions, monitoring, escalation, pause, or retirement.

This skill is an assurance-planning aid. It does not certify compliance, replace independent audit, or provide legal, regulatory, privacy, security, safety, or domain advice.

## When to Use

Use this skill for:

- AI Assurance Plans and annual assurance calendars
- Pre-deployment and release-gate assurance
- Model validation, red teaming, safety evaluation, and fairness testing
- AI control effectiveness and evidence reviews
- ISO/IEC 42001, ISO/IEC 27001, NIST AI RMF, UK GDPR, ICO, or OWASP assurance preparation
- Third-party AI vendor assurance and contract evidence reviews
- Operational monitoring, incident assurance, and management review
- Remediation verification and residual-risk acceptance

## Assurance Principles

- Start from risks, harms, obligations, and decisions, not from a document inventory.
- Test whether controls are designed, implemented, performed, and effective.
- Use evidence that is current, attributable, reproducible, complete, and appropriate to the risk.
- Separate first-line control ownership, second-line oversight, and independent third-line assurance where those roles exist.
- Independence must be proportionate to risk; the control owner should not be the sole reviewer of their own evidence for material risks.
- A completed checklist is not assurance. Require observable results, samples, metrics, test records, or independent challenge.
- Report uncertainty, limitations, sampling boundaries, and untested areas explicitly.
- Do not treat model accuracy or uptime alone as evidence of trustworthy AI.
- Link every finding to an owner, due date, severity, remediation, retest, and decision authority.
- Escalate risks that exceed tolerance, involve irreversible harm, affect vulnerable groups, or lack sufficient evidence for approval.

## Procedure

### 1. Define the assurance objective and decision

Capture:

- AI system, use case, model, vendor, version, and lifecycle stage
- Assurance objective: design approval, pre-deployment, release, operation, renewal, incident, or retirement
- Decision enabled: approve, continue, restrict, pause, remediate, accept residual risk, or retire
- Scope, exclusions, jurisdictions, affected people, vulnerable groups, and downstream users
- Risk tolerance, materiality, applicable obligations, and required independence
- Assurance sponsor, accountable risk owner, control owners, testers, reviewers, and approval authority
- Review period, evidence cutoff, reporting date, and next reassessment trigger

If the decision, scope, or tolerance is unclear, ask a focused question. Otherwise state assumptions and identify the decision that remains conditional on evidence.

### 2. Establish the assurance universe

Build an assurance universe from:

- AI risks, harms, benefits, and risk-register items
- NIST AI RMF GOVERN, MAP, MEASURE, and MANAGE outcomes
- AI policies, control matrices, contractual obligations, and regulatory requirements
- Trustworthy-AI characteristics: validity, reliability, safety, security, resilience, accountability, transparency, explainability, interpretability, privacy, fairness, and harmful-bias management
- Data, model, system, human-oversight, third-party, operational, and lifecycle controls
- Previous findings, incidents, complaints, appeals, near misses, changes, and accepted exceptions

Prioritize assurance effort using risk severity, likelihood, potential harm, affected stakeholders, uncertainty, change, control criticality, and ability to detect or reverse failure.

### 3. Design assurance activities

For each priority risk or control, define an activity that answers:

- **Assurance objective**: what must be true
- **Risk or control reference**: linked risk, harm, obligation, or control ID
- **Test procedure**: how the claim will be examined
- **Evidence**: exact record, dataset, log, configuration, interview, sample, metric, or independent report required
- **Population and sample**: what is covered and how samples are selected
- **Pass criteria**: measurable threshold or decision rule
- **Assurance method**: inspection, inquiry, observation, reperformance, technical test, simulation, red team, audit, validation, or independent review
- **Performer and reviewer**: responsible roles and independence level
- **Cadence and trigger**: scheduled frequency and events requiring an out-of-cycle review
- **Limitations**: known blind spots, unavailable data, vendor dependencies, or sampling limits
- **Output**: evidence record, score, finding, opinion, recommendation, or decision input

Use multiple methods for material controls. A policy inspection should be supplemented by evidence of operation; an interview should not be the sole basis for a high-risk conclusion.

### 4. Cover operational reality

Include assurance activities that test whether governance works in the live environment:

- Approved use matches actual use, users, data, decisions, and system configuration
- Human reviewers understand responsibilities, can challenge outputs, and actually intervene
- Access, identity, segregation of duties, logging, and privileged activity operate as intended
- Data quality, provenance, retention, deletion, and training-use restrictions are enforced
- Model performance, drift, calibration, safety, fairness, privacy, security, and explainability remain within thresholds
- Monitoring alerts reach owners, incidents are triaged, and corrective actions are completed
- Vendor changes, subprocessors, outages, harmful outputs, complaints, and regulatory changes trigger reassessment
- Rollback, degraded operation, suspension, communication, and exit procedures work in exercises
- Benefits are measured and remain proportionate to residual risks and harms

### 5. Build the AI Assurance Plan

Use one row per assurance activity. Include these canonical fields:

| Field | Required content |
|---|---|
| Assurance ID | Stable identifier such as `AI-ASR-001` |
| Assurance Domain | Governance, Data, Model, Security, Privacy, Human Oversight, Third Party, Operations, or Lifecycle |
| Assurance Objective | What must be demonstrated |
| Risk / Control Reference | Linked risk, control, obligation, or decision |
| NIST AI RMF Function | GOVERN, MAP, MEASURE, or MANAGE |
| Control / Claim Being Assured | Specific control or claim under review |
| Test Method | Inspection, inquiry, observation, reperformance, technical test, simulation, red team, audit, or validation |
| Evidence Required | Records, metrics, samples, configurations, logs, reports, or artifacts |
| Population / Sample | Scope and sampling approach |
| Pass Criteria | Threshold or decision rule |
| Performer | Accountable assurance performer |
| Independent Reviewer | Reviewer and independence level |
| Cadence / Trigger | Planned frequency and change or incident triggers |
| Owner | Control or risk owner responsible for response |
| Status | Planned, In Progress, Complete, Blocked, Deferred, or Retired |
| Result | Pass, Pass with Observation, Fail, Inconclusive, or Not Tested |
| Finding / Limitation | Defect, uncertainty, scope limit, or exception |
| Remediation / Decision | Action, acceptance, restriction, pause, or retirement decision |
| Due Date / Retest | Target date and verification activity |

### 6. Define assurance reporting and decision gates

Set clear gates appropriate to the lifecycle:

- **Design gate**: purpose, risks, stakeholders, controls, data, and assurance approach are defined.
- **Build gate**: required tests, security, privacy, safety, fairness, and documentation evidence is available.
- **Pre-deployment gate**: critical findings are closed or formally accepted by the authorized owner; residual risk is within tolerance.
- **Change gate**: material model, data, provider, user, feature, or context changes are reassessed before release.
- **Operate gate**: monitoring, incidents, complaints, control performance, and benefits support continuation.
- **Pause gate**: thresholds, evidence failures, incidents, or harmful impacts trigger restriction or suspension.
- **Retirement gate**: data, access, decisions, records, contracts, dependencies, and downstream effects are safely closed.

For every gate, state required evidence, approver, non-negotiable conditions, exceptions, and what happens when the gate fails.

### 7. Manage findings and continual improvement

Classify findings by severity and decision impact. For each finding record:

- Condition, cause, consequence, affected stakeholders, and evidence
- Severity, uncertainty, risk tolerance, and whether immediate containment is required
- Accountable owner, corrective action, target date, dependencies, and success measure
- Interim compensating control or use restriction
- Retest method, closure evidence, reviewer, and closure authority
- Whether the finding requires policy, control, contract, model, training, monitoring, or lifecycle change

Track recurring findings, overdue actions, ineffective controls, repeated exceptions, and areas where assurance cannot obtain evidence. Feed results into the risk register, control matrix, management review, vendor review, and next assurance plan.

## Default Output

Unless another format is requested, produce:

1. **Assurance conclusion and decision requested**
2. **System, scope, risk tolerance, and assurance objectives**
3. **Assurance universe and priority rationale**
4. **AI Assurance Plan**
5. **Decision gates and approval conditions**
6. **Evidence catalogue and evidence-quality assessment**
7. **Open findings, remediation, and retest plan**
8. **Operational monitoring and reassessment triggers**
9. **Independent assurance and specialist-review requirements**

## Quality Gate

Before finalizing, verify:

- The plan enables a named decision and identifies the approval authority.
- Every material risk or critical control has an assurance objective, test method, evidence, pass criteria, owner, cadence, and result.
- Tests cover operation in practice, not only policy existence.
- Evidence is current, attributable, reproducible, and sufficient for the risk.
- Independence and reviewer competence are proportionate to risk.
- Sampling, limitations, uncertainty, and untested areas are visible.
- Trustworthy-AI characteristics and real-world impacts are tested where relevant.
- Findings have severity, owners, due dates, remediation, retest, and closure authority.
- Release, continuation, change, pause, and retirement gates are explicit.
- Monitoring, incidents, third parties, human oversight, and decommissioning are included where relevant.
- Residual risk is within tolerance or formally accepted by an authorized owner.
- The plan demonstrates what governance does, who does it, what evidence proves it, and what happens when it fails.
