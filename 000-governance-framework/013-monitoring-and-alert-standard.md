---
title: Telleion Hospitals NHS Foundation Trust - AI Monitoring and Alert Standard
version: 0.1
date: 2026-09-11
status: Draft for consultation
owner: Head of AI Governance
approval_authority: AI Governance Committee
review_date: 2026-12-11
scope: Operational monitoring of material AI systems
---

# AI Monitoring and Alert Standard

## 1. Purpose

This standard defines minimum monitoring, alerting, evidence retention, and escalation requirements for material AI systems.

## 2. Monitoring Plan Requirements

Each system must define:

- Indicators for performance, drift, validity, safety, privacy, security, fairness, reliability, availability, human oversight, incidents, complaints, appeals, and benefits as relevant.
- Baseline, threshold, rationale, data source, collection method, owner, reviewer, and response time for each indicator.
- Automated and manual checks, population or sample, data-quality validation, and limitations.
- Alert route, escalation, fallback, restriction, pause, rollback, and reassessment actions.
- Evidence retention period and access controls.

## 3. Minimum Cadence

- Data collection: continuous or daily for operational systems where technically feasible.
- System-owner review: at least weekly during pilot and monthly in operation, or more frequently according to risk.
- Incident and threshold breach escalation: without undue delay and within one working day for material events.
- AI Governance Committee review: at least quarterly and monthly for Tier 3 systems during pilot or where thresholds are breached.
- Trust Board reporting: at least quarterly for portfolio, tolerance, incidents, benefits, and overdue remediation.

## 4. Threshold and Alert Rules

Thresholds must be set from validated baselines and approved before deployment. A threshold breach requires documented triage, decision, evidence, owner, and status. Repeated breaches, unexplained drift, harmful outputs, or data-quality failure trigger reassessment and may require restriction or pause.

Monitoring must not be designed only to demonstrate success. It must detect harm, inequity, control failure, silent degradation, and loss of approved boundaries.

## 5. Evidence and Escalation

Retain raw monitoring inputs where lawful and proportionate, derived metrics, alerts, decisions, investigations, corrective actions, and review records for the period defined in the records schedule. The System Owner responds first; unresolved material alerts escalate to the Head of AI Governance and AI Governance Committee, with Trust Board escalation for reserved matters or risk outside tolerance.
