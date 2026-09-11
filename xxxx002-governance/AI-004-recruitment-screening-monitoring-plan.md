---
title: AI-004 AI Recruitment Screening — Monitoring & Continuous Assurance Plan
date: 2026-09-11
lifecycle_stage: Pilot Testing & Operation
scope: Metrics, procedures, and governance for continuous fairness and performance monitoring
decision_requested: Whether proposed monitoring approach will provide timely detection and escalation of fairness issues in operation
owner: Data Analytics Lead in consultation with AI Governance
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Draft for consultation
---

# AI-004 AI Recruitment Screening — Monitoring & Continuous Assurance Plan

## Executive Summary

This plan defines metrics, data sources, analysis methods, alert thresholds, and escalation procedures for continuous monitoring of fairness, discrimination, performance, and compliance during pilot testing and production operation.

**Monitoring Cadence:**
- **Real-time:** Automated alerts on fairness thresholds
- **Weekly:** Data pipeline refresh; metric recalculation
- **Monthly:** Fairness dashboard review and analysis
- **Quarterly:** Comprehensive fairness audit
- **Annual:** Governance and compliance review

---

## 1. Monitoring Data Sources

### 1.1 Recruitment System

**Data Captured:**
- Applicant demographics (name, contact, location)
- CV/application content (employment history, education, skills)
- AI score (numerical 0–100)
- Recommendation (interview yes/no)
- HR review date and reviewer name
- HR override decision (accept recommendation or override)
- Override rationale (if applicable)

**Data Extraction:** Automated daily export from recruitment system to analytics database; deduplicated and reconciled

**Data Quality:** Audit monthly; verify no corruption, missing values, or inconsistencies (>95% data completeness expected)

### 1.2 Equal Opportunities Data

**Data Captured (Voluntary from Applicants):**
- Age (inferred from date of birth or stated)
- Gender identity (male, female, non-binary, prefer not to say)
- Ethnicity (ethnicities from ONS categories or "prefer not to say")
- Disability status (yes, no, prefer not to say)
- Sexual orientation (if provided)
- Religion/belief (if provided)
- Pregnancy/maternity status (if disclosed)

**Data Collection:** Optional web form in recruitment portal; can be completed at any point during recruitment process

**Data Linkage:** Linked to applicant ID (secure hashing); stored separately from AI scoring model; linked only for fairness monitoring

**Data Quality:** Review monthly; flag any trends suggesting non-response bias (certain demographic groups less likely to provide information)

### 1.3 HR Decision Data

**Data Captured:**
- HR reviewer decision (accept AI recommendation or override)
- Override rationale (if applicable; e.g., "candidate has hidden potential", "employment gap explained")
- Interview offered / rejected
- Interview date and interviewer
- Final hiring decision (offered job / rejected / withdrawn)

**Data Collection:** Manual entry by HR staff in recruitment system; reviewed for consistency

**Data Quality:** Weekly audit; verify all decisions documented and rationale provided for overrides

### 1.4 Hiring Outcomes Data (If Available)

**Data Captured:**
- Hired: Yes / No
- Job title and department
- Start date
- (If available) job performance rating at 3 months, 6 months, 12 months
- Retention: still employed or left

**Data Collection:** Annual export from HR system; linked to applicant data by name and start date

**Limitations:** Available only for successfully hired candidates; performance and retention data may lag by 6–12 months

---

## 2. Fairness Metrics & Monitoring

### 2.1 Recommendation Rate by Demographic Group

**Definition:** % of applicants recommended for interview in each demographic cohort

