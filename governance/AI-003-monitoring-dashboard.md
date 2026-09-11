---
title: AI-003 Generative AI Patient Service Assistant — AI Monitoring Dashboard & Metrics
date: 2026-09-11
lifecycle_stage: Deployment & Operations
scope: Real-time and historical monitoring of chatbot performance, safety, accuracy, and governance compliance
decision_requested: Whether the monitoring strategy is adequate to detect issues and enable proactive governance
owner: Clinical Safety Officer & Data Analytics Lead
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Draft
---

# AI-003 Generative AI Patient Service Assistant — AI Monitoring Dashboard & Metrics

## Purpose

This document defines the metrics, dashboards, and monitoring processes that enable ongoing governance of the patient service assistant chatbot post-deployment. Continuous monitoring is essential to:

- Detect performance degradation, bias, or safety issues early
- Enable rapid response to incidents
- Provide evidence for governance reviews
- Support continuous improvement
- Meet regulatory and organisational monitoring obligations

---

## Monitoring Architecture

### Real-Time Dashboard (Operations)

**Audience:** PALS Manager, Duty Clinician, System Administrator

**Update Frequency:** Real-time (updates every 60 seconds)

**Purpose:** Operational visibility; alert to performance issues that require immediate response

**Key Displays:**
- System uptime and response latency
- Enquiry volume (current/hourly/daily)
- Escalation queue depth and SLA compliance
- Alert status (any critical issues)

### Daily Operations Report (PALS Manager)

**Audience:** PALS Manager, PALS Team

**Frequency:** Daily (9 AM email)

**Purpose:** Day-to-day operations; staffing needs; workload planning

**Key Metrics:**
- Total enquiries and escalations (previous 24 hours)
- Escalation rate and breakdown by category
- SLA compliance (by category)
- Response latency (average and P95)
- System errors or alerts
- Top escalation reasons (trending)

### Weekly Safety & Quality Review (Clinical Safety Officer)

**Audience:** Clinical Safety Officer, Chief Medical Officer, Quality Lead

**Frequency:** Weekly (Monday 10 AM)

**Purpose:** Clinical safety governance; quality assurance; trend detection

**Key Metrics:**
- Accuracy audit results (sample of 25 responses)
- False-positive/negative escalation rates
- Patient feedback summary (satisfaction, errors reported)
- Incident reports (any patient harm, near-misses)
- Knowledge-base quality metrics (retrieval precision, coverage gaps)
- Safeguarding-escalation summary (appropriate responses)

### Monthly Governance Report (AI Governance Committee)

**Audience:** AI Governance Committee, Board (if escalated)

**Frequency:** Monthly (third Friday)

**Purpose:** Strategic oversight; governance compliance; risk management

**Key Metrics:**
- System performance summary (uptime, latency, volume trends)
- Safety & accuracy metrics (incident count, escalation appropriateness)
- Data protection compliance (data breaches, access violations)
- Vendor performance (if applicable)
- Staff training and competency
- Risk register status (residual risks, control effectiveness)
- Recommendations for system changes or improvements

### Annual Audit Report (Internal Audit)

**Audience:** Audit Committee, Compliance Officer, AI Governance Committee

**Frequency:** Annually

**Purpose:** Independent assurance; audit trail; compliance certification

**Key Metrics:**
- All metrics from monthly report, year-on-year trend
- NIST AI RMF compliance assessment
- Control effectiveness review (design vs. operation)
- Vendor audit results (if applicable)
- Staff competency and training records
- Change management compliance
- Incident root-cause analysis and remediation
- Recommendations for governance improvements

---

## Core Metrics

### 1. System Performance Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **System Uptime** | % of time chatbot is available and responding | 99.5% | Real-time monitoring | <99% triggers alert |
| **Response Latency (P50)** | Median response time from enquiry to response | <1 second | Every response | >2 sec = warning |
| **Response Latency (P95)** | 95th percentile response time | <3 seconds | Every response | >5 sec = alert |
| **Error Rate** | % of enquiries resulting in system error (not business logic, but technical failure) | <0.5% | Real-time logging | >1% = alert |
| **Throughput** | Enquiries processed per hour | Monitored (no fixed target; baseline in first month) | Hourly count | >30% above baseline = investigate |

