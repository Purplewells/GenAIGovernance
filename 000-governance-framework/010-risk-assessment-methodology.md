---
title: Telleion Hospitals NHS Foundation Trust - AI Risk Assessment Methodology
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: AI Governance Committee, subject to Trust Board approval of risk appetite
review_date: 2026-12-11
scope: AI risk and impact assessments
---

# AI Risk Assessment Methodology

## 1. Purpose

This methodology makes AI risk assessments comparable, evidence-based, and proportionate. It must be used with the AI Classification Standard, Risk Appetite Statement, and Approval Process.

## 2. Scoring

Score likelihood and impact from 1 to 5:

| Score | Likelihood | Impact |
|---|---|---|
| 1 | Rare | Negligible, no material harm |
| 2 | Unlikely | Minor, limited and readily reversible harm |
| 3 | Possible | Moderate, temporary or recoverable harm |
| 4 | Likely | Major, serious or difficult-to-reverse harm |
| 5 | Almost certain | Severe, permanent, systemic, rights-affecting, or life-threatening harm |

Calculate `Risk score = Likelihood x Impact`.

| Score | Rating |
|---|---|
| 1-4 | Low |
| 5-9 | Moderate |
| 10-16 | High |
| 17-25 | Critical |

The score is an aid to judgement. A legal prohibition, serious potential harm, vulnerable group, or unacceptable uncertainty may require escalation regardless of the numerical score.

## 3. Required Assessment

For each material risk record:

- Risk ID, category, cause, event, consequence, affected stakeholders, benefits, harms, and uncertainty
- Inherent likelihood, impact, score, rating, and rationale before controls
- Existing controls and their design, implementation, operating, and assurance status
- Residual likelihood, impact, score, rating, confidence, and comparison with tolerance
- Treatment, owner, due date, evidence, review trigger, and authorised decision

Controls must not reduce a score unless there is evidence that they are designed, implemented, and operating effectively. Vendor assertions and policies are not sufficient on their own.

## 4. Responsibilities

- System Owner drafts the assessment and evidence basis.
- Risk Owner validates ratings, treatment, and tolerance.
- Head of AI Governance checks methodology, consistency, and completeness.
- Specialist reviewers challenge privacy, security, clinical, fairness, legal, or domain assumptions.
- Assurance or Internal Audit independently reviews material assessments where required.
- AI Governance Committee approves Tier 3 or disputed assessments; Trust Board handles reserved matters.

## 5. Uncertainty and Overrides

Record confidence as High, Medium, or Low and state what evidence would change the conclusion. Apply the higher risk rating where assessors disagree until resolved. Classification overrides in the AI Classification Standard take precedence over a lower numerical score.

## 6. Review Triggers

Reassess after material change, incident, adverse outcome, significant drift, new evidence, change in law or guidance, new affected population, vendor change, or expiry of risk acceptance.
