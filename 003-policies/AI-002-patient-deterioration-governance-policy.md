# AI Governance Policy: Patient Deterioration Prediction System
## SentinelAI Governance Portfolio

**Document Status:** Draft  
**Date:** 2026-09-11  
**Review Date:** 2026-12-11  
**Prepared by:** AI Governance Board  
**Approval Authority:** AI Governance Board  
**Policy ID:** GP-002-PatientDeterioration-001  
**Jurisdiction:** NHS Trust (UK)

---

## 1. Policy Statement

This policy establishes governance, accountability, and decision-making authority for the development, validation, deployment, monitoring, and retirement of the AI-powered Patient Deterioration Prediction System. The policy applies the NIST AI Risk Management Framework 1.0 and UK governance standards to ensure the system operates safely, fairly, transparently, and accountably within the Trust's risk tolerance.

The system is intended to support clinicians in identifying hospitalised patients at elevated risk of clinical deterioration (unplanned critical event, cardiac arrest, unplanned ICU admission, or death) within a defined timeframe (24–72 hours), enabling earlier clinical assessment and intervention. The system augments clinical judgment; clinicians retain full accountability for patient assessment, treatment decisions, and escalation.

---

## 2. Scope and Applicability

**In Scope:**
- The AI model and its inputs (vital signs, observations, laboratory results, clinical events from the Electronic Patient Record)
- Data pipelines and integration with the EPR
- Alerting and notification systems
- Vendor-supplied or cloud-hosted infrastructure
- All lifecycle stages from use-case assessment through retirement

**Exclusions:**
- Electronic Patient Record governance (assumed covered separately)
- Patient consent mechanisms and privacy notices (addressed in Privacy Impact Assessment)
- Clinical training curricula and change-management programmes (addressed in separate Clinical Implementation Plan)
- Legacy Early Warning Score (EWS) systems

**Applicability:**
- AI Governance Board and governance sponsors
- Clinical Safety Lead
- Privacy Officer and Data Steward
- Information Security and vendor managers
- Clinical informatics and model developers
- Clinical staff using the system (nurses, doctors, ward managers)
- Vendor and cloud infrastructure providers

---

## 3. Governance Objectives

This policy establishes:

1. **Accountability:** Clear ownership and decision authority for system performance, safety, incidents, and retirement
2. **Risk Governance:** Risk tolerance definition, proportionate controls, and evidence-based decision-making
3. **Transparency:** Public documentation of governance decisions, evidence, rationale, and review dates
4. **Auditability:** Audit trail of major decisions, approvals, incidents, and governance reviews
5. **Safety:** Procedures to detect, escalate, contain, and remediate incidents affecting patient safety
6. **Fairness:** Assessment and monitoring of performance across patient demographic and clinical subgroups
7. **Privacy:** Compliance with UK GDPR, Data Protection Act 2018, and NHS data-protection standards
8. **Resilience:** System availability, failure-mode management, and business continuity

---

## 4. Governance Structure and Roles

### 4.1 AI Governance Board (Approval Authority)

**Composition:** Chief Medical Officer (Chair), Chief Nurse, Chief Information Officer, Privacy Officer, Head of Clinical Informatics, Clinical Safety Lead, AI Governance Lead

**Responsibilities:**
- Approve AI Governance Policy and material amendments
- Approve use-case assessment and recommend proceeding or stopping
- Approve risk tolerance statement and acceptance of residual risks
- Establish and approve pre-deployment approval gates
- Review and approve major governance decisions (vendor selection, model validation results, pilot outcomes)
- Review quarterly performance reports and incidents
- Authorise system suspension, restriction, or retirement
- Escalate unresolved governance issues to Executive Leadership or Board

**Authority:** AI Governance Board holds final approval authority for all major governance decisions. No material changes to system scope, design, model, vendor, or deployment proceed without Board approval.

**Cadence:** Monthly meetings; extraordinary meetings on incident or escalation

**Decision Record:** All decisions documented in Governance Decision Register with owner, date, rationale, and review date

---

### 4.2 Clinical Safety Lead (System Owner)

**Responsibilities:**
- Define clinical requirements and acceptance criteria (sensitivity, specificity, FNR, FPR thresholds)
- Sponsor clinical safety assessment and validation study
- Approve clinical safety findings before deployment
- Receive and escalate clinical incidents
- Authorise temporary system suspension pending investigation
- Review quarterly clinical audit reports
- Recommend system modification, restriction, or retirement based on safety evidence
- Provide clinical governance oversight throughout system lifecycle

