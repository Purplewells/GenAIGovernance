# Risk Assessment: AI Patient Deterioration Prediction System
## SentinelAI Governance Portfolio

**Document Status:** Draft  
**Date:** 2026-09-11  
**Review Date:** 2026-12-11  
**Prepared by:** AI Governance Portfolio  
**Approval Authority:** AI Governance Board (pending)  
**Risk Assessment ID:** RA-002-PatientDeterioration-001

---

## 1. Purpose and Scope

This risk assessment evaluates the proposed AI-powered patient deterioration prediction system described in use case AI-002. The assessment applies the NIST AI Risk Management Framework 1.0 (GOVERN, MAP, MEASURE, MANAGE) to identify, characterise, and propose control measures for material risks across the system lifecycle.

**Scope:**
- AI model, data pipelines, clinical alerting, and vendor/cloud infrastructure
- Pre-deployment governance gates through operational monitoring
- Legal, privacy, security, safety, clinical, fairness, and organisational risks

**Exclusions:**
- Existing Electronic Patient Record (EPR) system governance (assumed in scope separately)
- Patient consent mechanisms (assumed handled by Privacy Impact Assessment)
- Clinical training and change-management programmes (assumed separate workstream)

**Jurisdiction:** UK (Data Protection Act 2018, UK GDPR, NHS governance)  
**Audience:** AI Governance Board, Clinical Safety Lead, Privacy Officer, Information Security, Finance

---

## 2. Use Case Summary

**Problem:** Clinical deterioration occurs rapidly and unpredictably. Current Early Warning Score (EWS) systems rely on periodic observations; deterioration between observation points may be missed. The Trust receives ~50,000 admissions annually; unplanned critical events create clinical and financial impact.

**Proposed Solution:** A supervised machine-learning system that ingests continuous clinical observations, vital signs, laboratory results, and events from the EPR, predicts deterioration risk within 24–72 hours, and alerts clinicians when risk exceeds configurable thresholds.

**Intended Users:** Clinical staff (nurses, doctors, ward managers)  
**Intended Benefit:** Improve early detection, enable earlier intervention, reduce unplanned ICU admissions, reduce cardiac arrests and mortality.

---

## 3. NIST AI RMF Mapping and Risk Register

### GOVERN Function: Accountability, Policy, and Decision Authority

| Risk ID | Risk Description | Inherent Risk | Control Measure | Residual Risk | Owner | Status |
|---------|------------------|---|---|---|---|---|
| **GOVERN-001** | No clear accountability for AI system performance, accuracy failures, or patient harm resulting from missed or false-positive alerts | High | **Evidence:** Establish written AI Governance Policy naming accountability for pre-deployment testing, operational monitoring, incident response, and system retirement. Assign Clinical Safety Lead as system owner with clear escalation authority. Create AI Incident Response Plan with defined roles (data steward, clinical safety, security, privacy, quality) and notification triggers for alert failures or adverse clinical events. | Medium | AI Governance Board Lead | Draft |
| **GOVERN-002** | Lack of risk tolerance definition; no approved decision framework for accepting residual risks to patient safety, clinical workflow disruption, or regulatory exposure | High | **Evidence:** AI Governance Board to document risk tolerance statement and approval authority. Define maximum acceptable false-negative rate (missed deterioration causing patient harm), false-positive rate (alert fatigue, unnecessary escalation), and model uncertainty thresholds. Document in GOVERN decision register with review cadence (quarterly). | Medium | Clinical Governance Committee | Draft |
| **GOVERN-003** | Insufficient pre-deployment governance gates; no documented approval authority or approval criteria for deployment to production | High | **Evidence:** Define pre-deployment approval gates: (1) Model performance validation complete with independent review; (2) Privacy Impact Assessment approved; (3) Clinical Safety Assessment complete; (4) Vendor/cloud infrastructure approved by Information Security; (5) Clinical training and runbook complete; (6) Monitoring and incident escalation procedures operational. Gate decision to pass/fail/conditional approval; require Clinical Safety Lead and AI Governance Board sign-off. | Medium | AI Governance Board Lead | Draft |
| **GOVERN-004** | Vendor or cloud provider changes to model, data processing, or infrastructure without approval; no change management discipline | Medium | **Evidence:** Require Data Processing Addendum (DPA) and Service Change Procedure in vendor contract. Specify that model updates, retraining, configuration changes, or infrastructure changes require 30 days' notice and Trust approval before deployment. Define Change Impact Assessment template for vendor-initiated changes. Establish monthly vendor review cadence to identify undisclosed changes. | Low | Information Security / Vendor Manager | Recommendation |