### 2. Enquiry Volume & Escalation Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Total Enquiry Volume** | Number of enquiries received (daily/weekly/monthly) | Monitored (ramp-up expected first 3 months) | Real-time counter | Monitored for trend |
| **Escalation Rate** | % of enquiries escalated to human staff | <10% (initial); improve toward <5% as knowledge base matures | Per enquiry | >10% = investigate; trend analysis |
| **Escalation Category A (Clinical)** | % of enquiries escalated to clinician | Monitored (2–5% expected) | Per enquiry | >5% = trend analysis |
| **Escalation Category B (Urgent)** | % escalations to PALS (urgent) | Monitored; expected <3% | Per enquiry | Trend analysis |
| **Escalation Category C (Routine)** | % escalations to PALS (routine, no match) | Monitored; improve as knowledge base grows | Per enquiry | Decreasing trend expected |
| **Escalation SLA Compliance** | % escalations responded within SLA by category | CRITICAL: 100% <2 min; HIGH: 95% <15 min; MEDIUM: 90% <30 min | Per escalation | Below target = staffing review |

### 3. Accuracy & Safety Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Retrieval Precision (Top-1)** | % of responses where top-1 retrieved document is clinically appropriate | ≥90% | Weekly audit (25-response sample) | <85% = knowledge-base review |
| **Retrieval Precision (Top-3)** | % of responses where any of top-3 documents is appropriate | ≥95% | Weekly audit | <90% = investigation |
| **Hallucination Rate** | % of responses containing factually incorrect information not in approved sources | <2% | Weekly audit (25-response sample); clinician review | >2% = knowledge-base audit |
| **Inappropriate Escalation Rate** | % of escalations to clinician that clinician rates as unnecessary | <10% | Monthly review (20-escalation sample) | >10% = escalation logic review |
| **Missed Escalation Rate** | % of responses that should have been escalated but weren't (clinical concern missed) | <1% | Monthly review; clinician assessment | >1% = escalation logic tuning |
| **Patient Accuracy Feedback** | % of patients rating information as accurate in post-interaction survey | >95% | Post-interaction survey (optional) | <90% = investigate |
| **Incident Count** | Number of patient-harm incidents, complaints, or near-misses related to chatbot | 0 (target) | Incident reporting system | Any incident = immediate review |

### 4. Data Protection & Security Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Data Breach Incidents** | Number of unauthorised access, disclosure, or loss events | 0 | Incident reporting; audit logs | Any incident = immediate escalation |
| **Attempted Prompt Injections Detected** | Number of detected prompt-injection or security-attack attempts | Monitored | Security logs; content filter | >10 per day = trend analysis; review defences |
| **Unauthorised Access Attempts** | Number of attempts to access other patients' data or system controls | 0 | Access logs | Any attempt = investigation |
| **Data Retention Compliance** | % of enquiries deleted within 90-day retention policy | 100% | Monthly audit of data store | <100% = immediate remediation |
| **Encryption Compliance** | % of data encrypted in transit (TLS) and at rest (AES-256) | 100% | Configuration audit | <100% = immediate remediation |
| **Access Control Violations** | Unauthorised staff access to patient data or system controls | 0 | Access logs; monthly review | Any violation = incident response |

### 5. Monitoring Bias & Fairness Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Response Quality by Demography** | Accuracy rate by patient age group, sex, ethnicity | Equal across groups (statistical parity or similar fairness metric) | Quarterly audit (stratified sample) | Significant difference (>5% accuracy gap) = investigation |
| **Escalation Rate by Demography** | Escalation rate by age, sex, ethnicity | Equal across groups (no systematic over/under-escalation) | Quarterly audit | Significant difference = bias investigation |
| **Subgroup Clinical Safety** | Incident or harm rate by patient subgroup | Equal; no disparity | Quarterly review | Any disparity = fairness review |
| **Language Barrier Escalations** | Escalations where patient clearly had language difficulty | Monitored (should be rare if multilingual support available) | Post-interaction feedback | Trend analysis; accessibility improvement |