**Accountability:** Clinical Safety Lead is the named owner accountable to the Trust for system safety and clinical outcomes

**Authority:** May suspend system for up to 72 hours pending incident investigation; escalates to AI Governance Board for extended suspension or retirement

---

### 4.3 Privacy Officer (Data Protection Compliance)

**Responsibilities:**
- Conduct or sponsor Data Protection Impact Assessment (DPIA)
- Determine lawful basis for continuous data processing
- Approve data retention and deletion procedures
- Review and approve vendor Data Processing Addendum (DPA)
- Assess and approve patient information and consent approach
- Receive and escalate personal data breaches
- Audit vendor and cloud provider compliance with data-protection terms

**Accountability:** Privacy Officer is accountable for UK GDPR and Data Protection Act 2018 compliance

**Authority:** May recommend suspension of system if data-protection obligations are not met

---

### 4.4 Information Security Lead (System and Data Security)

**Responsibilities:**
- Assess vendor and cloud infrastructure security posture
- Approve vendor security certifications and controls (encryption, access control, audit logging, incident management)
- Review and approve vendor Service Level Agreement (SLA) and disaster-recovery plan
- Establish monitoring for security incidents (unauthorised access, data exfiltration, system compromise)
- Escalate security incidents to incident response team

**Accountability:** Information Security Lead is accountable for system and data security throughout lifecycle

**Authority:** May recommend suspension of system if security controls are inadequate or breach detected

---

### 4.5 Clinical Data Steward (Operational Monitoring)

**Responsibilities:**
- Establish and maintain operational performance monitoring (daily/weekly/monthly)
- Track key performance metrics: alert generation rate, alert override rate, adverse outcomes in alerted vs non-alerted patients
- Stratify performance by patient subgroups (age, sex, ethnicity, comorbidity) to detect performance degradation
- Generate monthly performance reports for Clinical Safety Lead and AI Governance Board
- Escalate performance concerns triggering alert thresholds to Clinical Safety Lead
- Support clinical audit programme

**Accountability:** Clinical Data Steward is accountable for detecting and escalating performance issues in real-time operation

**Authority:** Recommends system review, modification, or restriction if performance concerns identified

---

### 4.6 Clinical Informatics Lead (Model Governance)

**Responsibilities:**
- Plan and execute independent model validation study
- Maintain model registry (version, training data, hyperparameters, performance, explainability assessment)
- Assess and document model explainability and fairness
- Plan and execute model retraining or updates
- Track and manage model drift and performance degradation
- Support model suspension or retirement procedures

**Accountability:** Clinical Informatics Lead is accountable for model governance and performance management

**Authority:** Recommends model updates, retraining, or retirement based on performance evidence

---

### 4.7 Vendor Manager (Third-Party Governance)

**Responsibilities:**
- Execute vendor selection process and contract negotiation
- Obtain and maintain vendor security assessment and certifications
- Negotiate and execute Data Processing Addendum (DPA) and Service Level Agreement (SLA)
- Conduct monthly vendor performance reviews
- Track vendor compliance with contractual obligations (data security, SLA, incident reporting, change procedures)
- Escalate vendor breaches or non-compliance to Information Security and AI Governance Board

**Accountability:** Vendor Manager is accountable for vendor governance and contractual compliance

**Authority:** Recommends vendor suspension, contract termination, or replacement based on compliance findings

---

## 5. Risk Tolerance and Decision Authority

### 5.1 Risk Tolerance Statement

**Clinical Safety Risk Tolerance:**

The Trust accepts the following residual risks in the Patient Deterioration Prediction System:

- **False-Negative Risk (Missed Deterioration):** Maximum acceptable false-negative rate (FNR) is 5% on validation population and 7% in any patient subgroup (age, sex, ethnicity, comorbidity). If FNR exceeds 7% in any subgroup, system is restricted to other subgroups pending investigation and model redesign.

- **False-Positive Risk (Alert Fatigue):** Maximum acceptable false-positive rate (FPR) is 20% on validation population and 25% in any patient subgroup. If FPR exceeds 25%, alert thresholds are adjusted or model is redesigned to balance alert appropriateness and clinical burden.

- **Model Uncertainty:** Risk scores must be calibrated (predicted probability ≈ actual event rate) within ±5 percentage points. Uncalibrated models (e.g., systematic over/under-prediction) must be recalibrated before deployment.

