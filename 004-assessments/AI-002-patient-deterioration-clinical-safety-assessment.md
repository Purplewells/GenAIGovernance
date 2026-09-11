# Clinical Safety Assessment: Patient Deterioration Prediction System
## SentinelAI Governance Portfolio

**Document Status:** Draft  
**Date:** 2026-09-11  
**Review Date:** 2026-12-11  
**Prepared by:** Clinical Safety Lead (with Clinical Informatics, Medical Informatics)  
**Approval Authority:** Clinical Safety Lead, Clinical Governance Committee  
**Assessment ID:** CSA-002-PatientDeterioration-001

---

## 1. Executive Summary

This Clinical Safety Assessment evaluates whether the proposed AI-powered Patient Deterioration Prediction System meets clinical safety requirements for deployment in a UK NHS Trust. The assessment establishes clinical performance acceptance criteria, identifies potential harms and mitigation strategies, and documents clinical governance authority and accountability.

**Key Findings:**
- Clinical need is well-established (50,000 annual admissions; unplanned critical events represent significant clinical and financial impact)
- Proposed system technology is sound and used successfully in comparable healthcare settings
- **Critical dependency:** Independent model validation on this Trust's patient population must demonstrate sensitivity (true-positive rate) ≥90% and specificity ≥80% before deployment
- Clinical governance procedures (alert escalation, clinician training, incident reporting) must be established before system goes live
- Ongoing clinical audit is essential to validate clinical benefit in real-world operation

**Safety Verdict:** System is acceptable for pilot deployment conditional on Gates 2–4 approval (risk assessment, model validation, vendor governance).

---

## 2. Clinical Context and Problem Statement

### 2.1 Clinical Problem

**Epidemiology:**
- NHS Trust receives approximately 50,000 patient admissions annually
- Unplanned critical events (unexpected deterioration requiring emergency intervention) occur in 3–5% of admissions
- Current Early Warning Score (EWS) systems rely on periodic vital sign observations (typically 4–12 hourly for general ward patients)
- Deterioration between observation points may be missed
- Estimated 1,500–2,500 patients annually at risk of undetected deterioration

**Clinical Impact of Current Process:**
- Delayed recognition of deterioration increases risk of:
  - Cardiac arrest (mortality 70–80% even with CPR)
  - Unplanned ICU admission (length of stay ↑, mortality ↑)
  - Mortality in hospital (overall in-hospital mortality 3–5% nationally; higher in deteriorating patients)
- Cognitive burden of continuous manual monitoring diverts clinical attention from other priorities
- Staff workload during acute deterioration crises reduces care quality and increases medical errors

**Evidence:**
- National Confidential Enquiry into Patient Outcome and Death (NCEPOD) reports show 50–60% of in-hospital cardiac arrests have recognised warning signs in preceding hours
- Studies of Rapid Response Teams (RRTs) / Medical Emergency Teams (METs) show mortality reduction of 10–20% with early detection and intervention
- Early Warning Scoring systems reduce mortality by 0.5–2% when used effectively (National Institute for Health and Care Excellence [NICE] QS106)

**Clinical Opportunity:**
- AI-powered continuous monitoring could close gap between observation points
- Earlier risk assessment could enable earlier clinical review, investigations, and escalation
- Targeted alerts to high-risk patients could improve efficiency of clinical response
- Estimated clinical benefit: 5–15% reduction in unplanned ICU admissions and 2–5% reduction in in-hospital mortality if system performs as intended (evidence base: comparable systems in literature; this Trust-specific benefit must be validated in operational audit)

---

### 2.2 Proposed Solution

**Technology:**
- Supervised machine-learning model (algorithm type not yet specified; may be logistic regression, random forest, neural network, or commercial black-box model)
- Ingests continuous EPR data: vital signs (temperature, heart rate, blood pressure, respiratory rate, oxygen saturation), observations (consciousness, urine output), laboratory results, clinical events
- Generates risk score (0–100% probability) and alerts clinicians when predicted risk exceeds configurable threshold
- Clinicians review alert, assess patient, and decide whether to escalate care, increase monitoring, or take other clinical action

**Intended Use:** 
Support clinicians in identifying hospitalised patients at elevated risk of clinical deterioration within 24–72 hours, enabling earlier clinical assessment and intervention.

**Not Intended for:**
- Resource allocation or bed management decisions
- Discharge planning or length-of-stay predictions
- Performance evaluation of clinical staff
- Replacement of clinical judgment or human decision-making
- Triage or emergency department risk stratification (not validated for emergency setting)

