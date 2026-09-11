---
title: AI-004 AI Recruitment Screening — Assurance Plan
date: 2026-09-11
lifecycle_stage: Design, Testing, Operation
scope: Testing and verification approach to provide assurance that governance controls are operating effectively
decision_requested: Whether proposed assurance activities will adequately demonstrate control effectiveness and provide evidence for governance approval
owner: Head of AI Governance
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Ready for approval
---

# AI-004 AI Recruitment Screening — Assurance Plan

## Executive Summary

This plan defines how governance controls will be tested and verified during design, pilot testing, and operation to provide assurance that the AI recruitment screening system operates fairly, lawfully, and safely.

**Assurance Approach:** Independent, ongoing testing throughout lifecycle using multiple methods (design review, testing, monitoring, audit)

**Timeline:** Design review → Pilot testing → Pre-production audit → Quarterly operational audits

---

## 1. Design Phase Assurance (Pre-Pilot)

### 1.1 Governance Documentation Review

**Objective:** Verify governance artefacts are adequate and approval-ready

**Control Tested:** All governance controls (design adequacy)

**Test Method:**
- [ ] Risk Assessment reviewed by independent reviewer for completeness and risk scoring accuracy
- [ ] Control Matrix reviewed for clarity, specificity, and feasibility
- [ ] Fairness Assessment Framework reviewed for methodological rigor
- [ ] DPIA reviewed by independent DPO for UK GDPR compliance
- [ ] Gap analysis: identify any missing risks, controls, or evidence requirements

**Evidence:** Documentation review sign-off; gap list and remediation plan

**Acceptance Criteria:**
- No HIGH-severity gaps identified (gaps addressed before pilot)
- MEDIUM-severity gaps have remediation plan with owner and deadline
- All critical controls have documented procedures and assigned owners
- Approval by AI Governance Committee and DPO

**Timeline:** 2 weeks

---

### 1.2 Model Fairness Assessment (Independent)

**Objective:** Conduct fairness testing before any applicant data processed (Control CON-001)

**Control Tested:** REC-AI-001 (age), REC-AI-002 (gender), REC-AI-003 (ethnicity), REC-AI-004 (disability), REC-AI-006 (proxy variables), REC-AI-010 (underrepresented groups)

**Test Method:** Independent fairness auditor follows Fairness Assessment Framework Phase 1:
1. Training data audit (composition, representativeness, known biases)
2. Model performance testing (accuracy, false-positive/negative rates by demographic cohort)
3. Disparate impact calculation (impact ratio ≥0.8 for all groups?)
4. Proxy variable audit (identified, correlation tested, business justification documented?)
5. Explainability assessment (explanations clear, accurate, actionable?)

**Evidence:** Fairness Assessment Report with:
- Training data composition table
- Model performance metrics by demographic group
- Disparate impact ratios with confidence intervals
- Proxy variable analysis
- Explainability assessment
- Recommendation (proceed, proceed with caution, do not proceed)

**Acceptance Criteria:**
- No statistically significant disparate impact identified (p>0.05)
- False-negative rates <15% and <10 percentage points between demographic cohorts
- All high-correlation proxy variables have documented business justification
- Explanations clear and accurate for sample applicants (≥80% understandable)
- Independent auditor sign-off

**Timeline:** 4 weeks

---

### 1.3 GDPR Data Protection Review

**Objective:** Verify data protection controls implemented before data processing begins (Control CON-002, CON-005)

**Control Tested:** REC-AI-008 (data protection violations)

**Test Method:**
1. Consent form review: Does consent clearly describe AI use and data processing? Can applicants easily understand what they're consenting to?
2. Privacy notice review: Is privacy notice clear, accessible, provided before application submission?
3. Data minimisation audit: Are sensitive fields (name, ethnicity, disability) excluded from scoring model or properly controlled? (code review)
4. Data separation test: Are optional equal opportunities fields stored separately from scoring model? (technical testing)
5. DPA review: Are Data Processing Agreements in place with vendor/cloud provider with appropriate data protection terms?
6. Retention policy test: Is automated deletion configured correctly? Test with sample records.
7. Incident response procedure review: Is breach notification procedure documented and tested?

**Evidence:**
- Consent form and privacy notice (final versions)
- Code review confirming data minimisation
- DPA copies (signed with vendor/cloud provider)
- Data retention policy and automated deletion test results
- Incident response procedure (documented)
- DPO sign-off

**Acceptance Criteria:**
- Consent form and privacy notice reviewed and approved by DPO and Legal
- Consent obtained from sample applicants (test workflow)
- Code review confirms no sensitive data passed to scoring model
- Automated deletion tested; confirmed working
- DPA signed (if vendor/cloud provider)
- Incident response procedure published and tested

**Timeline:** 3 weeks

---