### MAP Function: Purpose, Data, Stakeholders, Context, and Dependencies

| Risk ID | Risk Description | Inherent Risk | Control Measure | Residual Risk | Owner | Status |
|---------|------------------|---|---|---|---|---|
| **MAP-001** | Unclear or drifting intended use; model used for purposes beyond its design (e.g., resource rationing, discharge planning, staffing decisions) | Medium | **Evidence:** Document intended use: "Identify hospitalised patients at risk of clinical deterioration within 24–72 hours to enable earlier clinical assessment and intervention." Define exclusions (e.g., not for resource allocation, not for discharge planning, not for performance evaluation of staff). Require clinical governance approval of any proposed secondary use. Train all users on intended use and escalate any observed out-of-scope use to Clinical Safety Lead. | Low | Clinical Safety Lead | Recommendation |
| **MAP-002** | Data dependencies unclear; system reliant on continuous EPR data feed; no documented data quality requirements or failure modes | High | **Evidence:** Data dependency map: identify all EPR feeds (vitals, observations, labs, events), latency requirements, availability targets (99.5% for continuous monitoring), failure-mode effects (e.g., missing vital sign → risk score indeterminate; partial observations → prediction uncertainty). Define data quality thresholds (completeness, timeliness, accuracy) and alert mechanisms if data quality drops below threshold. Implement daily data audit report to Clinical Data Steward. **Unknown:** Current EPR data availability and quality; requires EPR system assessment. | Medium | Clinical Data Steward / IT Operations | Recommendation |
| **MAP-003** | No documented patient population definition; model developed on different population than actual deployment population | High | **Evidence:** Specify populations included in model training (age ranges, comorbidity profiles, admission types, hospital setting, geographic region, time period). Compare training population demographics with this Trust's patient demographics. If material differences exist (e.g., training on adult ICU patients only, deployed on medical wards with different case mix), require population-specific validation study before deployment. **Assumption:** Model details (training data, population) will be available from vendor or model documentation; if vendor-provided model, request training population metadata. | Medium | Clinical Informatics / Vendor | Recommendation |
| **MAP-004** | Stakeholder and patient information, consent, and communication mechanisms not defined | Medium | **Evidence:** Identify all stakeholders: patients, clinicians (nurses, doctors, ward managers), clinical leadership, IT, privacy/governance, vendors. Develop stakeholder engagement plan: inform patients via privacy notice and hospital comms; provide clinicians with training on model outputs, limitations, and alert interpretation; engage clinical champions to support adoption. Document patient notification approach (privacy notice, consent requirements per GDPR lawful basis). **Unknown:** Chosen lawful basis for processing (task in public interest, healthcare management, legitimate interests); requires DPIA. | Medium | Communications / Privacy Officer | Recommendation |
| **MAP-005** | Model dependencies not documented; unclear what versions, hyperparameters, or training data versions are in production | Medium | **Evidence:** Establish model registry recording model ID, version, training data version, hyperparameters, performance metrics, deployment date, and owner. For vendor-supplied models, require vendor to provide model card (or equivalent) documenting model inputs, outputs, intended use, training data characteristics, performance by population, known limitations, and fair-use policy. Update registry on any model update. | Low | Clinical Informatics / Model Governance | Recommendation |

### MEASURE Function: Performance, Fairness, Uncertainty, and Real-World Monitoring

