---
title: Telleion Hospitals NHS Foundation Trust - AI Risk Appetite Statement
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: Trust Board, on recommendation from the AI Governance Committee
review_date: 2026-12-11
scope: AI systems proposed, acquired, developed, used, changed, monitored, or retired by the Trust
---

# AI Risk Appetite Statement

## 1. Purpose and Decision

This statement defines the Trust's proposed appetite and tolerance for AI-related risk. It guides use-case classification, control design, approval, monitoring, escalation, and residual-risk acceptance.

**Decision requested:** The Trust Board is asked to approve this statement on recommendation from the AI Governance Committee. Until approved, the values below are proposed decision criteria for consultation only and must not be treated as authorised risk acceptance.

Risk appetite is not permission to cause harm. No appetite statement overrides law, professional duties, patient safety, contractual obligations, or a specific decision to avoid or prohibit a use.

## 2. Risk Principles

The Trust has:

- **No appetite** for avoidable serious harm to patients, staff, applicants, service users, or other affected people.
- **No appetite** for unlawful processing, discrimination, concealment of AI use, unauthorised disclosure, or deployment without required approval.
- **Very low appetite** for untested or unexplained AI in high-impact clinical, patient-safety, safeguarding, employment, or rights-affecting decisions.
- **Low appetite** for material privacy, security, resilience, third-party, intellectual-property, or accountability risk.
- **Cautious appetite** for controlled innovation where benefits are clear, risks are understood, controls are tested, human oversight is meaningful, and residual risk is within tolerance.
- **Greater appetite** for low-impact experimentation using non-sensitive or synthetic data in approved environments, provided it cannot silently move into operational use.

## 3. Risk Tolerance Rules

- Residual risk must be within the approved tolerance for the use case and risk domain.
- Risk acceptance must be time-limited, evidence-based, assigned to an authorised owner, and reviewed by a stated date or trigger.
- A risk may not be accepted merely because a supplier, policy, certificate, questionnaire, or framework mapping claims that it is controlled.
- Missing evidence increases uncertainty and may require restriction, additional assurance, pause, or rejection.
- Risks affecting vulnerable groups, irreversible harms, fundamental rights, patient safety, or public trust must be escalated even where a numerical score appears moderate.
- Where risk appetite is exceeded, the default decision is avoid, reduce, restrict, pause, or retire. Transfer to a supplier does not remove Trust accountability.

## 4. Proposed Appetite by Risk Domain

| Risk domain | Proposed appetite | Minimum expectation | Escalation or stop trigger |
|---|---|---|---|
| Patient or clinical safety | None for avoidable serious harm; very low otherwise | Clinical or domain safety review, validation, human oversight, safe fallback, monitoring, incident response, and restart criteria | Serious harm, unsafe output, missed deterioration, uncontrolled automation, or inadequate evidence |
| Privacy and data protection | Low; none for unlawful processing or unjustified special-category use | Lawful basis, necessity, minimisation, transparency, DPIA where required, retention, rights, transfers, and DPO advice | Unlawful processing, unapproved data use, breach, missing DPIA, or unacceptable residual privacy risk |
| Security and confidentiality | Low; none for unauthorised disclosure or uncontrolled access | Identity, least privilege, encryption, logging, vulnerability management, incident response, resilience, and tested recovery | Data leakage, compromise, material vulnerability, uncontrolled privileged access, or failed recovery |
| Fairness and equality | None for intentional discrimination; very low for material unexplained disparity | Relevant subgroup testing, proxy analysis, monitoring, human challenge, recourse, and remediation | Discrimination, material disparate impact, inaccessible service, or inability to investigate outcomes |
| Accuracy and validity | Cautious and use-case dependent | Defined performance measures, limitations, uncertainty, local validation, human review, and thresholds | Performance below approved threshold, unknown local validity, or harmful reliance on unreliable output |
| Reliability and availability | Low for systems supporting critical or time-sensitive services | Service levels, fallback, continuity, recovery objectives, monitoring, and tested degraded operation | Single point of failure without fallback, repeated outage, unsafe failure mode, or untested recovery |
| Transparency and explainability | Very low for decisions affecting rights, access, employment, or care | AI disclosure, limitations, meaningful explanation, challenge, correction, and accountable human review | Concealed AI use, unexplainable material outcome, or no route to challenge or recourse |
| Human factors and oversight | Very low for high-impact decisions | Competent reviewer, time, information, authority, training, override, workload monitoring, and audit | Nominal human review, automation bias, unrecorded decisions, or inability to override |
| Legal, regulatory, and contractual | None for known unlawful or prohibited activity | Specialist review, current references, compliant terms, records, and approval | Legal prohibition, unresolved regulatory concern, contract gap, or unsupported compliance claim |
| Third-party and supply chain | Low; cautious for critical dependency or lock-in | Vendor due diligence, evidence, contractual controls, subprocessors, change notice, audit rights, and exit | Refusal to provide evidence, uncontrolled model change, inadequate remedies, or no viable exit |
| Intellectual property and licensing | Low | Rights, licences, provenance, permitted use, confidentiality, and output restrictions documented | Unclear rights, unauthorised training data, licence breach, or material ownership dispute |
| Reputation and public trust | Low | Transparent purpose, stakeholder engagement, benefits, harms, complaints, communications, and accountable decisions | Concealment, avoidable harm, repeated unresolved incidents, or material loss of trust |
| Environmental and societal impact | Cautious and proportionate | Consider energy, resource use, distributional impacts, and alternatives where material | Material unmanaged impact or benefits that do not justify wider harms |