### 6. Knowledge Base Quality Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Source Coverage** | % of common enquiry types for which a matching source exists in knowledge base | ≥95% | Quarterly gap analysis | <90% = identify missing content |
| **Source Recency** | % of sources reviewed within last 90 days | 100% | Document review log | <100% = review schedule enforcement |
| **Source Currency** | % of sources reflecting current Trust policies, procedures, and information | 100% (at time of ingestion) | Monthly trend analysis of updates | Any outdated source flagged = immediate update |
| **Retrieval Sensitivity** | % of relevant documents in knowledge base actually retrieved in top-10 for known queries | ≥95% (recall) | Monthly audit (20 known-answer queries) | <90% = retrieval parameter tuning |
| **False Positive Retrieval Rate** | % of retrieved documents that are irrelevant to enquiry | <10% | Weekly audit (sample of retrievals) | >10% = retrieval threshold or index review |

### 7. User Experience & Satisfaction Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Patient Satisfaction (Post-Interaction Survey)** | % of responding patients rating interaction as helpful | ≥80% | Optional survey (pilot phase) | <70% = user experience review |
| **Self-Service Success Rate** | % of enquiries answered by chatbot without escalation | Monitored; expect 85–95% | Per enquiry | Significant decline = knowledge-base review |
| **Patient Feedback: Accuracy** | % of survey respondents rating information as accurate | >90% | Optional survey | <80% = accuracy audit |
| **Patient Feedback: Clarity** | % of survey respondents rating responses as clear and understandable | >90% | Optional survey | <80% = communication review |
| **Dropout/Abandon Rate** | % of users who start interaction but abandon before completion | Monitored | Session analytics | High abandon rate = UX review |

### 8. Staffing & Operations Metrics

| Metric | Definition | Target | Collection | Alert Threshold |
|---|---|---|---|---|
| **Clinician Response Time (Actual)** | Average time from escalation to clinician response | <5 min (CRITICAL); <15 min (HIGH) | Per escalation | Average >target = staffing review |
| **PALS Response Time (Actual)** | Average time from escalation to PALS response | <15 min (MEDIUM/HIGH); <30 min (routine) | Per escalation | Average >target = staffing review |
| **Staff Training Completion** | % of staff completed required chatbot training | 100% | Training records | <100% = training enforcement |
| **Staff Competency Assessment** | % of staff passing competency assessment (e.g. test escalations) | 100% initial; 95% ongoing | Annual competency assessment | <95% = targeted retraining |
| **Staff Turnover** | Turnover in PALS/clinical staff assigned to chatbot escalations | Monitored (knowledge loss risk if high) | HR records | High turnover = retraining plan |

---

## Monitoring Dashboards

### Real-Time Operations Dashboard

**Platform:** Grafana, Tableau, or custom web app

**Displays (visible to PALS Manager, clinician, system admin):**

```
┌─────────────────────────────────────────────────────────┐
│ AI Patient Service Assistant — Real-Time Status         │
├─────────────────────────────────────────────────────────┤
│ System Uptime: 99.8%        │ Response Latency: 0.8 sec │
│ Current Enquiries Queue: 3  │ Critical Alerts: 0        │
├─────────────────────────────────────────────────────────┤
│ Escalation Queue (Real-Time)                            │
│ ┌─────────────────────────────────────────────────────┐ │
│ │ CRITICAL (Clinician): 0 items                       │ │
│ │ HIGH (PALS): 2 items | Avg wait: 3 min            │ │
│ │ MEDIUM (PALS): 5 items | Avg wait: 8 min          │ │
│ │ SLA Compliance: CRITICAL 100% | HIGH 95% | MED 92%│ │
│ └─────────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────────┤
│ Hourly Enquiry Volume: [Chart over last 24 hours]      │
├─────────────────────────────────────────────────────────┤
│ Last Critical Incident: None (OK)                       │
│ Last System Error: 12 hours ago (resolved)              │
└─────────────────────────────────────────────────────────┘
```

**Update Frequency:** Real-time (every 60 seconds)