- **Performance Drift:** If model performance metrics degrade below tolerance thresholds for >2 consecutive monitoring periods, system is reviewed for model update, retraining, or retirement.

**Fairness Risk Tolerance:**

The Trust accepts the following fairness requirements:

- **Demographic Parity:** Model performance (sensitivity, specificity) must not differ by >5 percentage points across age groups (<65 vs ≥65), sex, ethnicity (where data available), or comorbidity profile. Material differences require fairness investigation and mitigation (e.g., model redesign, subgroup-specific thresholds).

- **Disparate Impact:** If model alerts disproportionately affect specific demographic groups (e.g., lower sensitivity for women), investigation is required to identify drivers and mitigate bias.

**Incident Risk Tolerance:**

The Trust accepts zero tolerance for:
- Unauthorised access to patient data or system compromise
- Data breaches affecting patient privacy
- System unavailability >15 minutes without detection and escalation
- Clinical incidents (patient harm) attributable to system failure without immediate investigation and remediation

**Financial/Organisational Risk Tolerance:**

The Trust accepts:
- Operational costs of continuous monitoring and clinical audit (estimated 0.5 FTE Clinical Data Steward, quarterly audit cycles)
- Pilot deployment costs and transition to full deployment
- Costs of model retraining or vendor replacement if performance issues identified
- Investment in training, runbooks, and incident response capability

**Decision Authority:** AI Governance Board approves risk tolerance statement and may adjust tolerance on quarterly review with evidence supporting changes (e.g., new safety data, evolving clinical understanding, vendor performance trends).

---

### 5.2 Risk Escalation Framework

| Risk Level | Characteristic | Escalation | Authority |
|---|---|---|---|
| **Low** | Expected operational variation; within tolerance; no action required | None; document in monthly report | Clinical Data Steward |
| **Medium** | Performance metric approaching threshold; pattern emerging; trend monitoring | Escalate to Clinical Safety Lead for review and decision | Clinical Safety Lead |
| **High** | Performance metric exceeds tolerance; safety concern identified; unplanned incident | Escalate to Clinical Governance Committee and AI Governance Board; consider temporary suspension | Clinical Safety Lead + AI Governance Board |
| **Critical** | Patient harm detected; data breach; security compromise; widespread system failure | Immediate escalation to Chief Medical Officer and Executive Leadership; activate Incident Response Plan; consider immediate system suspension | Chief Medical Officer |

---

## 6. Pre-Deployment Approval Gates

The system proceeds through the following approval gates. Each gate requires documented evidence of control effectiveness and approval by named authority before proceeding.

### Gate 1: Use-Case and Requirements Definition (Week 0–2)
**Decision:** Proceed to risk assessment?

**Approval Criteria:**
- [ ] Use case clearly defined and justified (clinical need documented)
- [ ] Intended use and exclusions defined
- [ ] Clinical stakeholders engaged and supportive
- [ ] Budget and resource approved by Finance and Clinical Leadership
- [ ] Regulatory assessment initiated (medical device classification)

**Evidence Required:**
- Approved use-case document (AI-002-patient-deterioration.md)
- Clinical need assessment (clinical literature, outcome data, stakeholder interviews)
- Preliminary budget estimate

**Approval Authority:** Clinical Governance Committee  
**Status:** ✓ Approved (Initial Commit)

---

### Gate 2: Risk Assessment and Governance Policy (Week 2–6)
**Decision:** Approve risk tolerance and governance framework? Proceed to validation planning?

**Approval Criteria:**
- [ ] Risk assessment completed identifying inherent and residual risks
- [ ] Risk tolerance statement approved by AI Governance Board
- [ ] Governance policy approved establishing roles, authority, escalation, and decision gates
- [ ] Clinical Safety Assessment completed with clinical acceptance criteria approved
- [ ] Privacy Impact Assessment (DPIA) completed; lawful basis and consent approach approved
- [ ] Vendor and cloud infrastructure security assessment completed; acceptable or remediation plan approved
- [ ] All critical governance questions from risk assessment addressed or assigned owner
- [ ] Pre-deployment approval gates defined and socialised with stakeholders

**Evidence Required:**
- Approved Risk Assessment (AI-002-patient-deterioration-risk-assessment.md)
- Approved Governance Policy (this document)
- Approved Clinical Safety Assessment
- Approved DPIA
- Vendor security assessment report
- Governance Decision Register