## 5. Risk Rating and Tolerance Application

Use [010-risk-assessment-methodology.md](010-risk-assessment-methodology.md) for each assessment. The assessment must show:

- Inherent likelihood and impact before controls
- Existing and proposed controls
- Control design, implementation, operating effectiveness, and assurance status
- Residual likelihood and impact after controls
- Uncertainty, affected stakeholders, benefits, harms, and reversibility
- Comparison with the domain appetite and use-case tolerance
- Authorised decision, conditions, review date, and status

Until this methodology and the appetite are approved, they are consultation criteria only and cannot authorise operational risk acceptance.

Numerical scores support consistency but must not conceal serious harms, legal constraints, uncertainty, or impacts on vulnerable groups.

## 6. Decision Thresholds

### Proceed

A use case may proceed only where:

- Purpose, benefit, alternatives, scope, and affected stakeholders are understood.
- Required privacy, security, safety, equality, legal, vendor, and assurance reviews are complete or explicitly conditioned.
- Residual risk is within approved tolerance.
- Human oversight, monitoring, incident response, and exit arrangements are operational.
- The authorised decision records owner, rationale, evidence, date, review date, status, and conditions.

### Proceed with conditions

Conditional approval may be used only where:

- The remaining gaps do not exceed the authorised tolerance for the proposed limited scope.
- Conditions are specific, owned, time-bound, measurable, and supported by compensating controls.
- Use is restricted by data, users, geography, decisions, autonomy, volume, or duration where necessary.
- Failure to meet conditions triggers escalation, restriction, pause, or retirement.

### Do not proceed, pause, or retire

The Trust must not proceed, or must pause or retire, where:

- Risk exceeds tolerance and no authorised exception exists.
- Evidence is insufficient to make a defensible decision.
- Serious harm, discrimination, unlawful processing, material security exposure, or unsafe operation is identified.
- Human oversight, accountability, monitoring, incident response, or safe fallback is ineffective.
- A vendor or internal team cannot provide required evidence, controls, remedies, or exit capability.

## 7. Monitoring and Review

The Head of AI Governance will report at least quarterly:

- Risks outside tolerance and time-limited acceptances
- Open and overdue treatments and assurance findings
- Incidents, complaints, appeals, harmful outputs, and near misses
- Performance, fairness, privacy, security, availability, and benefit indicators
- Vendor changes, concentration, lock-in, and exit readiness
- Systems paused, restricted, retired, or awaiting approval

The risk appetite must be reviewed at least annually and after material changes to Trust strategy, law, standards, risk profile, incidents, public expectations, or the AI portfolio.

| Decision field | Value |
|---|---|
| Owner | Head of AI Governance |
| Rationale | Establish consistent, proportionate criteria for AI risk decisions and escalation |
| Evidence | AI Governance Framework, Policy, Principles, risk assessments, assurance results, and portfolio reporting |
| Date | 2026-09-11 |
| Review date | 2026-12-11 |
| Status | Draft for consultation |