**Clinical Users:**
- Nurses (primary alert recipients; assess patient and inform doctors)
- Doctors (make treatment and escalation decisions based on alert and patient assessment)
- Ward managers (allocate staffing and resources based on alert information)

---

## 3. Clinical Safety Objectives

The system must meet the following clinical safety objectives:

1. **Accurate Risk Prediction:** Model predictions correlate with actual deterioration outcomes with sufficient accuracy to be clinically useful
2. **Safety Across Populations:** Model performs equally across age, sex, ethnicity, and comorbidity groups; no demographic group is systematically under-treated or over-treated
3. **Interpretability:** Clinicians can understand predictions sufficiently to assess validity and override alerts confidently
4. **Human-Centred Design:** System augments clinical judgment; clinicians retain authority to override, ignore, or escalate alerts
5. **Alert Appropriateness:** Balance between sensitivity (catch true deterioration) and specificity (avoid alert fatigue); alerts are clinically actionable
6. **Safe Failure Modes:** System fails safely; clinicians are notified if system becomes unavailable; manual fallback procedures exist
7. **Incident Responsiveness:** Adverse events and near-misses are detected and escalated; system can be rapidly paused or adjusted if safety concerns arise

---

## 4. Clinical Requirements and Acceptance Criteria

### 4.1 Model Performance Acceptance Criteria

**Sensitivity (True-Positive Rate):**
- **Requirement:** Model must correctly identify ≥90% of patients who will experience deterioration within the prediction window
- **Rationale:** False negatives (missed deterioration) are the primary clinical safety risk; missing 1 in 10 at-risk patients is unacceptable for a safety-critical system
- **Measurement:** Calculate retrospectively on validation cohort (≥1000 admissions); stratify by age, sex, ethnicity, comorbidity
- **Acceptance:** Sensitivity ≥90% overall; ≥88% in any demographic/clinical subgroup (variance ≤2%)
- **Clinical Impact of Failure:** If FNR (false-negative rate) >10%, system offers no safety advantage over current EWS; recommendation is to redesign model or not deploy

**Specificity (True-Negative Rate):**
- **Requirement:** Model must correctly identify ≥80% of patients who will NOT experience deterioration (avoid alert fatigue)
- **Rationale:** False positives (unnecessary alerts) create workload burden and may reduce clinician trust in system; too many false alerts leads to "alert fatigue" and clinician disengagement
- **Measurement:** Calculate retrospectively on validation cohort; stratify by demographics
- **Acceptance:** Specificity ≥80% overall; ≥75% in any subgroup (variance ≤5%)
- **Clinical Impact of Failure:** If FPR >20%, alert fatigue risk is high; each alert requires clinician assessment and charting, adding ~5–10 minutes per alert; 50 wards × 5 false alerts/day = 250 alerts/day = significant clinical workload; system may not be adopted or may be disabled by clinicians

**Positive Predictive Value (PPV):**
- **Requirement:** When system issues an alert, ≥20% of alerted patients actually deteriorate within prediction window
- **Rationale:** PPV reflects "alert appropriateness"; if only 5% of alerts result in actual deterioration, alerts are not actionable and reduce clinical confidence
- **Measurement:** Calculate on validation cohort; this depends on prevalence of deterioration in population
- **Acceptance:** PPV ≥20% (i.e., ≥1 in 5 alerts represents true-positive deterioration)

**Negative Predictive Value (NPV):**
- **Requirement:** When system does NOT issue an alert, ≥95% of non-alerted patients will not deteriorate
- **Rationale:** NPV is most critical for safety; clinicians may reduce monitoring frequency on non-alerted patients; if 5% of non-alerted patients deteriorate, safety risk is significant
- **Measurement:** Calculate on validation cohort
- **Acceptance:** NPV ≥95%

**Calibration:**
- **Requirement:** Model-predicted probabilities must align with observed event rates (e.g., if model predicts 20% risk, ~20% of those patients actually deteriorate)
- **Rationale:** Miscalibrated models (e.g., model systematically over-predicts) lead to incorrect alert thresholds and performance mismatches
- **Measurement:** Calibration plot and Hosmer-Lemeshow test on validation cohort
- **Acceptance:** Predicted probability within ±5 percentage points of observed event rate across prediction range

---

### 4.2 Fairness and Equity Requirements