| Risk ID | Risk Description | Inherent Risk | Control Measure | Residual Risk | Owner | Status |
|---------|------------------|---|---|---|---|---|
| **MEASURE-001** | Model accuracy and sensitivity not validated in this Trust's patient population before deployment; transferred model may have worse performance | High | **Evidence:** Before deployment, conduct independent validation study: (1) retrospective analysis on ≥1000 recent admissions from this Trust, comparing model predictions with actual deterioration outcomes; (2) calculate sensitivity (true-positive rate), specificity (true-negative rate), positive predictive value (PPV), and negative predictive value (NPV) by key patient subgroups (age ≥65 vs <65, presence/absence of comorbidities, admission type); (3) compare against acceptance criteria approved by Clinical Safety Lead (e.g., sensitivity ≥90%, specificity ≥80%); (4) document and approve or remediate before production deployment. **Unknown:** Validation acceptance criteria; requires clinical governance decision. | Medium | Clinical Informatics / Clinical Safety Lead | Recommendation |
| **MEASURE-002** | False-negative rate (missed deterioration) not characterised; no documented clinical impact threshold | High | **Evidence:** In validation study, calculate false-negative rate and project clinical impact (e.g., if FNR = 5% and 50,000 admissions annually, ~2,500 at-risk patients missed). Conduct clinical review of false-negative cases to understand missed deterioration patterns (e.g., atypical presentations, rare comorbidities, rapid deterioration outside prediction window). Define maximum tolerable FNR with Clinical Safety Lead and document rationale. If FNR exceeds tolerance, redesign model or alert thresholds. **Unknown:** Acceptance criteria for FNR and clinical impact; requires clinical risk tolerance decision. | High | Clinical Safety Lead | Recommendation |
| **MEASURE-003** | False-positive rate (unnecessary alerts) not characterised; no documented effect on clinician alert fatigue and workload | High | **Evidence:** In validation study, calculate false-positive rate. Conduct workflow impact assessment: project alert volume (e.g., if FPR = 20% and 50 daily patients, ~10 false alerts daily), survey clinicians on burden and alert fatigue from comparable systems, define acceptable alert rate that minimises fatigue without missing true deterioration. Run pilot study (see MANAGE-006) to observe real-world alert fatigue and clinician response rates. Establish alert thresholds to balance FPR and FNR. **Unknown:** Maximum tolerable FPR and clinician alert fatigue threshold; requires clinical and human-factors decision. | High | Clinical Safety Lead / Human Factors | Recommendation |
| **MEASURE-004** | Model performance not monitored in real-world operation; drift in patient population, data quality, or model accuracy not detected | High | **Evidence:** Establish operational performance monitoring: (1) monthly comparison of predicted risk scores with actual outcomes (prospective monitoring of model calibration and discrimination); (2) track alert generation rate, alert override rate by clinicians, and adverse outcome rate among alerted vs non-alerted patients; (3) stratify by patient subgroups (age, comorbidity, admission type) to detect performance degradation in specific populations; (4) define alert thresholds triggering review (e.g., if override rate >50%, if adverse outcome rate among alerted patients >5%, if any subgroup FNR >10%); (5) assign Clinical Data Steward to review monitoring reports monthly and escalate findings to Clinical Safety Lead; (6) establish governance procedure for model suspension if performance drops below tolerance. | Medium | Clinical Data Steward / Clinical Informatics | Recommendation |
| **MEASURE-005** | Prediction uncertainty not quantified or communicated to clinicians; clinicians may over-rely on point predictions | Medium | **Evidence:** If model produces calibrated probability scores (not just binary classifications), document prediction confidence and communicate uncertainty to clinicians (e.g., "60% risk ± 15% confidence interval"). If model outputs binary alerts with no uncertainty quantification, require model redesign to provide confidence or probability, or restrict alerts to high-confidence predictions only. Include uncertainty communication in clinician training. | Low | Clinical Informatics / Model Development | Recommendation |
| **MEASURE-006** | Fairness and equity not assessed; model may perform poorly on specific demographic groups, leading to undertreatment of vulnerable patients | High | **Evidence:** In validation study, calculate sensitivity, specificity, PPV, NPV stratified by age, sex, ethnicity, comorbidity profile, and socioeconomic factors (if available). Compare performance across groups; if material performance differences identified (e.g., sensitivity 85% in women vs 95% in men), investigate drivers (e.g., different presentation patterns, historical bias in training data, feature engineering that encodes demographics). Define acceptable performance variance across groups and remediate models that fail equity criteria before deployment. Document equity assessment findings and governance approval. **Unknown:** Acceptance criteria for performance variance across groups; requires fairness and equality impact assessment. | Medium | Clinical Informatics / Equality & Diversity Lead | Recommendation |
| **MEASURE-007** | Prediction explainability insufficient; clinicians cannot understand why a risk alert was generated; clinicians cannot assess validity or override alerts with confidence | Medium | **Evidence:** Require model interpretability: either use inherently interpretable model (logistic regression, decision tree) with clear feature weights, or use black-box model with local explainability technique (LIME, SHAP) that identifies key features and their contribution to individual predictions. Test explainability with sample of clinicians: do they understand why an alert was generated? Can they identify if alert is clinically plausible? Integrate explanations into alert interface. | Low | Clinical Informatics / Human Factors | Recommendation |