**Approval Authority:** AI Governance Board  
**Target Date:** 2026-11-15

---

### Gate 3: Model Validation and Fairness Assessment (Week 7–16)
**Decision:** Model performance acceptable? Fairness requirements met? Proceed to pilot deployment?

**Approval Criteria:**
- [ ] Independent validation study completed on ≥1000 admissions from this Trust
- [ ] Sensitivity, specificity, PPV, NPV calculated and compared against acceptance criteria (FNR ≤5%, FPR ≤20%)
- [ ] Performance stratified by age, sex, ethnicity, comorbidity; equity requirements met (performance variance ≤5 percentage points)
- [ ] Model explainability assessed; clinicians can understand predictions (user testing or local explainability method documented)
- [ ] Model uncertainty quantification assessed and calibration verified (±5 percentage points)
- [ ] Fairness and bias assessment completed; findings documented
- [ ] Clinical Safety Lead approves model performance and safety readiness
- [ ] Data dependency and EPR data quality assessment completed
- [ ] Monitoring and audit plans finalised

**Evidence Required:**
- Validation study report (performance metrics, fairness analysis, subgroup analysis)
- Model card or equivalent documentation
- Fairness assessment report
- Clinical Safety Lead approval memo

**Approval Authority:** AI Governance Board (on recommendation of Clinical Safety Lead and Clinical Informatics Lead)  
**Target Date:** 2026-01-31

---

### Gate 4: Vendor Contract and Data Protection (Week 12–18)
**Decision:** Vendor contractual terms acceptable? Data processing compliant? Proceed to pilot deployment?

**Approval Criteria:**
- [ ] Data Processing Addendum (DPA) negotiated and signed (restricts vendor access to processing scope only; no secondary use without consent)
- [ ] Service Level Agreement (SLA) in place (≥99.5% availability, RTO/RPO documented, backup/recovery tested)
- [ ] Vendor liability and indemnity provisions reviewed and approved by Legal (no inappropriate caps on liability for patient harm or GDPR breach)
- [ ] Security certifications and audit rights documented
- [ ] Model ownership, export rights, and exit strategy documented
- [ ] Subprocessor list reviewed; approval required before new subprocessors added
- [ ] Privacy Officer approves data processing terms as UK GDPR compliant
- [ ] Information Security approves vendor security posture

**Evidence Required:**
- Signed DPA
- Signed SLA or service contract
- Legal review memo (liability and indemnity)
- Vendor security assessment
- Privacy Officer approval memo

**Approval Authority:** AI Governance Board (on recommendation of Privacy Officer, Information Security, and Vendor Manager)  
**Target Date:** 2026-02-28

---

### Gate 5: Pilot Deployment (Week 19–26)
**Decision:** Pilot performance acceptable? Proceed to full deployment?

**Approval Criteria:**
- [ ] Pilot deployment completed on single ward (10–15 beds) for ≥4 weeks
- [ ] Pilot success criteria met: alert generation rate within expected range, no safety incidents, clinician usability satisfactory, model performance within tolerance
- [ ] Daily pilot monitoring completed; no blockers identified
- [ ] Clinician feedback collected and incorporated; training effective
- [ ] Incident response procedures tested and functional
- [ ] Monitoring and audit systems operational
- [ ] Clinical Safety Lead approves progression to full deployment

**Evidence Required:**
- Pilot deployment report (alert rates, incidents, clinician feedback, model performance)
- Pilot go/no-go decision memo
- Clinician training completion records

**Approval Authority:** Clinical Safety Lead (with AI Governance Board final approval for full deployment)  
**Target Date:** 2026-04-30

---

### Gate 6: Full Deployment and Operational Readiness (Week 27+)
**Decision:** System ready for full deployment across all wards?

**Approval Criteria:**
- [ ] Pilot deployment completed successfully; clinical safety and performance requirements met
- [ ] Operational monitoring systems fully functional (daily/weekly/monthly reporting)
- [ ] Clinical audit programme operational (patient outcome tracking, alert appropriateness review)
- [ ] Incident response team trained and on-call procedures established
- [ ] Clinician training completed for all wards
- [ ] Runbooks and escalation procedures distributed and understood
- [ ] Vendor support and escalation contacts established
- [ ] AI Governance Board approves full deployment

