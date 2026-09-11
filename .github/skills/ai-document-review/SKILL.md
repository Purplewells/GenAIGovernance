---
name: ai-document-review
description: 'Review AI governance artefacts for missing sections, unsupported claims, inconsistent risk ratings, missing owners, missing evidence, contradictions, outdated references, and missing regulatory considerations. Use for cross-document governance quality reviews of risk registers, DPIAs, policies, control matrices, assurance plans, vendor assessments, incident records, and system documentation.'
argument-hint: '[governance artefacts, document set, or consistency question]'
user-invocable: true
disable-model-invocation: false
---

# AI Document Review

## Purpose

Review AI governance artefacts as a connected evidence set. Identify gaps and contradictions that could cause an unsafe, unlawful, unaccountable, or unsupported decision. Compare claims across documents and against available system, process, vendor, and operational evidence.

Examples of findings:

- A risk register says a DPIA is complete, but the DPIA is marked Draft.
- A control matrix marks a control Effective, but the assurance plan has no test or evidence.
- A vendor assessment says data is not used for training, but contract terms allow product improvement.
- A policy names a risk owner that differs from the approval record and current operating model.
- A risk is rated Low in one artefact and Critical in another without a rationale.

This skill is a governance quality review, not legal advice, certification, or a substitute for specialist privacy, security, safety, audit, regulatory, or domain review.

## When to Use

Use this skill for:

- Cross-document AI governance reviews
- Pre-approval, pre-audit, renewal, and management reviews
- Risk register, DPIA, policy, control matrix, assurance plan, vendor assessment, and system-card checks
- Post-incident and post-change document reconciliation
- Evidence quality and traceability reviews
- Regulatory and reference currency checks
- Identifying paper controls and unsupported governance claims

## Artefacts to Review

Review the available set, identifying what is missing rather than assuming it exists:

- AI inventory and use-case assessment
- Risk register and impact assessment
- DPIA, privacy notice, data map, retention schedule, and transfer assessment
- AI policy, standard, procedure, and acceptable-use guidance
- Control matrix, assurance plan, audit report, and evidence catalogue
- System card, model card, technical design, evaluation report, and monitoring plan
- Vendor assessment, contract, DPA, subprocessor list, and assurance reports
- Incident record, complaint, appeal, corrective-action log, and management decision
- Approval, change, release, suspension, retirement, and decommissioning records

## Review Principles

- Establish the document baseline and date before interpreting content.
- Prefer primary and current artefacts over summaries or copied statements.
- Trace every material claim to evidence, an owner, a decision, and a review date.
- Distinguish contradictions from legitimate scope, lifecycle, version, or jurisdiction differences.
- Do not resolve contradictions silently; state which source is authoritative or mark the issue unresolved.
- Treat missing evidence as a finding when the claim affects risk, compliance, safety, privacy, security, or approval.
- Do not infer completion from a document title, checkbox, certification logo, or reference to a framework.
- Flag claims that cannot be verified, are based only on vendor assertions, or lack a measurement method.
- Check whether references, laws, standards, guidance, model versions, owners, and dates are current.
- Avoid declaring legal non-compliance without sufficient facts and qualified review; identify the regulatory question and evidence needed.

## Procedure

### 1. Establish the review baseline

Record:

- Review objective, decision requested, artefacts in scope, exclusions, and evidence cutoff
- Document name, version, status, owner, approval authority, effective date, review date, and last update
- AI system, model, vendor, use case, environment, lifecycle stage, jurisdictions, and data scope
- Applicable frameworks, laws, contracts, policies, and organizational risk tolerance
- Known changes, incidents, previous findings, exceptions, and open remediation

Create an artefact inventory. Mark each expected artefact as Present, Missing, Draft, Expired, Superseded, Inconsistent, or Not Applicable with rationale.

### 2. Check completeness and required sections

For each artefact, compare the content with its purpose and approved template. Look for missing sections such as:

- Scope, purpose, intended use, exclusions, and lifecycle stage
- Roles, accountability, approval authority, risk owner, and review cadence
- Data sources, provenance, processing purpose, retention, location, access, and deletion
- Stakeholders, affected people, vulnerable groups, benefits, impacts, harms, and recourse
- Risk methodology, likelihood, impact, inherent risk, controls, residual risk, tolerance, and treatment
- Trustworthy-AI measures for validity, reliability, safety, security, privacy, fairness, transparency, explainability, and human oversight
- Third parties, subprocessors, model providers, dependencies, concentration, and exit
- Monitoring, incidents, complaints, appeals, change control, assurance, exceptions, and decommissioning
- Evidence, limitations, assumptions, references, approval, version history, and next review date

Only call a section missing when it is required by the artefact purpose, risk, applicable obligation, or agreed template. Explain the basis.

### 3. Trace claims to evidence

Extract material claims, including statements such as `complete`, `approved`, `effective`, `low risk`, `no personal data`, `no training use`, `compliant`, `tested`, `independently assured`, or `not applicable`.

For each claim, ask:

- Which artefact or primary evidence supports it?
- Is the source current, attributable, complete, and within scope?
- Does the evidence demonstrate design, implementation, operation, and effectiveness as applicable?
- Is the claim stronger than the evidence supports?
- Is the claim limited to a version, environment, vendor, jurisdiction, or date that is clearly stated?

Classify claim support as Verified, Partially Supported, Unsupported, Contradicted, Stale, or Not Testable. Do not upgrade a vendor statement or policy assertion to verified operation without corroboration.