### MANAGE Function: Monitoring, Incident Response, and Change Control

| Risk ID | Risk Description | Inherent Risk | Control Measure | Residual Risk | Owner | Status |
|---------|------------------|---|---|---|---|---|
| **MANAGE-001** | No incident detection or escalation procedure for AI system failures; adverse events not linked to AI system performance | High | **Evidence:** Define AI incident detection: (1) system unavailability >15 minutes; (2) data pipeline failure preventing model prediction; (3) unexpected increase in alert volume or override rate; (4) clinical incident report mentioning "alert missed deterioration" or "alert led to unnecessary escalation"; (5) model performance metric exceeding alert threshold. Establish escalation: Tier 1 (system alert) → IT Operations; Tier 2 (performance concern) → Clinical Data Steward & Clinical Safety Lead; Tier 3 (clinical harm) → Clinical Governance Committee & Incident Lead. Establish 24/7 on-call escalation contact for critical incidents. Document in AI Incident Response Plan. | Low | IT Operations / Clinical Safety Lead | Recommendation |
| **MANAGE-002** | No procedure for restricting, pausing, or retiring the system if performance degrades or harm is detected | High | **Evidence:** Establish suspension/retirement criteria: (1) if FNR exceeds tolerance for >2 consecutive monitoring periods, recommend clinical review and potential model redesign or restriction to lower-risk patient cohorts; (2) if unplanned incident causes >1 patient harm, trigger root-cause investigation and system pause pending remediation; (3) if clinical governance review finds unacceptable patient outcomes, recommend system retirement. Authorise Clinical Safety Lead or Clinical Governance Committee to suspend system pending investigation; escalate retirement decision to AI Governance Board. Document decisions and rationale in governance register. | Low | Clinical Safety Lead / AI Governance Board | Recommendation |
| **MANAGE-003** | No clinical audit or outcome monitoring; system performance and clinical benefit not validated in real-world operation | High | **Evidence:** Establish prospective clinical audit programme: (1) enrol cohort of patients alerts are generated for; (2) track clinical outcomes (unplanned ICU, cardiac arrest, death, length of stay, escalations avoided, interventions undertaken); (3) compare clinical outcomes and resource use between alerted and non-alerted cohorts, matched on baseline risk factors; (4) conduct quarterly audit reports to Clinical Governance Committee with analysis of alert appropriateness, clinician response rate, clinical benefit, and harms. Define success measures: (a) if clinical benefit observed (reduced unplanned ICU or mortality), support continuation; (b) if no benefit but acceptable safety, continue with enhanced monitoring; (c) if harm detected, trigger investigation and potential system restriction/retirement. | Medium | Clinical Audit / Quality Improvement | Recommendation |
| **MANAGE-004** | No defined procedure for handling conflicting evidence; if independent audit finds model performance inconsistent with vendor claims, no governance mechanism to resolve and act | Medium | **Evidence:** Establish evidence reconciliation procedure: when independent testing (validation study, operational monitoring, clinical audit) conflicts with vendor claims or pre-deployment testing, trigger evidence review by Clinical Safety Lead and Governance Sponsor. Determine authoritative source (e.g., independent testing more credible than vendor claims), communicate findings to stakeholders, and implement remedial action (model update, alert threshold adjustment, system restriction, or retirement). Document resolution in governance register. | Low | Clinical Safety Lead / Governance Sponsor | Recommendation |
| **MANAGE-005** | No defined procedures for model retraining or update; model may become outdated as patient population or clinical practice changes | Medium | **Evidence:** Establish model governance procedure: (1) annual clinical and statistical review of model performance trends; (2) if performance drops below tolerance or patient population materially changes (e.g., new admission pathways, new comorbidity profiles), conduct reassessment and decide whether retraining is justified; (3) if model is retrained, repeat validation study before deployment of updated model; (4) document retraining decision, rationale, validation results, and governance approval. Require vendor agreement to support retraining or model refresh at defined intervals and costs. | Low | Clinical Informatics / Vendor Manager | Recommendation |
| **MANAGE-006** | Pilot deployment or controlled rollout not planned; full deployment to all wards and clinicians creates uncontrolled risk if early issues arise | Medium | **Evidence:** Propose phased deployment: (1) **Pilot Phase (Weeks 1–8):** Deploy to single ward (10–15 beds) with detailed data collection, daily clinician feedback, daily system monitoring, and rapid adjustment authority; (2) **Controlled Rollout Phase (Weeks 9–16):** Expand to 2–3 additional wards, continued enhanced monitoring, weekly performance reviews, decision gate at week 12 to pause or proceed; (3) **Full Deployment (Week 17+):** Roll out to all wards contingent on pilot success. Establish pilot success criteria: alert generation within expected range, clinician usability satisfactory, no unexplained clinical incidents, model performance within tolerance. Assign dedicated Pilot Lead to manage deployment and escalate issues in real time. | Low | Clinical Informatics / Pilot Lead | Recommendation |