**Evidence Required:**
- Pilot completion report
- Operational readiness checklist
- Training completion records
- Incident response plan and team assignment
- Monitoring baseline established

**Approval Authority:** AI Governance Board  
**Target Date:** 2026-06-30

---

## 7. Monitoring and Performance Governance

### 7.1 Operational Monitoring

**Daily Monitoring (Clinical Data Steward):**
- System availability status (uptime, alert generation count, data pipeline status)
- Unexpected alert volume changes or data quality issues
- Escalate to IT Operations if system unavailable >15 minutes

**Weekly Monitoring (Clinical Data Steward):**
- Alert generation rate and trend (compare vs expected baseline)
- Alert override rate by clinicians (% of alerts acted upon vs ignored)
- Any reported clinical incidents or near-misses related to system

**Monthly Monitoring (Clinical Data Steward + Clinical Safety Lead):**
- Detailed performance report stratified by patient subgroups (age, sex, comorbidity, admission type)
- Sensitivity, specificity, PPV, NPV estimates (prospective, comparing predicted vs actual outcomes)
- Alert fatigue assessment (clinician feedback, override patterns)
- Data quality metrics (completeness, timeliness)
- Incident summary (if any)
- Alert thresholds triggering review:
  - Alert generation rate >30% increase or >20% decrease from baseline
  - Override rate >50% (suggests low clinician confidence in alerts)
  - Adverse outcome rate in alerted patients >5% (suggests false-positive alerts not reducing harm)
  - Any reported patient harm or safety incident

**Quarterly Clinical Audit (Clinical Audit + Quality Improvement):**
- Prospective patient cohort analysis: outcomes (unplanned ICU, cardiac arrest, death, length of stay) in alerted vs non-alerted patients, matched on baseline risk
- Clinical judgement audit: sample of alerts reviewed by clinician to assess appropriateness and evidence of clinical response
- Clinical benefit measurement: track key performance indicators (unplanned ICU admissions, cardiac arrests, mortality) before/after deployment
- Patient safety incident review: any adverse events related to system (missed alert, inappropriate alert, system failure causing delay in care)

**Annual Governance Review (AI Governance Board):**
- Comprehensive review of model performance, clinical outcomes, fairness metrics, incidents, and vendor compliance
- Decision: continue operation, modify model/thresholds, restrict to subgroups, or retire system
- Risk tolerance reassessment and update

---

### 7.2 Alert Thresholds Triggering Investigation

| Metric | Threshold | Action | Owner |
|---|---|---|---|
| System Unavailability | >15 minutes | Escalate to IT Operations; notify Clinical Safety Lead | IT Operations |
| Alert Generation Rate | >30% increase from baseline OR <20% of patient population | Clinical Data Steward reviews; may indicate data quality issue or model drift; escalate to Clinical Informatics | Clinical Data Steward |
| Alert Override Rate | >50% | Clinician survey on alert trust/relevance; consider alert threshold adjustment or model redesign | Clinical Safety Lead |
| Adverse Outcome in Alerted Patients | >5% (i.e., >1 in 20 alerted patients die, suffer cardiac arrest, or unplanned ICU) | Potential indicator of false-positive alerts or clinical non-response; clinical review and escalation | Clinical Safety Lead |
| Model Performance (Any Subgroup FNR) | >7% | Investigation required; potential restriction to other subgroups; model redesign consideration | Clinical Informatics |
| Model Performance (Any Subgroup FPR) | >25% | Alert threshold review; model redesign consideration | Clinical Informatics |
| Patient Harm Incident | Any incident involving patient harm (missed deterioration, inappropriate alert, system failure) | Immediate escalation to Clinical Safety Lead and Chief Medical Officer; incident investigation; system suspension decision | Clinical Safety Lead |
| Data Breach or Security Incident | Any unauthorised access or suspected compromise | Immediate escalation to Information Security and incident response; GDPR breach notification assessment | Information Security |

---

### 7.3 Governance Review Cadence

| Review Cycle | Frequency | Attendees | Scope |
|---|---|---|---|
| **Daily Briefing** | Daily (or as needed) | Clinical Data Steward, IT Operations Lead | System status, availability, alert volume anomalies |
| **Weekly Metrics Review** | Weekly | Clinical Data Steward, Clinical Safety Lead | Performance metrics, alert trends, incidents |
| **Monthly Governance Review** | Monthly | AI Governance Board (abbreviated) | Performance report, incidents, escalations, decisions |
| **Quarterly Board Review** | Quarterly | Full AI Governance Board | Strategic performance assessment, fairness analysis, vendor compliance, risk tolerance reassessment, decision on continuation or modification |
| **Annual Strategic Review** | Annually | AI Governance Board + Executive Leadership | Clinical outcomes, financial performance, organisational impact, decision on continuation, modification, expansion, or retirement |