**Performance Equity:**
- **Requirement:** Model sensitivity, specificity, PPV, NPV must not vary by >5 percentage points across demographic and clinical subgroups
- **Subgroups to assess:** 
  - Age (≤50, 51–70, >70 years)
  - Sex (male, female)
  - Ethnicity (where data available; White British, Asian, Black African/Caribbean, other)
  - Comorbidity profile (0 comorbidities, 1–2, ≥3 comorbidities)
  - Admission type (emergency, elective, transfer)
- **Rationale:** Differential model performance across groups may lead to under-treatment of specific populations; AI bias risks disproportionate harm to vulnerable groups
- **Measurement:** Stratified performance analysis in validation study
- **Acceptance:** Material differences (>5 percentage points) in any subgroup requires investigation; options include:
  - Model redesign or retraining to improve subgroup performance
  - Population-specific risk thresholds (e.g., lower alert threshold for subgroups with worse model performance)
  - Restriction of system to subgroups where performance acceptable, with manual alternative for other patients
  - System not approved if fairness gaps cannot be closed

**Disparate Impact Assessment:**
- **Requirement:** System must not result in disproportionate alert rates or clinical outcomes across demographic groups
- **Measurement:** Compare alert generation rate, alert response rate, clinical escalation rate, and outcomes (ICU admission, death) across groups
- **Acceptance:** If alert rates or outcomes differ >10% across groups, assess whether this is explained by true differences in deterioration risk (legitimate) or by model bias (unacceptable)

---

### 4.3 Explainability and Interpretability Requirements

**Requirement:** Clinicians must be able to understand why an alert was generated and assess alert validity confidently

**Interpretability Options:**
1. **Inherently Interpretable Model:** Model uses clear, simple features with human-understandable weights (e.g., logistic regression with coefficients; decision tree with clear rule path)
   - Clinician can see: "Alert triggered because: heart rate 110 + respiratory rate 28 + oxygen sat 92% → high risk"
   - Strength: immediate transparency; no specialist ML knowledge required
   - Weakness: may not achieve optimal predictive accuracy

2. **Local Explainability (Black-Box + Explanation):** Model is accurate but not inherently interpretable (e.g., neural network, gradient boosting); post-hoc explanation method (LIME, SHAP, attention maps) explains individual predictions
   - Clinician sees: "Alert triggered by: vital signs pattern similar to 120 historical cases with deterioration (97% match)"
   - Strength: can achieve higher accuracy while remaining interpretable
   - Weakness: explanations may be approximate and require technical explanation

**Acceptance Criteria:**
- Clinicians must score interpretability ≥7/10 in usability testing (can they explain alert rationale to a colleague?)
- No "unexplained" black-box alerts without supporting explanation
- Alert interface must display: risk score, key contributing factors, and confidence/uncertainty

---

### 4.4 Alert Appropriateness and Clinician Workflow

**Alert Volume:**
- **Target:** 10–20% of patient-days generate an alert (if 50 ward patients, 5–10 alerts per day)
- **Rationale:** Alerts must be frequent enough to catch deterioration but infrequent enough to avoid alert fatigue
- **Measurement:** Monitor alert generation rate daily in pilot deployment; track clinician override rate
- **Acceptance:** If alert rate <5% or >30% of patient-days, re-evaluate alert thresholds or model

**Alert Fatigue:**
- **Requirement:** System must not contribute to clinician alert fatigue or disengagement
- **Measurement:** Clinician survey post-pilot asking: "Do alerts feel appropriate?" "How often do you ignore alerts?" "Does alert volume feel manageable?"
- **Acceptance:** >80% of clinicians must report alert appropriateness; override rate must be <50%

**Clinician Decision Support:**
- **Requirement:** Alerts must be presented with sufficient context (patient name, bed, current vital signs, recent trends, alert rationale) to enable rapid clinical assessment
- **Implementation:** Alerts delivered to ward staff station, nursing handover, and (optionally) individual pagers/phones; include patient ID, risk score, key factors; link to patient EPR
- **Acceptance:** Clinicians report alert information is sufficient to make escalation decision without additional data review (survey score ≥7/10)

**Alert Override Capability:**
- **Requirement:** Clinicians must be able to override, snooze, or dismiss alerts if they assess patient as clinically stable
- **Rationale:** Clinicians retain decision-making authority; over-reliance on automated alerts is unsafe
- **Measurement:** Track override patterns; if override rate >50%, may indicate false-positive alerts or poor alert calibration
- **Acceptance Criteria:** System allows clinician override; override decision is logged (for audit and learning)

---

### 4.5 Safe Failure Modes

