---
name: ai-incident
description: 'Manage AI incidents through a structured response workflow covering detection, triage, containment, harm assessment, evidence preservation, notification, recovery, remediation, and lessons learned. Use for harmful outputs, privacy breaches, security events, safety failures, bias incidents, model drift, vendor incidents, and AI governance escalations.'
argument-hint: '[AI incident, alert, harmful output, breach, failure, or suspected event]'
user-invocable: true
disable-model-invocation: false
---

# AI Incident

## Purpose

Manage an AI incident from detection through closure while protecting people, preserving evidence, restoring safe operation, and improving governance. Treat an incident as a governance event when AI behavior, data, controls, vendor operation, or human oversight creates actual or potential harm, loss of control, legal exposure, or material deviation from approved use.

Use the NIST AI RMF functions throughout:

- **GOVERN**: establish incident authority, roles, escalation, communications, and decision rights.
- **MAP**: understand the affected system, context, users, data, stakeholders, dependencies, and potential harms.
- **MEASURE**: assess severity, scope, likelihood of recurrence, evidence quality, and control failure.
- **MANAGE**: contain, remediate, recover, communicate, monitor, and decide whether to continue, restrict, pause, or retire the system.

This skill supports incident coordination and documentation. It does not determine legal notification duties or replace qualified privacy, security, legal, safety, regulatory, or law-enforcement advice.

## Incident Types

Classify one or more types:

- Harmful, unsafe, discriminatory, misleading, or materially inaccurate output
- Privacy breach, personal-data exposure, confidentiality loss, or unauthorized retention
- Security compromise, prompt injection, data exfiltration, malicious tool use, or supply-chain event
- Model drift, performance degradation, monitoring failure, or out-of-scope behavior
- Human-oversight failure, automation bias, unauthorized decision, or inability to provide recourse
- Availability, resilience, outage, rollback, or vendor service failure
- Intellectual-property, licensing, regulatory, contractual, or reputational event
- Third-party, subprocessor, model-provider, or downstream incident

## Procedure

### 1. Detect, record, and triage

Create an incident record immediately with:

- Incident ID, reporter, detection time, current status, and confidentiality classification
- Affected AI system, model or vendor, version, environment, use case, and owner
- Initial description, observed behavior, trigger, evidence location, and known uncertainty
- Whether the event is an incident, near miss, control failure, complaint, or suspected event
- Immediate safety, privacy, security, operational, legal, and human-impact concerns

Triage severity using impact, number and vulnerability of affected people, duration, reversibility, likelihood of recurrence, regulatory or contractual exposure, and whether the system is still operating. Escalate immediately where there is active harm, sensitive-data exposure, material security compromise, high-impact decision impact, or risk beyond tolerance.

### 2. GOVERN the response

Assign:

- Incident commander and accountable executive or risk owner
- Technical, security, privacy, legal, safety, communications, vendor, and domain specialists
- Decision authority for containment, notification, restart, risk acceptance, suspension, and retirement
- Stakeholder communication owner and need-to-know access controls
- Regulatory, customer, supplier, insurer, law-enforcement, or affected-person liaison where relevant

Record decisions, timestamps, rationale, dissent, approvals, and escalation. Do not let commercial pressure override safety, privacy, legal, or affected-person considerations.

### 3. MAP scope, harm, and dependencies

Determine:

- What happened, where, when, and under which version or configuration
- Which data, prompts, outputs, records, models, tools, users, and downstream systems were involved
- Directly and indirectly affected people, vulnerable groups, customers, employees, communities, and third parties
- Actual harm, potential harm, benefits lost, rights affected, and routes to support or recourse
- Whether the event is isolated or systemic across products, tenants, regions, or providers
- Vendor, subprocessor, open-source, integration, and supply-chain dependencies
- Whether similar incidents, complaints, near misses, or control exceptions exist

Use verified facts, reported information, assumptions, and unknowns as separate labels.

### 4. MEASURE and preserve evidence

Preserve evidence before changing the system where safe to do so:

- Prompts, inputs, outputs, model and system versions, configurations, policies, and feature flags
- Access, identity, audit, application, security, monitoring, and vendor logs
- Data lineage, retention, deletion, training-use, and transfer records
- User reports, complaints, appeals, screenshots, test results, evaluation data, and communications
- Timeline, commands, changes, decisions, controls invoked, and attempted interventions

Maintain chain of custody, time source, evidence owner, integrity protection, retention or legal-hold requirements, and access restrictions. Avoid collecting unnecessary personal or sensitive data.

Assess:

- Scope and severity of actual and plausible harm
- Control performance and failure points
- Model validity, reliability, safety, security, privacy, fairness, transparency, and human-oversight effects
- Probability of recurrence and whether the failure can be detected or reversed
- Whether the incident indicates a broader risk-register, vendor, policy, or assurance gap

### 5. Contain and protect people

Choose proportionate containment:

- Stop unsafe actions, disable tools, revoke access, isolate data, or restrict users and use cases
- Add human review, reduce autonomy, block prompts or outputs, switch to a safe fallback, or roll back a release
- Pause the model, vendor service, integration, or affected decision process
- Protect affected people through communication, correction, support, appeal, remediation, and access to a human decision-maker

Record containment criteria and test that containment worked. Do not restore service solely because the immediate symptom disappeared.

### 6. Notify and communicate

Assess notification requirements and stakeholder needs with qualified specialists. Consider:

- Supervisory authorities, regulators, customers, affected people, suppliers, insurers, and law enforcement
- Contractual notification windows, evidence obligations, and cross-border requirements
- What happened, what is known and unknown, affected scope, actions taken, risks, support, and next steps
- Avoiding speculation, blame, unnecessary sensitive details, and misleading reassurance

Document the decision to notify or not notify, the authority consulted, timing, content approval, and follow-up commitments.

### 7. Remediate, recover, and verify

Identify root and contributing causes across model, data, code, configuration, vendor, process, policy, training, and human factors. Define corrective actions with owners, due dates, dependencies, success criteria, and evidence.

Before resuming operation:

- Confirm containment and corrective changes through testing or independent review
- Reassess risks, harms, affected groups, residual risk, and risk tolerance
- Validate monitoring, alerting, rollback, human oversight, and incident playbooks
- Confirm contractual or vendor remediation and assurance evidence
- Obtain the authorized restart, restricted-use, or retirement decision

### 8. Close and learn

Close only when harm response, notifications, evidence, corrective actions, residual risk, and approvals are complete or formally accepted. Produce a post-incident review covering timeline, impact, response effectiveness, control failures, missed signals, lessons, and recurring patterns.

Update the risk register, control matrix, assurance plan, vendor assessment, training, policies, monitoring thresholds, and decommissioning criteria. Track actions until independently verified.

## Default Output

Unless another format is requested, produce:

1. **Incident summary and current severity**
2. **Immediate safety, privacy, security, and operational actions**
3. **Incident roles, authority, and communications**
4. **Scope, affected stakeholders, harms, and dependencies**
5. **Evidence register and timeline**
6. **Containment, notification, remediation, and recovery plan**
7. **Restart, restriction, pause, or retirement decision**
8. **Root cause, control failures, and residual risk**
9. **Post-incident actions, owners, due dates, and verification**

## Quality Gate

Before finalizing, verify:

- The incident has an ID, owner, severity, status, decision authority, and next action.
- Active harm and high-risk exposure are escalated and contained.
- Actual and potential harms, affected people, vulnerable groups, and recourse are considered.
- Evidence is preserved with integrity, access control, retention, and legal-hold considerations.
- Facts, reports, assumptions, and unknowns are distinguished.
- Notification decisions are documented and specialist review is identified.
- Recovery is conditional on tested remediation, monitoring, and authorized approval.
- Root causes include technical, data, vendor, process, policy, and human factors where relevant.
- Lessons update risks, controls, assurance, vendor oversight, and lifecycle decisions.