**Formula:** (# applicants recommended for interview in cohort / # total applicants in cohort) × 100

**Calculation:** Weekly; disaggregated by:
- Age cohort (18–30, 31–45, 46–55, 56+)
- Gender (M, F, non-binary, not provided)
- Ethnicity (White British, Asian, Black, Mixed, Other, not provided)
- Disability status (Yes, No, not provided)

**Data Source:** Recruitment system; equal opportunities data

**Threshold:** Calculate disparate impact ratio (recommendation rate for group A / recommendation rate for reference group B):
- GREEN: Impact ratio ≥0.80 (no disparate impact detected)
- YELLOW: Impact ratio 0.70–0.79 (borderline; investigate)
- RED: Impact ratio <0.70 (potential unlawful discrimination; immediate escalation)

**Alert:** Automatically triggered if RED; manual review if YELLOW

**Statistical Significance:** Calculate 95% confidence interval for impact ratio; red alert only if lower bound <0.70 (not due to random variation with small sample size)

### 2.2 Mean AI Score by Demographic Group

**Definition:** Average AI score for each demographic cohort

**Formula:** (Sum of scores for cohort members / # cohort members)

**Calculation:** Weekly

**Data Source:** Recruitment system

**Analysis:**
- Plot score distribution by cohort (histogram)
- Compare mean, median, standard deviation across cohorts
- Calculate score gap (highest mean - lowest mean)
- Test significance with t-test (p<0.05 indicates significant gap)

**Threshold:**
- GREEN: Score gap <10 points and not statistically significant
- YELLOW: Score gap 10–15 points OR statistically significant
- RED: Score gap >15 points

**Alert:** YELLOW and RED trigger investigation; determine if due to qualification differences (acceptable) or bias (concerning)

### 2.3 Interview Conversion Rate by Demographic Group

**Definition:** % of recommended applicants offered interview for each demographic cohort

**Formula:** (# cohort members offered interview / # cohort members recommended) × 100

**Calculation:** Monthly (after sufficient interviews scheduled)

**Data Source:** Recruitment system

**Threshold:** Similar to recommendation rate; impact ratio ≥0.80 (GREEN), 0.70–0.79 (YELLOW), <0.70 (RED)

**Alert:** Tracks whether HR interview scheduling differs by demographic group (indicates potential human bias in final interview scheduling)

### 2.4 Hiring Rate by Demographic Group

**Definition:** % of cohort members offered and accepted job offers

**Formula:** (# cohort members hired / # cohort members total) × 100

**Calculation:** Monthly/Quarterly (after hiring decisions completed)

**Data Source:** HR system; linked to applicant data

**Threshold:** Impact ratio ≥0.80 (GREEN)

**Alert:** Tracks end-to-end hiring outcomes; indicates cumulative impact of AI + HR decisions + hiring manager decisions

**Note:** Hiring rate affected by multiple decision-points; may not reflect AI system alone (HR and hiring manager decisions also influential)

### 2.5 HR Override Rate by Demographic Group

**Definition:** % of AI recommendations overridden by HR for each cohort

**Formula:** (# overridden recommendations in cohort / # total recommendations in cohort) × 100

**Calculation:** Weekly

**Data Source:** Recruitment system (HR decision records)

**Analysis:**
- Calculate override rate by cohort
- Calculate override rate overall (should be >5%, indicating meaningful review)
- Analyse override rationale by cohort (are certain groups overridden for different reasons?)
- Test: Do women have higher override rate than men? (May indicate bias in HR judgment or AI scoring)

**Threshold:**
- GREEN: Override rate 5–15% overall; consistent across demographic groups (<5 percentage point difference)
- YELLOW: Override rate very low (<5%) indicating possible over-reliance on AI; or rates differ >5 percentage points by cohort
- RED: Override rate inconsistent by gender/age/ethnicity suggesting systemic HR bias (e.g., women overridden 20%, men 3%)

**Alert:** RED alert triggers investigation of HR decision quality and potential human bias

---

## 3. Performance Metrics

### 3.1 Model Accuracy (Overall)

**Definition:** % of applicants recommended by AI who are hired ("precision") and % of hired candidates who were recommended by AI ("recall")

**Formula:**
- Precision = (# hired who were recommended by AI / # total recommended) × 100
- Recall = (# hired who were recommended by AI / # total hired) × 100

**Calculation:** Quarterly (after hiring decisions complete)

**Data Source:** Recruitment system + HR hiring decisions

**Threshold:**
- GREEN: Precision >70% (most recommended candidates are successfully hired) and Recall >50% (system identifies majority of successful hires)
- YELLOW: Precision 50–70% or Recall 30–50%
- RED: Precision <50% or Recall <30%

**Alert:** If metrics degrade (e.g., precision drops from 75% to 60%), investigate model accuracy and revalidation

### 3.2 False-Negative Rate by Demographic Group

**Definition:** % of hired candidates in cohort who were NOT recommended by AI (missed good candidates)

**Formula:** (# hired in cohort but not recommended / # total hired in cohort) × 100

**Calculation:** Quarterly

**Data Source:** Recruitment system + hiring decisions

**Analysis:** Compare FNR across demographic cohorts; test for statistical significance; alert if FNR differs >10 percentage points between groups

**Threshold:**
- GREEN: FNR <20% overall; consistent across demographic groups
- YELLOW: FNR 20–30%
- RED: FNR >30% OR significantly different by demographic group (e.g., FNR 10% for men, 30% for women)

**Alert:** RED alert indicates model systematically missing qualified candidates from certain groups

---

## 4. Operational Metrics

### 4.1 Volume & Throughput

**Definition:** Number of applications screened, recommendations made, interviews offered, positions filled

**Calculation:** Weekly

**Data Source:** Recruitment system

**Tracking:** Ensure sufficient volume for fairness metrics to be statistically valid (target >50 applicants/month per job type)

### 4.2 Processing Time

**Definition:** Time from application submission to AI score, HR review, interview decision

**Calculation:** Weekly

**Data Source:** Recruitment system

**Threshold:** Alert if processing time spikes (may indicate system issues or bottlenecks)

### 4.3 System Availability

**Definition:** % of time system operational without errors or downtime

**Calculation:** Daily

**Data Source:** System monitoring logs

**Threshold:** Target >99% uptime; alert if <99%

---

## 5. Complaint & Incident Tracking

### 5.1 Discrimination Complaints

**Data Captured:**
- Complaint date and complainant
- Complaint type (age discrimination, gender discrimination, disability discrimination, etc.)
- Complaint description and specific concern
- Investigation outcome (substantiated / not substantiated / inconclusive)
- Remediation action (applicant reconsideration, model adjustment, system suspension, etc.)

**Calculation:** Ongoing; tracked in incidents database

**Analysis:** Monthly and quarterly
- Trend analysis: Are complaints increasing or decreasing?
- Demographic trends: Are certain groups filing more complaints?
- Root cause analysis: What are most common complaint types? Model bias, HR bias, or other factors?

**Alert:** Any discrimination complaint triggers investigation and escalation to AI Governance

### 5.2 Data Protection Incidents

**Data Captured:**
- Incident type (unauthorized access, data breach, retention violation, etc.)
- Date and description
- Data affected (number of applicants, types of data)
- Investigation and remediation

**Calculation:** Ongoing; reported monthly

**Alert:** Any confirmed data breach triggers notification (to ICO within 72 hours if high risk)

### 5.3 Applicant Concerns

**Data Captured:**
- Applicant request for explanation of score
- Applicant request for human review (alternative to AI)
- Applicant feedback on fairness or transparency

**Calculation:** Monthly summary

**Analysis:** Trends in explanations requested (are certain groups requesting more often?), satisfaction with human review alternative

---

## 6. Monitoring Dashboard

### 6.1 Dashboard Components

**Real-Time/Weekly Dashboard:**
- Recommendation rate by demographic group (with impact ratios and alerts)
- Mean AI score by group (with score gaps and visual distribution)
- HR override rate by group
- Volume and throughput metrics
- System status (uptime, errors)

**Monthly Review Dashboard:**
- Fairness metrics summary (red/yellow/green status)
- Interview conversion and hiring rate by demographic group
- Complaints and concerns summary
- Recommendations for investigation or action

**Quarterly Audit Dashboard:**
- False-negative rates by demographic group
- Model accuracy (precision, recall)
- Complaint trends and root cause analysis
- Incidents and remediation status
- Fairness audit findings and recommendations

### 6.2 Dashboard Access & Governance

**Access:** AI Governance Lead, Data Analytics Lead, HR Manager (read-only); HR Director and CIO (executive summary)

**Reviews:** 
- Weekly: Data Analytics Lead (technical review; verify data quality)
- Monthly: AI Governance Lead + HR Manager (fairness review; discussion of alerts and actions)
- Quarterly: AI Governance Committee (governance review; audit findings)

**Alerts:** Red alerts (impact ratio <0.70, score gap >15, etc.) sent immediately to AI Governance Lead via email; trigger investigation

---

## 7. Investigation & Escalation

### 7.1 Investigation Trigger

**Automatic Investigation Triggered By:**
- Recommendation rate or interview rate impact ratio <0.80 (YELLOW alert)
- Mean score gap >15 points
- HR override rate inconsistent by demographic group (>5 percentage point difference)
- False-negative rate >10 percentage points difference between demographic groups
- Any discrimination complaint
- Any data protection incident

### 7.2 Investigation Procedure

**Step 1 — Initial Assessment (Within 2 Days):**
- AI Governance Lead reviews alert and raw data
- Assess: Is alert due to data quality issue, random variation, or genuine concern?
- If likely genuine, proceed to Step 2

**Step 2 — Root Cause Analysis (Within 5 Days):**
- Data Science Lead + AI Governance Lead investigate:
  - Is it model bias? (score gap for demographic group in model training/testing)
  - Is it proxy variable? (employment gap, education, etc. correlates with protected characteristic)
  - Is it HR bias? (override decisions inconsistent by demographic group)
  - Is it applicant pool difference? (certain demographic groups have fewer qualifications; lower scores justified)
- Analyse scoring patterns; interview HR staff if needed

**Step 3 — Remediation Planning (Within 10 Days):**
- Determine remediation:
  - If model bias: retrain model, adjust thresholds, remove proxy variables
  - If HR bias: retrain HR staff, escalate to HR Director
  - If applicant pool: may be acceptable if justified by actual qualification differences
  - If data quality: correct data and recalculate metrics
- Document investigation findings; plan remediation with owner and timeline

**Step 4 — Escalation to HR Director & Executive (If Serious):**
- If potential Equality Act 2010 violation suspected, escalate to HR Director and DPO
- Determine: Model adjustment, temporary pause, or suspension?
- Communicate findings to applicants if discrimination claim substantiated (remediation offer: reconsideration, apology)

### 7.3 Escalation Thresholds

| Alert Type | Threshold | Action | Escalation |
|---|---|---|---|
| **Impact Ratio** | <0.70 | Immediate investigation; potential model suspension | AI Governance → HR Director → Board |
| **Score Gap** | >15 points | Investigation; determine bias or qualification difference | AI Governance → Data Science |
| **Override Rate Inconsistency** | >5pp between groups | HR review; assess human bias | AI Governance → HR Director |
| **False-Negative Rate Gap** | >10pp between groups | Model review; potential retraining | AI Governance → Data Science |
| **Discrimination Complaint** | Any substantiated complaint | Investigation; remediation plan | AI Governance → HR Director → Legal |
| **Data Breach** | Any confirmed breach | Incident response; ICO notification if required | Data Protection Officer → Board |

---

## 8. Remediation Actions

### 8.1 Model Adjustments

**If Model Bias Detected:**
- [ ] Identify specific source of bias (training data imbalance, proxy variable, model architecture)
- [ ] Rebalance training data (increase representation of underrepresented groups)
- [ ] Remove or adjust proxy variables (e.g., don't use "years of experience"; use "relevant experience")
- [ ] Adjust scoring thresholds (e.g., lower threshold for historically disadvantaged groups if justified by fairness principle)
- [ ] Retrain model on adjusted data/parameters
- [ ] Revalidate fairness; test impact ratios
- [ ] Roll out adjusted model; monitor for improvement

**Timeline:** 4–6 weeks from identification to rollout

### 8.2 HR Staff Retraining

**If HR Bias Detected (Inconsistent Override Rates):**
- [ ] Review problematic override decisions with HR staff member
- [ ] Discuss fairness principles and avoiding unconscious bias
- [ ] Provide additional training on identifying qualified candidates despite non-traditional backgrounds
- [ ] Increase monitoring of HR staff's override decisions for period (weekly audit)
- [ ] Escalate if bias continues

**Timeline:** Immediate retraining; monitoring for 4 weeks

### 8.3 System Suspension

**If Serious Discrimination Risk Detected:**
- [ ] Pause AI scoring for affected role/demographic group while investigating
- [ ] Manual HR review of all pending recommendations
- [ ] Offer reconsideration to recently rejected applicants from affected group
- [ ] Complete investigation and remediation before resuming AI scoring
- [ ] Communicate to applicants affected (transparency, fairness)

**Timeline:** Can be implemented immediately; resolution within 4 weeks typical

---

## 9. Monitoring Cadence & Governance

### 9.1 Monitoring Schedule

| Frequency | Activity | Owner | Audience |
|---|---|---|---|
| **Daily** | System status check (uptime, errors) | IT Operations | IT Leadership |
| **Weekly** | Fairness metrics refresh; alert review | Data Analytics | AI Governance Lead |
| **Weekly** | Fairness dashboard technical review | Data Analytics Lead | Internal (technical) |
| **Monthly** | Fairness dashboard review & discussion | AI Governance + HR | AI Governance Committee |
| **Monthly** | Compliance audit (data retention, access) | Data Protection Officer | DPO + AI Governance |
| **Monthly** | Complaints summary | HR Manager | HR Director + AI Governance |
| **Quarterly** | Comprehensive fairness audit | Independent Auditor | AI Governance Committee |
| **Quarterly** | Incident trends analysis | AI Governance | AI Governance Committee |
| **Annual** | Governance review & DPIA update | AI Governance | Board + Audit Committee |

### 9.2 Governance & Accountability

| Role | Responsibility |
|---|---|
| **Data Analytics Lead** | Dashboard operation, metric calculation, data quality; alert to AI Governance Lead |
| **AI Governance Lead** | Monitor alerts, initiate investigations, track remediation, escalate serious concerns |
| **Data Science Lead** | Respond to model bias alerts, conduct root cause analysis, plan/execute model adjustments |
| **HR Manager/Director** | Respond to HR bias alerts, retrain staff, investigate complaints, approve system adjustments |
| **Data Protection Officer** | Compliance monitoring, data protection incidents, legal review |
| **Independent Auditor** | Quarterly fairness audit, verify investigation rigor, recommend actions |
| **Executive Sponsorship** | Approve serious remediation (system suspension, model retirement), escalate to Board |

---

## 10. Continuous Improvement

### 10.1 Metric Refinement

Review metrics quarterly; adjust based on:
- Industry best practices (compare with similar AI systems)
- Regulatory guidance (ICO, Equality and Human Rights Commission)
- Operational learnings (which alerts most predictive of actual discrimination?)
- Stakeholder feedback (HR, applicants, audit)

### 10.2 Threshold Adjustment

Review alert thresholds annually:
- Are current thresholds triggering appropriate level of investigation?
- Are thresholds too loose (missing real issues) or too strict (false alarms)?
- Adjust based on actual outcomes (e.g., if red alerts always result in model adjustment, threshold appropriate; if most red alerts are false alarms, lower threshold)

### 10.3 Monitoring Technology

- Evaluate fairness monitoring tools and platforms annually (new tools emerging regularly)
- Consider upgrading dashboard for better automation, real-time alerts, predictive analytics
- Balance sophistication with usability (dashboard must be accessible to non-technical users)

---

## 11. Documentation & Records

**Records Maintained:**
- Weekly fairness dashboards (archived)
- Monthly monitoring reports
- Quarterly audit reports
- Investigation summaries and remediation plans
- Incident log (all concerns, complaints, escalations)
- Monitoring procedure documentation (how metrics calculated, alert logic, etc.)

**Retention:** 7 years (employment records)

---

## 12. Review & Approval

| Role | Approval |
|---|---|
| **Data Analytics Lead** | ✓ Approve monitoring feasibility and data sources |
| **AI Governance Lead** | ✓ Approve monitoring scope and alert thresholds |
| **HR Director** | ✓ Approve HR-related monitoring and escalation procedures |
| **AI Governance Committee** | ✓ Approve monitoring plan |

---

## 13. Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | AI Governance | Draft for consultation |

---

**Document Classification:** Internal Use Only — AI Governance  
**Retention Period:** 7 years  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11