**System Unavailability:**
- **Requirement:** If AI system becomes unavailable, clinicians must be notified and fallback procedures activated
- **Fallback:** Revert to manual Early Warning Score (EWS); nursing staff increase observation frequency on known high-risk patients; escalation procedures remain unchanged
- **Acceptable Downtime:** ≤1 hour without patient impact (alerts may be missed briefly, but patients with known risk factors get increased observations); ≤15 minutes before escalation to IT Operations
- **Measurement:** Monitor system uptime; track alert delivery latency

**Data Quality Failure:**
- **Requirement:** If critical EPR data is missing or delayed (e.g., vital signs not updated for >2 hours), system must alert data stewards and not issue unreliable risk predictions
- **Acceptable Data Latency:** Vital signs ≤30 minutes old; labs ≤4 hours old
- **Measurement:** Monitor data freshness daily; report data quality issues to Clinical Data Steward

**Model Failure (Out-of-Distribution Data):**
- **Requirement:** Model performance is validated only on data similar to training distribution; if model encounters atypical patient presentations, predictions may be unreliable
- **Mitigation:** Confidence intervals or uncertainty quantification on risk scores; alerts with low confidence flagged as "uncertain" requiring extra clinician scrutiny
- **Measurement:** Track prediction uncertainty; flag low-confidence alerts for clinical review

---

### 4.6 Incident Detection and Escalation

**Safety Incident Categories:**
- **Near-Miss:** Alert generated; clinician assessed patient as stable; patient subsequently deteriorated but no harm resulted (e.g., patient recovered with supportive care)
- **Adverse Event (Preventable):** Alert missed; patient deteriorated without alert notification; patient suffered harm (cardiac arrest, unplanned ICU, death)
- **Adverse Event (Non-Preventable):** Patient deteriorated rapidly despite appropriate clinical care; alert would not have prevented harm
- **False-Positive Harm:** Alert generated; clinician escalated care based on alert; escalation caused unnecessary intervention or harm (e.g., unnecessary transfer to ICU, complications from invasive monitoring)

**Detection Mechanism:**
- Clinician incident reporting (standard NHS incident form, linked to AI system)
- Retrospective audit: clinical review of non-alerted patients who suffered adverse outcomes (quarterly)
- Automated alert: adverse outcome in patient within 24 hours of alert (flags for review)

**Escalation Authority:**
- Any incident involving patient harm: Clinical Safety Lead + Chief Medical Officer + Incident Response Team
- Systematic pattern (e.g., >2 similar incidents in <4 weeks): AI Governance Board notified; system review and potential suspension initiated

---

## 5. Clinical Validation Plan

### 5.1 Retrospective Validation Study (Pre-Deployment)

**Objective:** Demonstrate that model performance on this Trust's patient population meets acceptance criteria (sensitivity ≥90%, specificity ≥80%, fairness requirements)

**Design:** Retrospective cohort study using historical admissions data

**Population:**
- Admissions to medical and surgical wards (exclude ICU, A&E, paediatrics) from past 12–24 months
- ≥1,000 admissions (minimum sample size for adequate statistical precision and subgroup analysis)
- Inclusion: all admissions with complete vital signs, observation, and laboratory data
- Exclusion: patients admitted for end-of-life care (where deterioration is expected/planned)

**Data Source:** EPR extracts for enrolled admissions; linked to outcomes data (discharge summaries, ICU transfer records, mortality data)

**Outcome Definition:**
- **Primary Outcome:** Clinical deterioration = unplanned critical event (unplanned ICU admission, cardiac arrest, or death) within 24–72 hours of model prediction
- **Rationale:** These outcomes represent the clinical events the system is intended to prevent
- **Measurement:** Extract from EPR discharge summaries, ICU admission records, hospital-acquired complication coding

**Predictions:**
- Apply trained model retrospectively to historical EPR data for each enrolled admission
- Generate risk score at multiple time points (e.g., daily at midnight for each admission day)
- Set alert threshold at model prediction probability (to be determined from ROC curve; typically ~20–30%)

**Analysis:**
- Calculate sensitivity (true-positive rate), specificity (true-negative rate), PPV, NPV at chosen threshold
- Calculate 95% confidence intervals using exact binomial or logistic regression
- Stratify analysis by age, sex, ethnicity, comorbidity, admission type
- Assess performance consistency across subgroups (variance analysis)
- Calibration plot: compare predicted probability vs observed event rate
- ROC curve: assess discrimination at multiple thresholds
- Secondary analysis: assess impact of different alert thresholds on sensitivity/specificity trade-off

