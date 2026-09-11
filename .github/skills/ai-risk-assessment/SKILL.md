---
name: ai-risk-assessment
description: 'Generate a structured AI risk assessment and risk register using NIST AI RMF GOVERN, MAP, MEASURE, and MANAGE. Use for AI use-case reviews, model risk assessments, trustworthy AI analysis, impact assessments, control reviews, risk registers, and deployment or lifecycle decisions.'
argument-hint: '[AI system, use case, assessment scope, or risk question]'
user-invocable: true
disable-model-invocation: false
---

# AI Risk Assessment

## Purpose

Generate a decision-ready AI risk assessment and a structured risk register. Apply the NIST AI RMF functions consistently:

- **GOVERN**: establish accountability, roles, policies, risk tolerance, approval rights, and escalation paths.
- **MAP**: define the AI system, purpose, context, stakeholders, benefits, impacts, harms, dependencies, and lifecycle stage.
- **MEASURE**: evaluate evidence, trustworthy-AI characteristics, likelihood, impact, controls, and uncertainty.
- **MANAGE**: prioritize treatment, assign ownership, monitor residual risk, and decide whether to deploy, restrict, pause, or retire.

This skill produces governance analysis, not legal advice or a compliance certification. Flag where legal, privacy, security, safety, audit, accessibility, or domain-specialist review is required.

## Risk Categories

Select categories that are relevant to the system. Do not force every category into every assessment:

- Privacy
- Security
- Safety
- Fairness
- Bias
- Accuracy
- Reliability
- Transparency
- Explainability
- Accountability
- Legal/Regulatory
- Operational
- Third Party
- Reputational
- Human Factors

Add a more specific category when needed, and explain why it was added.

## Procedure

### 1. Frame the assessment

Establish or state assumptions for:

- Assessment objective and decision required
- AI system, model, service, feature, or proposed use case
- Scope, exclusions, jurisdictions, and assessment date
- Intended users, affected stakeholders, vulnerable groups, and downstream recipients
- Lifecycle stage: idea, design, development, validation, deployment, operation, change, suspension, or retirement
- Applicable laws, regulations, contracts, policies, standards, and risk criteria
- Risk tolerance, prohibited uses, approval authority, and escalation threshold

Ask a focused question when a missing fact could materially change the result. Otherwise continue with an explicit assumption and label it as such.

### 2. GOVERN and MAP the context

Document:

- Accountable risk owner and decision rights
- Business purpose, intended benefits, and alternatives to using AI
- Data sources, data subjects, providers, integrations, open-source components, and third parties
- Intended use, reasonably foreseeable misuse, out-of-scope use, and operating environment
- Potential positive impacts, negative impacts, harms, affected people, and routes to recourse
- Dependencies, human oversight, intervention points, and failure-handling paths

Treat providers, suppliers, integrators, and downstream users as part of the risk boundary. Identify information that is unavailable or controlled by a third party.

### 3. Build the evidence base

Use relevant repository files, system documentation, policies, data documentation, evaluations, test results, incident records, contracts, provider statements, interviews, and operational evidence. Do not infer that a control exists merely because it would be desirable.

Classify important claims as:

- **Verified**: supported by direct evidence
- **Reported**: provided by a stakeholder or supplier but not independently verified
- **Assumed**: used to continue the assessment pending confirmation
- **Unknown**: evidence is missing or contradictory

For material findings, record the evidence source, confidence, limitation, and what would change the conclusion.

### 4. MEASURE risks and controls

Assess trustworthy-AI characteristics relevant to the use case:

- Validity and reliability
- Safety and resilience
- Security and robustness
- Accountability and transparency
- Explainability and interpretability
- Privacy enhancement and data governance
- Fairness and harmful bias management

For each material risk, describe the condition, cause, event or failure mode, potential impact, affected stakeholders, benefit at stake, potential harm, evidence gap, and uncertainty. Consider direct, indirect, cumulative, systemic, and difficult-to-remedy harms.

Inventory existing controls and assess whether they are designed appropriately and operating effectively. Consider preventive, detective, corrective, compensating, and human-oversight controls.

### 5. Score inherent and residual risk

Use the default 1–5 scale unless the engagement specifies another scale. Define the scale in the assessment:

| Score | Likelihood | Impact |
|---|---|---|
| 1 | Rare | Negligible |
| 2 | Unlikely | Minor |
| 3 | Possible | Moderate |
| 4 | Likely | Major |
| 5 | Almost certain | Severe or catastrophic |