**Alert Conditions:**
- Uptime <99% → Alert PALS Manager + IT
- Response latency >2 sec (P50) → Alert System Administrator
- Escalation queue CRITICAL >5 min → Page on-call clinician
- Escalation queue HIGH SLA not met → Alert PALS Manager
- Error rate >1% → Alert System Administrator + Clinical Safety Officer

---

### Weekly Clinical Safety Dashboard

**Audience:** Clinical Safety Officer, Chief Medical Officer

**Frequency:** Updated daily; reviewed weekly

**Metrics displayed:**

```
┌──────────────────────────────────────────────────────┐
│ Weekly Clinical Safety Review (Week of Sept 11-17)   │
├──────────────────────────────────────────────────────┤
│ Safety Metrics                                        │
│ ├─ Hallucination Rate: 1.2% (Target <2%) ✓         │
│ ├─ Missed Escalation Rate: 0% (Target <1%) ✓       │
│ ├─ Inappropriate Escalation Rate: 8% (Target <10%) ✓│
│ └─ Patient Harm Incidents: 0 (Target 0) ✓           │
├──────────────────────────────────────────────────────┤
│ Accuracy & Quality                                    │
│ ├─ Retrieval Precision (Top-1): 88% (Target ≥90%)  │
│ │  ⚠️ BELOW TARGET — investigate low-performing FAQ │
│ ├─ Retrieval Precision (Top-3): 96% (Target ≥95%) ✓ │
│ └─ Patient Accuracy Rating: 94% ✓                    │
├──────────────────────────────────────────────────────┤
│ Escalation Analysis                                   │
│ ├─ Total Escalations: 145 (8.2% of 1,768 enquiries) │
│ ├─ Category A (Clinical): 12 escalations            │
│ │   - All appropriately routed to clinician         │
│ ├─ Category B (Urgent): 45 escalations              │
│ │   - 5 were appropriate; 40 routine queries        │
│ │   ⚠️ HIGH FALSE POSITIVE RATE — review triggers   │
│ └─ Category C (Routine): 88 escalations             │
│   - Knowledge base gaps identified in: scheduling,  │
│     test results, billing                           │
├──────────────────────────────────────────────────────┤
│ Incidents This Week: 0                               │
│ Audit Findings: 1 hallucination in test-result FAQ  │
│ │ → Action: Review source; retrain on medical terms │
└──────────────────────────────────────────────────────┘
```

---

### Monthly Governance Report

**Audience:** AI Governance Committee, Board

**Frequency:** Monthly (3rd Friday)

**Sections:**

1. **Executive Summary** (1 page)
   - System status (operational, issues)
   - Safety/accuracy (green/yellow/red)
   - Key recommendations

2. **Performance Summary** (1 page)
   - Uptime, latency, enquiry volume (trends)
   - Escalation metrics by category
   - SLA compliance

3. **Safety & Clinical Governance** (2 pages)
   - Incident summary (count, severity, resolution)
   - Accuracy metrics (retrieval precision, hallucination rate)
   - Bias/fairness assessment
   - Escalation appropriateness review

4. **Data Protection & Security** (1 page)
   - Breach incidents (count)
   - Access violations (count)
   - Security alerts/attacks detected
   - Vendor compliance (if applicable)

5. **Knowledge Base Quality** (1 page)
   - Source coverage and currency
   - Update activity (how many sources updated)
   - Gap analysis (missing topics)
   - Planned improvements

6. **Staff & Operations** (1 page)
   - Escalation SLA compliance by team
   - Staff training status
   - Staffing challenges or changes
   - Workload trends

7. **Risk Management** (1 page)
   - Risk register status (any new or escalated risks)
   - Residual risk vs. tolerance
   - Control effectiveness assessment
   - Recommendations for changes/improvements

8. **Appendices**
   - Detailed metrics tables
   - Incident details (if any)
   - Vendor performance (if applicable)
   - Budget/resource needs

---

## Alert & Response Procedures

### Alert Severity Levels