### Third-Party Risk (Vendor and Cloud Infrastructure)

| Risk ID | Risk Description | Inherent Risk | Control Measure | Residual Risk | Owner | Status |
|---------|------------------|---|---|---|---|---|
| **VENDOR-001** | Vendor model or cloud infrastructure provider may access patient data for purposes beyond the contract (model improvement, analytics, support); patient data privacy not protected | High | **Evidence:** Data Processing Addendum (DPA) must explicitly restrict vendor and infrastructure provider access to patient data: (1) vendor and subprocessors may process data only for stated purpose (risk prediction in this Trust's environment); (2) vendor shall not use patient data to improve its commercial model or train future models for other customers without explicit written consent; (3) vendor shall not allow routine access by support staff or analytics teams without Trust approval; (4) vendor must publish list of subprocessors and obtain Trust approval before adding new subprocessors; (5) vendor must notify Trust immediately of any suspected unauthorised access. Contract must include audit rights allowing Trust to verify compliance with data restrictions. **Unknown:** Vendor and infrastructure provider data policies; requires vendor assessment. | Medium | Privacy Officer / Vendor Manager | Recommendation |
| **VENDOR-002** | Vendor bankruptcy, product discontinuation, or exit from market; no exit plan; patient data and model remain locked with vendor | High | **Evidence:** Contract must include exit strategy: (1) vendor must support data export in standard formats (CSV, HL7 FHIR, or equivalent) within 30 days of contract termination; (2) vendor must provide model export (model weights, architecture, training data summary) or acknowledge model return to Trust; (3) vendor must document all processing procedures and audit trails to enable transition to alternative supplier; (4) Trust must have rights to archived patient data and audit records for compliance, legal, and clinical purposes. Establish 18-month evaluation of alternative suppliers to enable rapid migration if needed. | Medium | Vendor Manager / IT Strategy | Recommendation |
| **VENDOR-003** | Vendor infrastructure (cloud provider) availability and resilience not documented; system failure impacts patient safety | Medium | **Evidence:** Require vendor to document: (1) cloud infrastructure provider SLA (availability target ≥99.5% monthly); (2) data centre geographic redundancy (data replicated across multiple regions to survive single data-centre failure); (3) disaster-recovery procedure and recovery time objective (RTO) and recovery point objective (RPO) — e.g., RTO ≤1 hour, RPO ≤1 hour; (4) backup and restore testing cadence (quarterly minimum). Conduct independent audit of vendor claims. Define system unavailability alert threshold (≥15 minutes) and escalation procedure to Vendor Manager and Clinical Safety Lead. Document in vendor SLA agreement. | Low | Information Security / Vendor Manager | Recommendation |
| **VENDOR-004** | Vendor contract terms include liability caps or disclaimers that inappropriately limit accountability for patient harm; vendor not accountable for model failures | High | **Evidence:** Contract must include: (1) vendor accountability for model accuracy and performance claims; liability provisions must not exclude or cap liability for death or personal injury caused by vendor negligence or breach of data-processing obligations; (2) indemnity for IP infringement (model does not infringe third-party patents or copyrights); (3) indemnity for breaches of UK GDPR or UK Data Protection Act 2018; (4) vendor insurance covering professional indemnity, cyber liability, and errors & omissions at adequate levels (minimum £1M recommended); (5) termination right for material breach with 60-day cure period. Require legal review of vendor contract to ensure terms are acceptable to NHS risk tolerance. **Unknown:** Vendor contract terms; requires legal review. | High | Legal / Procurement | Recommendation |

---

## 4. NIST AI RMF Core Characteristic Risks

Beyond functional risks, assess performance on NIST AI RMF core characteristics:

| Characteristic | Assessment | Evidence / Gap | Control Recommendation | Owner |
|---|---|---|---|---|
| **Accuracy & Reliability** | **Risk:** Accuracy not validated; may not meet clinical requirements | Validation study (MEASURE-001) not yet conducted; model performance on this Trust's population unknown | Conduct independent validation before deployment; monitor performance in operation (MEASURE-004) | Clinical Informatics |
| **Fairness & Equity** | **Risk:** Model may discriminate against age, sex, ethnicity, or comorbidity groups | Fairness assessment (MEASURE-006) not yet conducted; if model trained on biased historical data, may perpetuate bias | Stratify validation by demographic and clinical subgroups; establish acceptable performance variance; define fairness governance policy | Clinical Informatics / Equality Lead |
| **Explainability & Interpretability** | **Risk:** Clinicians cannot understand predictions; may not trust or may over-trust alerts | Model design unknown; if black-box model without explainability, clinicians have no basis to override or question alerts | Require interpretable model or local explainability technique (LIME, SHAP); integrate explanations in alert interface (MEASURE-007) | Clinical Informatics |
| **Resilience & Robustness** | **Risk:** System fails or makes incorrect predictions when encountering out-of-distribution data or system faults | Unknown whether model performance degrades gracefully or fails catastrophically on unfamiliar patient presentations | Conduct adversarial testing and stress testing before deployment; establish monitoring to detect performance degradation (MANAGE-004); define fallback procedures if system unavailable | Clinical Informatics / IT Ops |
| **Transparency & Accountability** | **Risk:** Governance and decision-making opaque; no clear accountability for failures or patient harm | No documented accountability structure, incident response procedure, or suspension criteria yet established | Establish governance roles, decision authority, incident escalation, and system suspension/retirement criteria (GOVERN-001, MANAGE-002) | AI Governance Board |
| **Cybersecurity & Privacy** | **Risk:** Patient data not protected from unauthorised access; vendor/cloud provider may misuse data; system vulnerable to attack | Data security and privacy controls depend on vendor and cloud infrastructure; DPA and security assessment not yet conducted | Data Processing Addendum (VENDOR-001); security assessment of vendor and infrastructure (VENDOR-003); audit rights and monitoring (VENDOR-001) | Privacy Officer / Information Security |

---

## 5. Legal and Regulatory Baseline

**Regulatory Framework:**
- UK GDPR (legal basis for data processing, lawful processing conditions, patient rights)
- Data Protection Act 2018, section 10 (processing for healthcare purposes)
- NHS Data Security & Protection Toolkit (information governance minimum standard)
- Care Quality Commission (CQC) Health and Social Care Act 2008 (Regulated Activities) Regulations 2014 (safe and effective care)
- Medical Devices Regulation 2002/768 (if model qualifies as medical device; currently **Unknown** — requires legal assessment)

**Privacy Baseline:**
- Lawful basis for processing must be established and documented in Data Protection Impact Assessment (DPIA)
- Patient information and rights must be communicated (privacy notice)
- Data subject rights (access, deletion, portability, objection) must be respected
- Data retention periods must be limited and justified
- Patient data must not be used for secondary purposes (e.g., model improvement for other customers) without explicit consent or separate lawful basis

**Safety and Clinical Governance Baseline:**
- Trust has duty of care to patients; clinicians remain accountable for treatment decisions
- Trust has duty to provide safe, effective, and person-centred care
- Adverse events and near-misses must be reported to Patient Safety Incident Response Framework (PSIRF)
- Clinical governance committee has authority to restrict or pause unsafe systems

**Status:** Regulatory assessment incomplete; requires legal, safety, and privacy specialist review.

---

## 6. Key Unknowns and Dependencies

| Item | Impact | Mitigation | Owner | Target Date |
|---|---|---|---|---|
| Model details (training data, population, performance, explainability) | **High:** Cannot assess accuracy, fairness, or interpretability without model metadata | Request model documentation from vendor or model developer; conduct independent performance validation study | Clinical Informatics | Before validation study starts |
| Lawful basis for continuous data processing | **High:** Cannot proceed with system without lawful basis; affects patient information and consent requirements | Conduct Data Protection Impact Assessment (DPIA) to determine appropriate lawful basis (e.g., healthcare management task, patient consent, legitimate interest) | Privacy Officer | Before deployment gate |
| Clinical acceptance criteria (max FNR, max FPR, alert fatigue tolerance) | **High:** Cannot determine if model performance is acceptable without clinical consensus on requirements | Convene clinical stakeholder workshop (Clinical Safety Lead, nursing leadership, doctors, medical informatics) to define and document acceptance criteria | Clinical Safety Lead | Before validation study |
| Vendor/cloud infrastructure data policy and security posture | **High:** Cannot assess data privacy and security risks without vendor assessment | Conduct vendor security assessment; request Data Processing Addendum and SLA; negotiate contractual data restrictions and audit rights | Information Security / Vendor Manager | Before deployment gate |
| Medical device classification and regulatory pathway | **Medium:** Unclear if system qualifies as medical device; affects regulatory approval pathway | Obtain legal or regulatory specialist assessment of whether model qualifies as Class I, II, or III medical device under MDR 2002/768; if so, follow regulatory approval pathway | Legal / Regulatory | Before deployment gate |
| Patient population demographics and comorbidity distribution | **Medium:** Cannot assess fairness or generalisability without understanding this Trust's patient population | Conduct demographic and clinical profiling of this Trust's patient population; compare with model training population; identify material differences that require population-specific validation | Clinical Informatics | Before validation study |
| Current EPR data quality, availability, and integration capability | **Medium:** Cannot plan data pipeline or assess data dependencies without understanding EPR capabilities | Audit current EPR data quality (completeness, timeliness, accuracy); assess data extraction and integration capabilities; document data quality requirements and failure modes | Clinical Data Steward / IT Operations | Before system design phase |

---

## 7. Risk Prioritisation and Governance Decision

### Highest Priority Risks (Residual Risk: High or Material)

**For GOVERN Approval Authority to address before deployment:**

1. **MEASURE-002 (False-negative rate not characterised):** Missed deterioration causing patient harm is the primary clinical risk. Must conduct validation study and establish FNR tolerance with Clinical Safety Lead before deployment.

2. **MEASURE-003 (False-positive rate and alert fatigue):** Unnecessary alerts may reduce clinician trust and increase workload. Must understand alert impact and establish FPR tolerance before deployment.

3. **MEASURE-006 (Fairness assessment):** If model performs worse on specific demographic groups, may lead to under-treatment of vulnerable patients. Must conduct fairness assessment and establish equity governance before deployment.

4. **GOVERN-001 & GOVERN-003 (Accountability and approval gates):** No clear accountability structure or approval authority yet established. Must assign owners, define governance procedures, and establish pre-deployment approval gates before system goes live.

5. **VENDOR-001 & VENDOR-004 (Vendor data access and liability):** Patient data privacy and vendor accountability are legal and clinical imperatives. Must negotiate Data Processing Addendum and liability terms before deployment.

---

## 8. Governance Approval Decision

**Decision Requested:**

Can the AI Patient Deterioration Prediction System proceed to the next governance gate (detailed system design and validation planning)?

**Approval Conditions (Pre-Design Gate):**

- [ ] AI Governance Board approves risk assessment and identifies missing controls
- [ ] Clinical Safety Lead confirms clinical acceptance criteria for model performance (FNR, FPR, alert volume)
- [ ] Privacy Officer confirms lawful basis for data processing in DPIA and data-processing terms
- [ ] Information Security confirms vendor/cloud infrastructure acceptable or requirements for vendor remediation
- [ ] Finance approves budget for validation study, pilot deployment, and operational monitoring

**Approval Authority:** AI Governance Board  
**Recommended Review Cadence:** Quarterly risk re-assessment as system progresses through lifecycle stages  
**Escalation Route:** Material changes to risk profile or residual risk exceeding tolerance → Clinical Governance Committee → Chief Medical Officer

---

## 9. Recommendations Summary

| Priority | Recommendation | Owner | Due Date |
|---|---|---|---|
| **1 (Critical)** | Establish GOVERN policy: define accountability roles, risk tolerance, approval authority, incident escalation, and suspension criteria | AI Governance Board Lead | 2026-10-31 |
| **2 (Critical)** | Conduct Data Protection Impact Assessment (DPIA); determine lawful basis for continuous data processing and document patient information/consent approach | Privacy Officer | 2026-10-31 |
| **3 (Critical)** | Define clinical acceptance criteria: maximum tolerable FNR, FPR, alert volume, and performance variance across patient subgroups | Clinical Safety Lead | 2026-10-31 |
| **4 (Critical)** | Conduct vendor security and data-policy assessment; negotiate Data Processing Addendum and liability terms | Information Security / Vendor Manager | 2026-10-31 |
| **5 (High)** | Plan and budget independent model validation study (retrospective analysis on ≥1000 admissions; stratified performance assessment; fairness analysis) | Clinical Informatics | 2026-10-31 |
| **6 (High)** | Establish pre-deployment approval gates and governance procedures; document in AI Governance Policy | AI Governance Board Lead | 2026-11-30 |
| **7 (High)** | Audit current EPR data quality, availability, and integration capability; document data dependencies and failure modes | Clinical Data Steward | 2026-11-30 |
| **8 (High)** | Assess medical device classification and confirm regulatory approval pathway (if applicable) | Legal / Regulatory | 2026-11-30 |
| **9 (Medium)** | Design phased pilot deployment; establish pilot success criteria and rapid decision authority | Clinical Informatics / Pilot Lead | 2026-12-31 |
| **10 (Medium)** | Establish operational monitoring programme: performance tracking, incident detection, clinical audit, and governance review cadence | Clinical Data Steward / Quality Improvement | 2027-01-31 |

---

## 10. Document Control

| Version | Date | Author | Status | Notes |
|---|---|---|---|---|
| 1.0 | 2026-09-11 | AI Governance Portfolio | Draft | Initial risk assessment based on use case AI-002 |

**Next Review:** 2026-12-11 or when major changes to system design, vendor selection, or clinical plan occur.

---

## Appendix A: Cross-Reference to Use Case Governance Questions

This risk assessment addresses the Governance Questions listed in AI-002 use case:

| Use Case Governance Question | Addressed in Risk Assessment | Risk ID(s) |
|---|---|---|
| Model Development & Validation | MEASURE-001, MEASURE-002, MEASURE-003, MEASURE-006 | RA-002-001 through 007 |
| Clinical Safety & Accuracy | MEASURE-001, MEASURE-002, MEASURE-003, MEASURE-005, MEASURE-007 | RA-002-001 through 007 |
| Bias & Fairness | MEASURE-006 | RA-002-006 |
| Human Oversight & Accountability | GOVERN-001, MANAGE-001, MANAGE-002 | RA-002-001, 004, 005 |
| Data Processing & Privacy | MAP-002, VENDOR-001, Legal/Regulatory Baseline | RA-002-002, VENDOR-001 |
| System Availability & Resilience | VENDOR-003 | RA-002-008 |
| Monitoring & Incident Management | MANAGE-001, MANAGE-003, MANAGE-004 | RA-002-009, 010, 011 |
| Vendor Management | VENDOR-001, VENDOR-002, VENDOR-003, VENDOR-004 | RA-002-007, 008, 009, 010 |

---

**Document Prepared by:** AI Governance Portfolio  
**For:** SentinelAI Governance Portfolio Demonstration  
**Status:** Ready for AI Governance Board Review  
**Next Action:** Board approval of risk assessment and governance decision on proceeding to design gate.