**Success Criteria:**
- Sensitivity ≥90% (FNR <10%); no subgroup <88%
- Specificity ≥80%; no subgroup <75%
- PPV ≥20%; NPV ≥95%
- Performance variance across subgroups ≤5 percentage points
- Calibration within ±5 percentage points

**Timeline:** 3–4 weeks (data extraction + analysis)

**Ownership:** Clinical Informatics Lead (with support from Data Scientist, Statistician)

**Independent Review:** External clinical informatics consultant reviews methodology, analysis, and findings before presentation to Clinical Safety Lead

---

### 5.2 Pilot Deployment and Clinical Audit (Weeks 1–8 Post-Deployment)

**Objective:** Validate that model performance translates to real-world operation and generates clinical benefit without harm

**Design:** Prospective pilot deployment on single ward (10–15 beds) with detailed monitoring and clinical review

**Ward Selection:** Medical ward with high acuity and frequent deterioration events (to enable rapid assessment of alert sensitivity and outcomes)

**Monitoring:**
- **Daily Metrics:** Alert generation rate, alert override rate, system availability, data quality
- **Weekly Metrics:** Provisional outcomes (ICU transfers, deaths) in alerted vs non-alerted patients; clinician feedback survey
- **Weekly Clinical Safety Review:** Clinical Safety Lead and Ward Manager review all alerts and outcomes; assess for safety issues

**Outcomes Tracked:**
- Alert sensitivity (% of patients who deteriorate that receive alert)
- Alert specificity (% of non-deteriorating patients that do not receive alert)
- Clinician override rate (% of alerts clinicians deem not clinically actionable)
- Clinical escalation rate (% of alerts resulting in clinical action: increased monitoring, investigations, or ICU transfer)
- Patient outcomes: unplanned ICU transfers, cardiac arrests, deaths (compared to baseline historical rate)
- Alert fatigue (clinician survey)

**Success Criteria for Pilot:**
- Alert generation rate 10–25% of patient-days (consistent with validation study)
- No unplanned patient deaths directly attributable to missed alerts (near-misses acceptable; adverse events trigger investigation)
- Clinician override rate <50%
- Clinical Governance Committee approves continuation to full deployment

**Safety Stopping Rules:**
- >1 patient death directly attributable to system failure (missed alert) → system suspended for investigation
- >3 serious adverse events (e.g., delayed recognition of deterioration despite alert) in 4-week period → system paused for review
- System unavailability >4 hours on any day → escalation and remediation required

**Timeline:** 8 weeks (4-week intensive monitoring + 2-week decision gate + 2-week adjustment before full rollout)

**Ownership:** Clinical Safety Lead + Clinical Informatics Lead + Pilot Ward Manager

---

### 5.3 Ongoing Clinical Audit (Post-Deployment)

**Objective:** Measure clinical benefit and detect safety issues in real-world operation

**Design:** Quarterly prospective clinical audit with outcome measurement and alert appropriateness review

**Patient Cohort:** All patients admitted to wards with AI system deployed during calendar quarter

**Outcomes Measured:**
1. **Primary Outcome:** Unplanned critical events (ICU admission, cardiac arrest, death) within hospital stay; compare rate before/after system deployment
2. **Secondary Outcomes:** Length of stay, hospital-acquired complications, rapid response team activations
3. **Alert Performance:** Proportion of patients experiencing deterioration who received alert (real-world sensitivity); proportion of alerts resulting in clinical action

**Alert Appropriateness Review:**
- Random sample of 50 alerts per quarter; clinical review of each alert
- Clinician assessor (senior nurse or doctor) reviews alert context and determines: was alert clinically appropriate? Did alert result in appropriate clinical action? What was patient outcome?
- Categorise alerts as: True Positive (alert appropriate, outcome positive), False Positive (alert inappropriate or led to unnecessary escalation), Missed Alert (deterioration occurred without alert)

**Subgroup Analysis:**
- Stratify outcomes by age, sex, ethnicity, comorbidity, admission type to assess fairness and identify disparities

**Reporting:**
- Quarterly audit report to Clinical Governance Committee with findings, trends, and recommendations
- Annual report to AI Governance Board

**Success Criteria:**
- Clinical benefit: unplanned ICU admissions or mortality reduced by ≥5% compared to baseline (if effect not observed, reassess system value)
- Alert appropriateness: ≥80% of alerts categorised as true positives
- Safety: no preventable patient deaths attributable to system failure