---

## 8. Incident Management and Escalation

### 8.1 Incident Classification

| Incident Type | Description | Severity | Escalation Route |
|---|---|---|---|
| **System Unavailability** | System offline or unable to generate predictions >15 minutes | Medium | IT Operations → Clinical Data Steward → Clinical Safety Lead |
| **Data Quality Issue** | EPR data missing, delayed, or inaccurate preventing reliable predictions | Medium | Clinical Data Steward → Clinical Informatics → Clinical Safety Lead |
| **Model Performance Degradation** | Performance metrics exceed tolerance (FNR >7%, FPR >25%, or performance variance in subgroups >5%) | High | Clinical Data Steward → Clinical Informatics → Clinical Safety Lead → AI Governance Board |
| **Unexplained Alert Pattern** | Alert generation rate or override pattern significantly abnormal; no obvious cause | Medium | Clinical Data Steward → Clinical Informatics → Clinical Safety Lead |
| **Clinical Incident (Near-Miss)** | Alert generated but clinician did not act; patient subsequently deteriorated (near-miss; no outcome yet) | High | Clinician → Clinical Safety Lead → Incident Response Team |
| **Clinical Incident (Harm)** | Missed alert; patient deteriorated without alert notification; patient harmed (cardiac arrest, unplanned ICU, death) | Critical | Clinician → Clinical Safety Lead → Chief Medical Officer → Incident Response Team (activate 24/7 response) |
| **False-Positive Harm** | Alert generated; clinician acted based on alert; escalation caused unnecessary intervention or harm | High | Clinician → Clinical Safety Lead → Incident Response Team |
| **Data Breach** | Unauthorised access to patient data; suspected data exfiltration or compromise | Critical | IT Security → Information Security Lead → Chief Information Officer → Incident Response Team; GDPR breach notification assessment |
| **Vendor Non-Compliance** | Vendor breaches data-processing terms, SLA, security obligations, or contractual commitments | High | Vendor Manager → Information Security → Privacy Officer → AI Governance Board |
| **Uncontrolled System Change** | Vendor deploys model update, configuration change, or infrastructure change without Trust approval | High | Vendor Manager → Clinical Informatics → AI Governance Board |

---

### 8.2 Incident Response Procedure

**Phase 1: Detection and Reporting (Real-time)**
- System monitoring alerts (automated) or clinician report triggers escalation
- Reporter (clinician, Data Steward, IT Ops) notifies Clinical Safety Lead immediately for critical/high-severity incidents
- Incident logged in incident register with timestamp, description, initial severity assessment

**Phase 2: Immediate Response (<1 hour)**
- Clinical Safety Lead assesses incident severity and scope (single patient affected? system-wide? ongoing?)
- For critical incidents: Chief Medical Officer and IT Security notified; incident response team activated
- For high-severity incidents: Incident investigation team assigned (Clinical Safety Lead, Clinical Informatics Lead, Information Security, IT Ops as appropriate)
- Initial evidence preservation: logs, alert records, system state captured and secured
- Initial containment action (if needed): system paused, alert thresholds adjusted, clinician notification issued

**Phase 3: Investigation (First 48–72 hours)**
- Root-cause analysis: what happened, why, contributing factors (model drift, data quality, user error, system failure, vendor issue)
- Impact assessment: how many patients affected, what harm resulted, what is ongoing risk
- Evidence collection and documentation: logs, audit trails, model outputs, clinical records
- Stakeholder notification (if harm or data breach): Clinical Governance Committee, Privacy Officer (breach notification assessment per UK GDPR)
- Preliminary remedial action: model suspension, alert threshold adjustment, vendor remediation requirement

**Phase 4: Remediation and Recovery**
- Implement remedial actions (model update, system restart, vendor fix)
- Conduct post-remediation testing to confirm issue resolved
- Clinical review of affected patients (if harm occurred) to assess additional clinical oversight needed
- Prepare incident report with findings and recommendations