| Severity | Definition | Response | Notification |
|---|---|---|---|
| **CRITICAL** | System unavailable, patient harm risk, security breach | Immediate (within 1 min); escalate to senior management | SMS + phone call to on-call manager |
| **HIGH** | Performance degradation, safety concern, SLA breach | Within 15 minutes; alert relevant team | Email + in-system alert |
| **MEDIUM** | Quality issue, trend detected, escalation needed | Within 1 hour; analyse and plan response | Email to relevant lead |
| **LOW** | Minor issue, informational, monitoring data | Review during daily/weekly meetings | Daily digest report |

### Critical Alert Examples

| Alert | Trigger | Response |
|---|---|---|
| **System Down** | Uptime drops below 99% | Page infrastructure lead; activate fallback (manual queue) |
| **Patient Harm Incident** | Reported harm linked to chatbot response | Immediate incident response; clinical review; system check |
| **Security Breach** | Unauthorised data access or prompt-injection success | Security incident response; forensics; GDPR breach assessment |
| **Hallucination Storm** | Hallucination rate spikes to >5% in 1 hour | Escalation SLA breached; system pause if severe; source review |

---

## Data Collection & Privacy

### Enquiry Logging

**What is logged:**
- Enquiry text (full)
- Patient de-identified ID (e.g. NHS number hashed)
- Timestamp
- Source IP (for rate-limiting analysis; not retained long-term)
- Chatbot response (full)
- Escalation flag (if escalated)
- Source document retrieved (FAQ ID, not full text)
- Retrieval confidence score
- Response latency

**Retention:** 90 days (then deleted per data retention policy)

**Access:** PALS staff (to respond); Clinical Safety Officer (for audit); Quality Team (for monitoring); IT (for troubleshooting)

**Audit trail:** Access to enquiry logs is itself logged; monthly access review

### Patient Privacy

- Enquiry data not linked to patient demographics (age, sex, ethnicity) in logs
- Separately tracked data (complaints, feedback) linked only to hashed patient ID
- No enquiries retained for model training
- Biometric data (voice in SMS) not stored beyond session

---

## Continuous Improvement Process

### Weekly Huddle (Clinical Safety Officer + PALS Manager + Lead Developer)

**Purpose:** Review metrics, identify issues, plan improvements

**Topics:**
- High-escalation enquiry types → plan knowledge-base additions
- Quality audit findings → retrain staff, update sources
- System performance issues → technical fixes
- Staff feedback → process improvements

**Outcome:** Action list with owners and due dates

### Monthly Improvement Sprint (Lead Developer + Clinical Informatics Lead)

**Purpose:** Implement improvements to knowledge base, retrieval logic, escalation rules

**Activities:**
- Update/add knowledge-base sources for high-escalation topics
- Tune retrieval parameters (similarity threshold, top-N documents)
- Adjust escalation rules based on false-positive/negative analysis
- Implement staff feedback (UI improvements, clarity)

**Metrics:** Track improvement impact (escalation rate trend, accuracy improvement)

### Quarterly Comprehensive Review (AI Governance Committee)

**Purpose:** Strategic oversight; major system changes; governance adjustments

**Topics:**
- Annual safety/accuracy trends
- Bias/fairness assessment across patient populations
- Vendor performance and compliance (if applicable)
- Staff competency and training needs
- Process improvements (escalation, monitoring, governance)
- Recommendations for system enhancement or decommissioning

---

## Conditions for Monitoring Operationalisation

The monitoring system can be activated only when:

1. **Dashboards built:** Real-time and reporting dashboards live and accessible
2. **Metrics defined:** All metrics have clear definitions, calculation methods, and targets
3. **Alerts configured:** Critical and high alerts programmed; notification channels tested
4. **Staff trained:** Monitoring staff trained to interpret dashboards and respond to alerts
5. **Procedures documented:** Escalation and response procedures documented and accessible
6. **Baseline established:** First month of operation establishes performance baseline for trend analysis
7. **Data pipeline tested:** Logging, data extraction, and dashboard population tested end-to-end

---

## Document Control

| Item | Value |
|---|---|
| Document ID | AI-003-MONITORING-DASHBOARD-20260911 |
| Version | 1.0 (Draft) |
| Classification | Internal Governance |
| Owner | Clinical Safety Officer & Data Analytics Lead |
| Last Updated | 2026-09-11 |
| Next Review | 2026-12-11 or upon deployment |