**Timeline:** Ongoing; quarterly reporting

**Ownership:** Quality Improvement Lead (with support from Clinical Audit Lead)

---

## 6. Clinical Governance Procedures

### 6.1 Clinician Training and Competency

**Training Content:**
1. System purpose and intended use (clinical need, expected benefit, limitations)
2. How to interpret alerts (risk score, key contributing factors, confidence/uncertainty)
3. Alert workflow (where alerts appear, how to acknowledge, how to override)
4. Clinical decision-making (when to act on alerts, when to ignore; alert is NOT command to escalate)
5. How to assess alert validity (clinician clinical judgment supersedes system alert)
6. When and how to escalate (if patient clinically unwell, escalate regardless of alert; if alert but patient clinically stable, assess for unnecessary escalation)
7. Incident reporting (how to report safety concerns related to system)
8. Know your limitations (system validated only on general ward patients; performance unknown in other settings)

**Training Methods:**
- Mandatory e-learning module (30 minutes) before system access
- In-person ward-based training session (1 hour) led by Clinical Informatics Lead or designated champion
- Competency assessment: short quiz (≥80% pass required) or observed supervised use
- Refresher training annually

**Ongoing Support:**
- Clinical champion(s) designated on each ward (nurse and doctor) available for questions
- FAQ document and runbook available
- Help desk / escalation contact for technical issues

**Competency Assurance:**
- Track training completion rates; target ≥95% of clinical staff on each ward
- Monitor quiz pass rates; remedial training for staff <80%

---

### 6.2 Alert Escalation Procedures

**Alert Notification:**
- Alert displayed on ward staff station or clinical dashboard (visible to nursing staff)
- If alert generated outside business hours or on night shifts, alert to on-call doctor by phone/pager (to be determined)
- Alert includes patient name, bed number, risk score, and key contributing factors

**Clinical Response Flow:**
1. Nurse receives alert; reviews alert context (current vital signs, recent notes)
2. Nurse assesses patient clinically (brief bedside check): Is patient clinically well? Any signs of distress, drowsiness, or vital sign abnormality?
3. If patient clinically WELL: Nurse may override alert (decision logged) and increase monitoring; no escalation required
4. If patient clinically UNWELL or alert deemed clinically plausible: Nurse escalates to doctor
5. Doctor assesses patient and decides: increase monitoring, investigate, escalate to ICU, or reassure and observe
6. All alert assessments documented in EPR (alert generated, action taken, outcome)

**Escalation Criteria (Regardless of Alert):**
- Clinician should escalate care if patient shows signs of deterioration, regardless of whether alert was generated
- System is tool to prompt assessment; clinical judgment is final authority

**Override Logging:**
- When clinician overrides alert (deems not clinically actionable), decision logged in system
- Monthly reporting of override patterns to Clinical Safety Lead (high override rate may indicate false-positive alerts requiring model adjustment)

---

### 6.3 Clinical Incident Reporting and Response

**Incident Reporting:**
- Any adverse event or near-miss related to AI system (missed alert, false-positive alert, system failure) reported on standard NHS incident form
- Incident form includes: incident type, patient harm (if any), brief description, and link to AI system
- Clinician submits incident to ward manager; escalated to Clinical Safety Lead

**Safety Incident Triage (Within 24 Hours):**
- **Critical (Patient Harm):** Death or serious harm attributable to system failure (e.g., missed alert causing missed diagnosis) → immediate escalation to Chief Medical Officer and incident response team; system review and potential suspension
- **High (Near-Miss or Preventable Harm):** Alert missed; patient deteriorated; clinician recognised deterioration without system alert → investigation by Clinical Safety Lead; assess if systematic model issue
- **Medium (Workflow Issue):** Alert generated appropriately but clinician did not receive notification (system/communication failure) → IT operations investigation
- **Low (Expected Variation):** Patient assessed as clinically stable despite alert; no subsequent deterioration → expected; monitor for patterns

**Incident Investigation (Serious Incidents):**
- Assign investigator (Clinical Safety Lead + Clinical Informatics Lead)
- Timeline: root cause analysis completed within 72 hours of critical incident
- Investigation addresses: what happened, why, contributing factors (model drift? data quality? user error? system failure?), what could prevent recurrence
- Findings and recommendations presented to Clinical Governance Committee
- Decision: continue operation, modify procedures, restrict system, or suspend/retire system