### 4. Reconcile risk, control, and assurance information

Compare across artefacts:

- Risk IDs, descriptions, categories, causes, impacts, affected stakeholders, likelihood, impact, and ratings
- Inherent versus residual risk calculations and risk-tolerance decisions
- Existing controls, control owners, effectiveness ratings, evidence, assurance results, and open findings
- Treatment actions, due dates, status, accepted exceptions, and closure evidence
- Model, system, vendor, data, subprocessor, and environment versions
- Approval status, deployment status, incident status, monitoring thresholds, and lifecycle state

Flag inconsistent ratings when the difference lacks a documented method, date, scope, or change explanation. Check calculations rather than trusting stated Low, Moderate, High, or Critical labels.

### 5. Detect contradictions and stale information

Search for direct and indirect contradictions, including:

- Completed versus Draft or expired documents
- Approved versus unapproved deployment status
- Different owners, approval authorities, risk tolerances, or review dates
- No personal data versus DPIA, data map, or personal-data fields
- No training use versus contract, vendor terms, or product settings allowing training
- No subprocessors versus a subprocessor list or vendor architecture
- Effective control versus failed test, overdue evidence, incident, or unresolved finding
- Model version or service configuration mismatches
- Retention, deletion, data-location, encryption, access, or incident obligations that differ
- Risk accepted versus treatment still open or approval missing
- Retired or paused system versus active monitoring, traffic, or dependent workflows

For each contradiction, cite both sources, explain why it matters, identify the authoritative source if known, and state the resolution required.

### 6. Check regulatory and reference coverage

Identify regulatory considerations suggested by the facts, including:

- UK GDPR principles, lawful basis, transparency, rights, DPIA, automated decision-making, processor terms, security, retention, transfers, and breach response where relevant
- Data Protection Act 2018, sector rules, contractual duties, records obligations, and applicable jurisdictional requirements
- ICO guidance relevant to AI, data protection, fairness, explainability, security, governance, or individual rights
- NIST AI RMF, ISO/IEC 42001, ISO/IEC 27001, OWASP GenAI, or other cited frameworks and their stated editions
- Privacy, security, safety, equality, accessibility, intellectual-property, consumer, employment, and product obligations suggested by the use case

Check reference title, edition, publication date, effective date, link, and whether the source has been superseded. Flag missing considerations as questions or evidence gaps, not unsupported legal conclusions.

### 7. Report findings and remediation

Assign each finding a stable ID such as `DOC-REVIEW-001` and classify it:

- Missing Section
- Unsupported Claim
- Inconsistent Rating
- Missing Owner
- Missing Evidence
- Contradiction
- Outdated Reference
- Missing Regulatory Consideration
- Stale Status
- Traceability Gap

Rate severity using impact, likelihood, affected people, reversibility, risk tolerance, decision urgency, and confidence in the finding. For each finding record:

- Finding and expected state
- Source artefact(s), section, version, and evidence
- Why it matters and affected decision or risk
- Severity, confidence, and whether immediate containment is needed
- Owner responsible for resolution
- Corrective action, dependency, due date, and success measure
- Verification method, reviewer, and closure evidence
- Whether the risk register, control matrix, assurance plan, vendor assessment, incident record, or policy must also be updated

Do not close a contradiction by editing one document without checking every dependent artefact.

## Default Output

Unless another format is requested, produce:

1. **Executive summary and decision impact**
2. **Artefact inventory and baseline status**
3. **Completeness and missing-section review**
4. **Claim-to-evidence review**
5. **Risk, control, owner, and rating reconciliation**
6. **Contradictions and stale-information findings**
7. **Regulatory and reference coverage review**
8. **Prioritized findings and remediation plan**
9. **Open questions, assumptions, and specialist review**

Use this findings table:

| Field | Required content |
|---|---|
| Finding ID | Stable identifier such as `DOC-REVIEW-001` |
| Finding Type | Missing Section, Unsupported Claim, Inconsistent Rating, Missing Owner, Missing Evidence, Contradiction, Outdated Reference, or Missing Regulatory Consideration |
| Severity | Critical, High, Moderate, Low, or Observation |
| Source Artefacts | Documents, versions, sections, or records compared |
| Finding | What is missing, unsupported, inconsistent, contradictory, or stale |
| Evidence | Source evidence and confidence |
| Decision / Risk Impact | Why the issue matters |
| Owner | Accountable resolution owner |
| Remediation | Specific corrective action |
| Due Date | Target date or review trigger |
| Verification | Retest, reconciliation, approval, or evidence required |
| Status | Open, In Progress, Blocked, Accepted, Verified, or Closed |

## Quality Gate

Before finalizing, verify:

- The review includes an artefact inventory, baseline status, versions, owners, and evidence cutoff.
- Missing sections are judged against purpose, risk, obligations, and approved templates.
- Material claims are traced to current evidence and classified by support strength.
- Risk ratings, calculations, owners, treatments, statuses, and risk-tolerance decisions are reconciled across artefacts.
- Contradictions cite both sources and identify resolution or authoritative evidence.
- Unsupported completion, approval, effectiveness, compliance, and low-risk claims are explicitly flagged.
- Evidence gaps distinguish missing design, missing implementation, missing operation, and missing assurance.
- Regulatory considerations and reference currency are reviewed without overstating legal conclusions.
- Every finding has severity, owner, remediation, due date, verification, and status.
- Dependent artefacts and records to update are identified.
- The report clearly states whether the governance decision can proceed, must be conditional, or should pause pending resolution.