**Phase 5: Governance Resolution (Ongoing)**
- Incident report submitted to Clinical Safety Lead and AI Governance Board
- Board reviews incident, assesses if systemic issue requires policy/control change
- Decision: resume normal operation, modify procedures, restrict system, or retire system
- Communicate outcome and lessons learned to clinical staff
- Update risk assessment and controls as needed
- Close incident with owner sign-off and review date

**Escalation Contacts (24/7 On-Call):**
- Clinical Safety Lead: [contact details, to be populated]
- IT Operations Lead: [contact details]
- Chief Medical Officer (for critical incidents): [contact details]
- Chief Information Officer (for security incidents): [contact details]

---

## 9. System Suspension and Retirement

### 9.1 Grounds for System Suspension

The system may be suspended (paused pending investigation and remediation) if:

1. **Patient harm incident:** Any unplanned patient outcome (death, cardiac arrest, unplanned ICU admission) directly attributable to system failure (missed alert, false alert, system unavailability)
2. **Model performance degradation:** FNR exceeds 7% or FPR exceeds 25% in any patient subgroup for >2 consecutive monitoring periods
3. **Data breach or security compromise:** Unauthorised access to patient data or suspected data exfiltration
4. **System unavailability:** System offline >4 hours without resolution plan
5. **Vendor non-compliance:** Material breach of data-processing or contractual obligations

**Suspension Authority:** Clinical Safety Lead may suspend system for up to 72 hours pending investigation. Extension beyond 72 hours requires AI Governance Board approval.

**Suspension Notice:** All clinical staff notified immediately of suspension reason and duration. EPR alert system deactivated pending remediation.

---

### 9.2 Grounds for System Retirement

The system may be retired (permanently decommissioned) if:

1. **Unresolvable safety issue:** Patient harm incident or model performance failure cannot be remediated within acceptable risk tolerance
2. **Persistent fairness concern:** Material performance disparities affecting vulnerable patient groups cannot be adequately mitigated
3. **Lack of clinical benefit:** Prospective clinical audit shows no improvement in patient outcomes or unintended harmful consequences (e.g., excessive alert fatigue causing clinician disengagement)
4. **Vendor discontinuation:** Vendor ceases product support, discontinues model updates, or becomes unavailable without acceptable successor
5. **Regulatory or legal requirement:** Medical device classification or regulatory pathway makes continued operation infeasible or non-compliant
6. **Organisational decision:** Clinical leadership and AI Governance Board determine system no longer aligns with organisational strategy or clinical priorities

**Retirement Authority:** AI Governance Board approves system retirement.

**Retirement Procedure:**
- Alert clinical staff of retirement date and reason
- Establish fallback procedures (revert to manual Early Warning Score or alternative system)
- Archive patient data and model artefacts per UK GDPR retention requirements
- Conduct final clinical audit to document system outcomes
- Prepare retirement report documenting system lifecycle, outcomes, lessons learned, and recommendations

---

## 10. Policy Review and Amendment

This policy is reviewed annually or when material changes occur:
- **Material Changes:** Updates to AI Governance Framework, NIST AI RMF, NHS standards, or UK regulations
- **Incident-Driven Changes:** Major incident or clinical outcome prompts policy review and control enhancement
- **Operational Changes:** System expansion, vendor change, or significant model updates

**Review Authority:** AI Governance Board  
**Amendment Approval:** AI Governance Board votes to approve amendments  
**Stakeholder Engagement:** Privacy Officer, Information Security, Clinical Safety Lead, and Vendor Manager consulted before amendments

**Version History:**

| Version | Date | Changes | Approval |
|---|---|---|---|
| 1.0 | 2026-09-11 | Initial governance policy | Pending Board Approval |

---

## 11. Related Documents and References

- NIST AI Risk Management Framework 1.0 (https://nvlti.nist.gov/pages/home)
- UK GDPR and Data Protection Act 2018
- NHS Data Security & Protection Toolkit
- ISO/IEC 42001 AI Management System
- Use Case: AI-002-patient-deterioration.md
- Risk Assessment: AI-002-patient-deterioration-risk-assessment.md
- Clinical Safety Assessment: AI-002-patient-deterioration-clinical-safety-assessment.md
- Data Protection Impact Assessment: AI-002-patient-deterioration-dpia.md

---

**Prepared by:** AI Governance Board  
**Approved by:** [Pending Board signature]  
**Effective Date:** [Upon approval]  
**Next Review:** 2027-09-11