**Learning from Incidents:**
- Quarterly incident summary to clinical staff (anonymised cases, key lessons, system improvements made)
- Incident trends reviewed by Clinical Governance Committee and AI Governance Board
- Systemic issues (recurring pattern of false-positive alerts, fairness disparities) addressed through model retraining or governance procedure changes

---

## 7. Harm Scenarios and Mitigation

### 7.1 Potential Harms

| Harm Scenario | Description | Likelihood (Pre-Control) | Severity | Mitigation |
|---|---|---|---|---|
| **Missed Deterioration (False Negative)** | Patient deteriorates but system does not alert; clinician misses deterioration; patient experiences cardiac arrest or preventable death | Medium | Catastrophic | Model validation to achieve FNR <10%; ongoing monitoring; clinical audit to detect missed cases; system suspension if FNR >7% |
| **Alert Fatigue (False Positive)** | Too many unnecessary alerts; clinician ignores alerts; clinician disengagement reduces clinical attention even for true positives | Medium | Major | Model validation to achieve FPR <20%; alert threshold tuning; clinician feedback; monitoring of override rates; alert redesign if override >50% |
| **Bias Against Demographic Group** | Model performs worse for specific age, sex, ethnicity, or comorbidity groups; these patients systematically under-detected or over-alerted; disparate clinical outcomes | Low | Major | Fairness assessment in validation study; stratified performance analysis; equity governance policy; system restriction or redesign if disparities found |
| **Over-Escalation (Unnecessary ICU Transfer)** | Alert-driven unnecessary escalations to ICU or invasive monitoring; patient exposed to ICU risks (central lines, ventilator-associated pneumonia) without clinical benefit | Low | Moderate | Alert appropriateness review in pilot and ongoing audit; clinician training on alert interpretation; alert override capability; monitoring of escalation rates |
| **System Unavailability (No Fallback)** | AI system fails; clinicians unaware of system unavailability; clinicians expect alerts; missed deterioration without manual fallback | Low | Moderate | System monitoring with automatic failover; alerts to IT Ops if system down >15 minutes; clinician notification procedure; manual EWS fallback activated; system recovery target <1 hour |
| **Data Breach (Patient Privacy)** | Vendor or cloud provider unauthorised access to patient data; personal data exfiltration; GDPR breach and patient harm to privacy | Low | Major | Data Processing Addendum restricting vendor access; encryption of data in transit and at rest; audit rights and regular vendor audits; breach notification procedures; cyber incident response plan |
| **Model Drift (Gradual Performance Degradation)** | Over time, patient population changes (new comorbidities, new medications, new care pathways); model trained on historical data no longer representative; predictions become unreliable | Medium | Moderate | Ongoing performance monitoring (monthly); comparison of predicted vs actual outcomes; alert thresholds triggering investigation (e.g., override rate >50%); annual model retraining or redesign if drift detected |
| **Regulatory Non-Compliance (Unexpected Medical Device Classification)** | System later classified as medical device under MDR 2002/768; deployment without regulatory approval creates compliance risk | Low | Major | Early legal assessment of medical device classification; regulatory pathway planning before deployment; compliance monitoring |

---

### 7.2 Safety by Design Principles

**Principle 1: Clinician Authority**
- System is decision-support tool; clinicians retain full authority to assess, override, or escalate regardless of alert
- Training emphasises: "Use clinical judgment; alert is prompt to assess patient, not instruction to escalate"

**Principle 2: Transparency**
- Alerts include rationale (key features contributing to risk score) so clinician can assess validity
- Explainability testing with clinicians before deployment
- "Unexplained" black-box alerts not acceptable without supporting explanation method

**Principle 3: Safe Failure**
- System designed to fail gracefully; system unavailability does not prevent clinical care
- Fallback to manual EWS; increased monitoring frequency on high-risk patients
- Alerts to data stewards if data quality drops below threshold

**Principle 4: Continuous Monitoring**
- Real-world performance monitored daily/weekly to detect drift, bias, or systematic issues
- Alert thresholds defined to trigger investigation (e.g., if override rate >50%, sensitivity <88%, fairness disparity detected)
- Regular clinical audit (quarterly) to validate benefit and detect harm

**Principle 5: Reversibility**
- System can be paused or suspended for investigation without patient harm
- Procedures and training to switch to manual EWS within hours if needed
- Clear criteria for system suspension and retirement

---

## 8. Clinical Evidence Base and Risk Tolerance

### 8.1 Evidence for Effectiveness of Early Warning Systems