Calculate `Inherent Risk = Likelihood x Impact` before considering existing controls. Calculate `Residual Risk = residual likelihood x residual impact` after considering existing controls. If the assessment uses a different method, state it explicitly and do not imply that scores are directly comparable.

Use this default rating band unless the client provides an approved matrix:

- 1–4: Low
- 5–9: Moderate
- 10–16: High
- 17–25: Critical

Do not let a numeric score hide uncertainty, vulnerable groups, irreversible harm, legal constraints, or a risk that exceeds tolerance. Explain the rationale for each score and state whether the residual risk is within tolerance.

### 6. MANAGE treatment and decisions

For each risk above the accepted tolerance, or where evidence is insufficient for approval, recommend one or more treatments:

- Avoid: do not use the AI system or remove the risky purpose
- Reduce: add or improve controls to lower likelihood or impact
- Transfer/share: allocate contractual, insurance, or operational responsibility without assuming the risk disappears
- Accept: formally accept residual risk through the authorized owner
- Restrict: limit users, data, decisions, geography, volume, or autonomy
- Pause: suspend operation pending investigation or remediation
- Retire: decommission the system and manage transition and downstream effects

Every treatment must specify the accountable owner, action, due date or cadence, dependencies, success measure, evidence of completion, residual risk, and approval required.

Define monitoring for model and data drift, performance, safety, security, privacy, fairness, reliability, incidents, complaints, appeals, human overrides, provider changes, and harmful outputs. Define thresholds and actions for reassessment, rollback, restriction, suspension, or retirement.

### 7. Produce the risk register

Use one row per distinct risk. Include these canonical fields in this order:

| Field | Required content |
|---|---|
| Risk ID | Stable identifier such as `AI-RISK-001` |
| Risk Category | One or more approved categories |
| Risk Description | Clear risk statement describing cause, event, and consequence |
| Cause | Root or contributing cause |
| Potential Impact | Business, individual, societal, environmental, legal, or operational effect |
| Affected Stakeholders | People, groups, organizations, or systems affected |
| Likelihood | Inherent likelihood, 1–5 with rationale |
| Impact | Inherent impact, 1–5 with rationale |
| Inherent Risk | Score and rating before controls |
| Existing Controls | Current preventive, detective, corrective, or oversight controls |
| Control Effectiveness | Effective, Partially Effective, Ineffective, Not Tested, or Unknown, with evidence |
| Residual Risk | Post-control score, rating, uncertainty, and tolerance decision |
| Risk Owner | Accountable role or named owner |
| Treatment | Avoid, Reduce, Transfer/Share, Accept, Restrict, Pause, or Retire, plus action |
| Status | Proposed, Open, In Treatment, Accepted, Monitoring, Blocked, Paused, Retired, or Closed |

Add `Evidence`, `Control Owner`, `Target Date`, `Review Cadence`, `Risk Tolerance`, and `Treatment Rationale` when the register is used operationally. Keep the requested canonical fields visible even when additional fields are added.

### 8. Summarize decisions

After the register, include:

1. Executive conclusion and decision requested
2. Highest risks and risks outside tolerance
3. Key benefits, impacts, harms, and affected stakeholders
4. GOVERN, MAP, MEASURE, and MANAGE coverage
5. Major evidence gaps and assumptions
6. Recommended treatments and dependencies
7. Monitoring and reassessment triggers
8. Deployment, continuation, restriction, pause, or retirement recommendation
9. Required specialist review and explicit approval owner

## Quality Gate

Before finalizing, verify:

- Every risk has a unique ID, category, owner, treatment, and status.
- Likelihood and impact include rationale, not only numbers.
- Inherent risk is calculated before controls and residual risk after controls.
- Control effectiveness is supported by evidence or marked unknown/not tested.
- Benefits, impacts, harms, affected stakeholders, and uncertainty are addressed.
- Risk tolerance and the authority for acceptance are explicit.
- Third-party, human-factor, lifecycle, monitoring, and decommissioning risks are considered where relevant.
- Recommendations are proportionate, actionable, sequenced, and measurable.
- Unsupported facts are labeled as reported, assumed, or unknown.
- Legal or specialist review needs are visible.
- The assessment states the decision requested and the next review date or trigger.

## Default Output

Unless another format is requested, produce:

1. **Executive conclusion**
2. **Scope, system context, and assumptions**
3. **Scoring method and risk tolerance**
4. **Structured AI risk register**
5. **Priority treatments and decisions**
6. **Monitoring and lifecycle actions**
7. **Evidence gaps, specialist review, and next steps**