### 1.4 HR Procedure & Training Review

**Objective:** Verify HR procedures documented and training complete before pilot (Control CON-003, CON-007)

**Control Tested:** REC-AI-009 (human oversight failure)

**Test Method:**
1. HR procedure review: Is no-auto-reject procedure documented? Clear review checklist? Override documentation process defined?
2. Training review: Is training curriculum comprehensive (AI basics, bias, discrimination, fairness, override procedures)? Training materials clear?
3. Knowledge assessment: Do sample HR staff (n=5) understand training? Can they identify bias signals? Can they explain override decisions?
4. Procedure walk-through: Test HR review procedure with sample applicants (end-to-end); verify procedure followed correctly.

**Evidence:**
- HR procedure (final version, approved by HR Director)
- Training materials and curriculum
- Training attendance records
- Assessment results (sample HR staff understanding)
- Procedure walk-through results

**Acceptance Criteria:**
- HR procedure published and approved
- ≥95% of pilot HR staff trained
- ≥80% pass knowledge assessment
- Procedure walk-through completed successfully (no blockers)

**Timeline:** 2 weeks

---

## 2. Pilot Testing Phase Assurance

### 2.1 Fairness Metrics Monitoring (Ongoing During Pilot)

**Objective:** Monitor for fairness and discrimination on live applicant data; escalate concerns

**Control Tested:** CON-006 (bias monitoring dashboard); REC-AI-001/002/003/004/006/010 (discrimination risks)

**Test Method:** Automated monitoring dashboard (updated weekly)
- Recommendation rate by demographic group (age, gender, ethnicity if available, disability if available)
- Mean AI score by group
- HR override rate by group
- Interview conversion rate by group
- Disparate impact ratios; alert if <0.80

**Evidence:** Weekly fairness dashboards and alerts

**Acceptance Criteria:**
- Dashboard operational by week 2 of pilot
- No statistically significant disparate impact detected (impact ratio ≥0.80)
- HR override rate >5% and consistent across demographic groups
- No escalation alerts requiring investigation
- If alert triggered: investigation completed within 5 days; findings documented

**Timeline:** Ongoing throughout pilot (8–12 weeks)

---

### 2.2 HR Procedure Compliance Audit

**Objective:** Verify HR staff following review procedure; human oversight effective

**Control Tested:** CON-003 (human review procedure)

**Test Method:** Monthly audit of sample HR decisions (n=10–20 per month)
- Verify HR reviewed AI score and applicant data before recommendation
- Verify HR documented decision and override rationale (if applicable)
- Assess decision quality (is override justified? Is bias signal identified?)
- Calculate override rate; compare with baseline (<5% vs. >10% suggests under/over-reliance on AI)
- Analyse patterns: Do override rates differ by demographic group? If yes, investigate bias.

**Evidence:** Monthly audit reports with:
- Sample decisions audited
- Compliance with procedure (100% expected)
- Override rate and patterns
- Decision quality assessment

**Acceptance Criteria:**
- 100% of sampled decisions reviewed by HR (no auto-rejections found)
- Override rate 5–10% (indicating meaningful review)
- Override rate consistent across demographic groups (<5% difference)
- No quality issues identified (overrides justified and documented)

**Timeline:** Monthly during pilot

---

### 2.3 Data Protection Compliance Audit

**Objective:** Verify data protection controls operating correctly

**Control Tested:** CON-002, CON-005 (data minimisation, GDPR compliance)

**Test Method:** Monthly audit
- Verify data retention schedule followed (unsuccessful applicants deleted after 6 months; successful hires after 2 years)
- Verify no sensitive data in scoring logs or audit trails
- Check access logs (who accessed applicant data? appropriate access?)
- Verify DPA terms honoured (if vendor, confirm applicant data not used for secondary purposes)
- Track any data protection concerns or near-misses

**Evidence:** Monthly compliance audit reports

**Acceptance Criteria:**
- Data deleted per retention policy (100% of scheduled deletions completed)
- No sensitive data leakage in logs or audit trails
- All data access by authorised staff only
- No vendor data misuse detected
- Zero data breaches or near-misses

**Timeline:** Monthly during pilot

---

### 2.4 Applicant Feedback & Complaints

**Objective:** Gather applicant feedback on AI use, fairness, transparency

**Control Tested:** CON-010 (discrimination complaint procedure); overall fairness and transparency

**Test Method:**
- Post-decision survey (sample of rejected applicants): "Were you informed AI was used? Do you feel decision was fair? Would you like explanation?"
- Complaints tracking: Any applicants request explanation, challenge decision, or file complaint?
- Focus group (if possible): Interview sample of rejected applicants to identify concerns

**Evidence:**
- Survey results (n=30–50 applicants)
- Complaints log and investigation summaries
- Focus group notes