**Literature Summary:**
- Early Warning Scoring systems (manual EWS, Rapid Response Teams) reduce in-hospital mortality by 0.5–2% when implemented effectively (NICE Quality Standard QS106)
- AI-powered early detection systems used in comparable hospital settings show promise; published case studies report 5–15% reduction in unplanned ICU admissions
- However, evidence is limited to published case studies (potential publication bias); randomised controlled trials of AI deterioration prediction are lacking

**Confidence Level:** Moderate for concept (early detection beneficial); uncertain for this specific model and population (requires validation)

**Risk Tolerance Implication:** System must demonstrate clinical effectiveness in this Trust through prospective audit; if audit shows no benefit, system should be reviewed or retired even if technically performing as designed

---

### 8.2 Risk Tolerance for False-Negative and False-Positive Rates

**False-Negative Tolerance (FNR <5% Acceptable):**
- Rationale: If system misses 1 in 20 at-risk patients, benefit is marginal compared to current EWS; clinical staff may lose confidence
- Comparison: Current manual EWS estimated to miss 20–30% of deterioration; system with FNR 5% represents significant improvement
- If FNR >10%: system not recommended for deployment

**False-Positive Tolerance (FPR <20% Acceptable):**
- Rationale: Each alert requires ~5–10 minutes clinician time for assessment and documentation; 50-bed ward × 20% FPR = ~10 false alerts daily = ~2 FTE clinician time daily
- Workload impact is significant but potentially acceptable if alerts are at appropriate times (e.g., not during critical care activities)
- If FPR >30%: alert fatigue risk high; system not recommended or alert thresholds must be increased (reducing sensitivity)

**Clinical Safety Committee Endorsement Required:** Before deployment, Clinical Safety Lead and Clinical Governance Committee must formally endorse the risk tolerance decision

---

## 9. Clinical Safety Approval Decision

**Decision Requested:**

Is the AI Patient Deterioration Prediction System acceptable for proceeding to pilot deployment, conditional on governance gates?

**Approval Conditions:**

- [ ] Risk Assessment approved by AI Governance Board (GOVERN, MAP, MANAGE functions mapped; residual risks acceptable)
- [ ] Governance Policy approved; Clinical Safety Lead named as system owner with clear authority
- [ ] Model Validation Study shows sensitivity ≥90%, specificity ≥80%, fairness requirements met
- [ ] Clinician training plan approved; competency assessment designed
- [ ] Incident response procedures and clinical audit plan operational
- [ ] Clinical Safety Lead and Clinical Governance Committee endorse risk tolerance decision
- [ ] Vendor/cloud infrastructure approved by Information Security; Data Processing Addendum executed
- [ ] Pilot deployment plan approved; pilot ward and pilot lead identified

**Approval Authority:** Clinical Safety Lead, Clinical Governance Committee

**Conditional Approval:** System approved for pilot deployment (Gate 5) pending successful completion of pre-deployment gates (Gates 2–4)

**Safety Caveat:** This clinical safety assessment is based on planned system design, model assumptions, and governance procedures. Clinical safety depends critically on:
1. Model validation results (if FNR >10% or fairness disparities >5%, system not approved for deployment)
2. Effective governance procedures (incidents must be detected and escalated; system must be suspendable)
3. Clinician competency (training and supervised use essential; over-reliance on alerts creates new safety risk)

---

## 10. Review and Revision

This Clinical Safety Assessment is reviewed:
- **Annually:** Or when major changes to system design, model, or clinical environment occur
- **Incident-Driven:** If serious incident occurs, safety assessment reviewed within 30 days
- **Pilot Outcomes:** Assessment revised based on pilot validation results and clinical audit findings

**Next Review Date:** 2026-12-11 or upon completion of model validation study

---

## 11. Related Documents and References

- Use Case: AI-002-patient-deterioration.md
- Risk Assessment: AI-002-patient-deterioration-risk-assessment.md
- Governance Policy: AI-002-patient-deterioration-governance-policy.md
- Data Protection Impact Assessment: AI-002-patient-deterioration-dpia.md
- NICE Quality Standard QS106: Acutely Ill Adults in Hospital (2015)
- UK GDPR and NHS Data Security & Protection Toolkit
- NIST AI Risk Management Framework 1.0

---

**Prepared by:** Clinical Safety Lead  
**Endorsed by:** [Clinical Governance Committee signature pending]  
**Status:** Ready for Clinical Governance Committee review  
**Effective Date:** Upon approval by Clinical Governance Committee