**Acceptance Criteria:**
- ≥80% of surveyed applicants aware AI used
- ≥70% feel decision was fair or acceptable
- <5% request explanation or file complaint
- Any complaints investigated and resolved

**Timeline:** Conducted mid-pilot and end-of-pilot

---

## 3. Pre-Production Phase Assurance

### 3.1 Comprehensive Fairness Audit (Post-Pilot)

**Objective:** Independent comprehensive audit of pilot outcomes; determine if model safe for production

**Control Tested:** All discrimination risks (REC-AI-001/002/003/004/005/006/010)

**Test Method:** (See Fairness Assessment Framework Phase 3)
1. Pilot outcome analysis (recommendation rate, hire rate, job performance by demographic group)
2. Statistical testing (chi-square, logistic regression, confidence intervals)
3. HR override decision analysis (rates, rationale, patterns)
4. Hiring outcome analysis (job performance, retention by demographic group)
5. Legal compliance review (Equality Act 2010, GDPR)
6. Recommendations (approve for production, approve with enhanced monitoring, do not approve)

**Evidence:** Comprehensive fairness audit report with statistical analysis, findings, and recommendations

**Acceptance Criteria:**
- No statistically significant disparate impact identified (p>0.05 for all demographic groups)
- Hiring outcomes not systematically disadvantaging protected groups
- False-negative rates acceptable (<15% overall, <10 point gap between groups)
- Legal compliance confirmed by independent legal review
- Independent auditor recommendation to approve for production

**Timeline:** 2–3 weeks post-pilot completion

---

### 3.2 Production Readiness Review

**Objective:** Verify all controls ready for operation; no blockers to production deployment

**Control Tested:** All governance controls

**Test Method:** Production readiness checklist
- [ ] Fairness assessment approved; all findings addressed
- [ ] GDPR compliance verified; DPIA signed off by DPO
- [ ] Data security controls implemented and tested
- [ ] HR procedures documented and staff trained
- [ ] Monitoring dashboard operational and tested
- [ ] Incident response procedures documented and tested
- [ ] Escalation procedures defined and communicated
- [ ] Vendor/cloud provider DPA signed (if applicable)
- [ ] Applicant communication strategy implemented (privacy notice, consent)
- [ ] Audit committee and Board approval obtained

**Evidence:** Production readiness checklist (all items signed off)

**Acceptance Criteria:**
- All checklist items completed (no red items outstanding)
- All HIGH-severity findings from audits addressed
- MEDIUM-severity findings have remediation plan in progress
- Stakeholder approvals obtained (AI Governance Committee, HR Director, DPO, Executive Sponsorship)

**Timeline:** 1 week before production deployment

---

## 4. Operational Phase Assurance (Post-Launch)

### 4.1 Quarterly Independent Fairness Audit

**Objective:** Continuous assurance of fairness in operation; early detection of bias or discrimination

**Control Tested:** All discrimination risks; CON-006 (monitoring dashboard)

**Test Method:** (See Fairness Assessment Framework Phase 4)
- Statistical analysis of fairness metrics (recommendation rate, score distribution, interview rate, hiring rate by demographic group)
- Disparate impact testing; alert if impact ratio <0.80
- Complaint and escalation analysis (trends in discrimination concerns)
- Root cause analysis (if disparities detected: model bias, proxy variables, human bias, applicant pool changes?)
- Recommendations (continue, enhanced monitoring, model adjustment, system pause)

**Evidence:** Quarterly fairness audit reports

**Acceptance Criteria:**
- No statistically significant disparate impact identified (p>0.05)
- If impact ratio 0.70–0.80 for any group: investigation completed, root cause determined, remediation plan in place
- If impact ratio <0.70: escalate to Executive Sponsorship; consider model suspension pending investigation
- All recommendations from prior audits tracked; status documented

**Timeline:** Quarterly (every 13 weeks); report delivered within 2 weeks of quarter end

---

### 4.2 Monthly Monitoring Dashboard Review

**Objective:** Routine review of fairness metrics; early warning of anomalies

**Control Tested:** CON-006 (monitoring dashboard)

**Test Method:** Monthly review of dashboard by AI Governance Lead and HR Manager
- Review fairness metrics (recommendation rate, scores, override rates by demographic group)
- Any alerts triggered? If yes, investigate and document
- Trends: are metrics improving or degrading?
- Escalation: any concerns requiring investigation?

**Evidence:** Monthly dashboard reports

**Acceptance Criteria:**
- Metrics reviewed and signed off by AI Governance Lead
- Any alerts investigated and findings documented
- No escalation required (or escalation completed) for routine months

**Timeline:** Monthly review meetings (held first week of each month)

---

### 4.3 Compliance Audit (Annual)

**Objective:** Comprehensive annual review of all governance controls; update compliance assessments

**Control Tested:** All controls

**Test Method:** Annual compliance audit
- Design adequacy: Are control designs still appropriate? Any changes needed?
- Implementation: Are controls implemented as designed? Any gaps?
- Operating effectiveness: Are controls functioning correctly? Evidence of effectiveness?
- Compliance: GDPR, Equality Act 2010, other regulatory requirements — still compliant?
- Incidents: Any data breaches, discrimination complaints, operational issues during year?
- Model changes: If model updated/retrained, fairness impact assessed?

**Evidence:** Annual compliance audit report with:
- Control assessment (design, implementation, effectiveness) for each control
- Compliance status (GDPR, Equality Act 2010)
- Incident summary
- Remediation actions and status
- Recommendations

**Acceptance Criteria:**
- All controls assessed; effectiveness documented
- No material control gaps (MEDIUM or lower severity)
- GDPR and Equality Act 2010 compliance confirmed
- Incidents tracked; root causes determined; remediation completed
- Recommendations prioritised and assigned owners

**Timeline:** Annual (conducted in Q4 for Board review)

---

### 4.4 Complaints & Incident Management

**Objective:** Track and respond to applicant complaints and fairness concerns

**Control Tested:** CON-010 (discrimination complaint procedure); overall fairness governance

**Test Method:**
- Incident logging: All complaints, concerns, and fairness alerts logged in incidents database
- Investigation: Each incident investigated within defined timeline (5 days for initial assessment; 20 days for full investigation)
- Escalation: Serious incidents (potential discrimination, data breach) escalated to AI Governance and HR Director
- Remediation: Actions taken to address incident (applicant reconsideration, model adjustment, system suspension, etc.)
- Trend analysis: Quarterly analysis of incident trends (are certain demographic groups filing more complaints?)

**Evidence:** Incident log with investigation summaries and remediation status

**Acceptance Criteria:**
- All incidents logged and tracked
- Investigations completed within defined timeline
- Serious incidents escalated and resolved
- Trend analysis conducted quarterly; patterns identified and escalated
- No repeat incidents (if issue resolved, does not recur)

**Timeline:** Ongoing; quarterly trend reporting

---

## 5. Independent Audit Function

### Audit Independence

Audits must be conducted by **independent auditor** (not involved in model development, HR decisions, or IT operations):
- External audit firm with fairness and AI expertise
- Or internal audit function (separate from operational teams)
- NOT the model vendor, developer, or HR staff

### Auditor Qualifications

- Experience in AI fairness, discrimination, and bias testing
- Knowledge of UK employment law (Equality Act 2010) and GDPR
- Technical competency (statistics, model evaluation)
- No conflicts of interest with AI system

### Audit Scope

- Fairness and discrimination risks (primary focus)
- Data protection compliance (secondary focus)
- Control operating effectiveness (secondary focus)

### Audit Rights

- Access to recruitment data (applicant scores, HR decisions, outcomes)
- Access to model internals (model code, training data, feature importance)
- Interviews with HR staff, AI team, management
- System access (logs, audit trails, monitoring dashboard)
- Right to recommend model adjustment or suspension

---

## 6. Governance & Escalation

### Escalation Paths

**LEVEL 1 — Routine Alert (Dashboard Monitoring):**
- Triggered: Fairness metric alert (e.g., impact ratio <0.80)
- Owner: Data Analytics Lead
- Action: Initial investigation; rule out data quality issues
- Timeline: Within 5 days
- Escalation: If confirmed, escalate to Level 2

**LEVEL 2 — Investigation Required (Month 1):**
- Owner: AI Governance Lead + Data Science Lead
- Action: Root cause analysis; determine if model bias, proxy variable, or other cause
- Timeline: Within 10 days
- Escalation: If serious concern confirmed, escalate to Level 3

**LEVEL 3 — Serious Concern (Month 2):**
- Owner: HR Director + AI Governance Lead + DPO
- Action: Legal review; determine if potential Equality Act 2010 violation; plan remediation
- Timeline: Within 20 days
- Escalation: If material risk, escalate to Level 4

**LEVEL 4 — Executive Decision (Month 3):**
- Owner: Executive Sponsorship (Trust Board)
- Action: Approve remediation plan; may decide to pause or suspend system
- Timeline: Immediate

---

## 7. Approval

| Role | Approval Authority |
|---|---|
| **Head of AI Governance** | ✓ Review plan; approve assurance approach |
| **AI Governance Committee** | ✓ Approve assurance plan and audit independence |
| **Data Protection Officer** | ✓ Approve data protection audit approach |
| **HR Director** | ✓ Approve HR procedure testing and complaints handling |

---

## 8. Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | AI Governance | Draft for approval |

---

**Document Classification:** Internal Use Only — AI Governance  
**Retention Period:** 7 years  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11
