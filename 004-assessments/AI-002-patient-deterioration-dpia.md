# Data Protection Impact Assessment (DPIA)
## Patient Deterioration Prediction System
### SentinelAI Governance Portfolio

**Document Status:** Draft  
**Date:** 2026-09-11  
**Review Date:** 2026-12-11  
**Prepared by:** Privacy Officer (with Data Protection Lead, Information Security, Clinical Informatics)  
**Approval Authority:** Privacy Officer, Data Protection Committee  
**DPIA ID:** DPIA-002-PatientDeterioration-001  
**Jurisdiction:** UK (Data Protection Act 2018, UK GDPR)

---

## 1. Executive Summary

This Data Protection Impact Assessment (DPIA) evaluates compliance of the proposed AI-powered Patient Deterioration Prediction System with UK GDPR and Data Protection Act 2018. The assessment identifies processing purposes, lawful basis, processing activities, personal data involved, recipients, storage location, and residual privacy risks.

**Key Findings:**
- Processing of patient personal data (vital signs, observations, laboratory results, clinical notes) is necessary for stated clinical purpose (deterioration prediction)
- Legal basis for processing identified: **Task in Public Interest** (NHS healthcare management; lawful basis under GDPR Article 6(1)(e) and DPA 2018 Schedule 1 Part 1)
- High-risk processing triggers mandatory DPIA (continuous monitoring of health data; AI model; third-party vendor involvement)
- Material privacy risks identified and mitigated (vendor data access, data retention, cross-border transfer if cloud provider outside UK)
- Patient information and consent mechanisms require documentation
- Recommended controls: Data Processing Addendum, encryption, access controls, audit rights, data deletion procedures

**Privacy Verdict:** Processing is lawful and proportionate, conditional on recommended controls being implemented and documented before system deployment.

---

## 2. Data Processing Context

### 2.1 Purpose and Legal Basis

**Primary Purpose:**
To predict which hospitalised patients are at risk of clinical deterioration (unplanned critical event, cardiac arrest, unplanned ICU admission, or death) within a defined timeframe (24–72 hours), enabling earlier clinical assessment and intervention to improve patient outcomes.

**Secondary Purpose:**
To evaluate the clinical effectiveness of the AI system through real-world monitoring and audit (optional; requires separate patient information and consent if used for research or publication).

**Legal Basis:**

Under UK GDPR Article 6 and Data Protection Act 2018, processing is lawful under **Task in Public Interest:**

- **GDPR Article 6(1)(e):** Processing is necessary for the performance of a task carried out in the public interest or official authority vested in the controller (NHS Trust)
- **DPA 2018 Schedule 1 Part 1 Paragraph 2:** Processing is necessary for the purposes of a legal obligation, or in the exercise of official authority vested in the controller
- **Healthcare Exemption:** Processing of health data is permitted under GDPR Article 9 (and Data Protection Act 2018 Schedule 1 Part 2) for healthcare management purposes

**Rationale for Legal Basis:**
- NHS Trust has legal duty to provide safe, effective, and person-centred care to patients (Health and Social Care Act 2008)
- Patient deterioration detection is essential to fulfilling that duty
- Processing is confined to clinical use within the Trust; does not use data for commercial benefit or secondary purposes without separate lawful basis
- Scope of processing is proportionate to stated purpose

**Supplementary Information:**
- **Patient Consent:** Not required for primary purpose (task in public interest); however, patients must be informed via privacy notice
- **Alternative Bases Not Used:**
  - Consent: Trust does not rely on consent because patients may lack capacity or be unable to refuse care; task in public interest is more robust
  - Legitimate Interests: Task in public interest is more appropriate for healthcare settings than legitimate interests balancing
- **Secondary Use (Research/Publication):** If system performance data or outcomes are used for research publication, separate lawful basis (consent or research exemption under GDPR Article 89 and DPA 2018) is required

---

### 2.2 Data Controller and Processor

**Data Controller:** NHS Trust (the organisation implementing the system and responsible for patient care)

**Responsibilities:**
- Determine purpose and means of processing (health data for deterioration prediction)
- Ensure processing is lawful, fair, transparent
- Implement appropriate technical and organisational measures to protect personal data
- Respond to subject access requests and other data subject rights requests
- Report data breaches to ICO and (if high risk) to affected patients
- Maintain records of processing activities

**Data Processor(s):** 

**Option 1 (Internal Model):** If AI model is developed internally:
- No external processor; Trust is controller and processor

**Option 2 (Vendor-Supplied Model or Cloud-Hosted):** If model is supplied by vendor or hosted on cloud platform (e.g., Azure Machine Learning, AWS SageMaker):
- **Primary Processor:** Vendor or cloud provider; enters into Data Processing Addendum (DPA) with Trust
- **Sub-Processors:** Cloud vendor's infrastructure providers (e.g., Microsoft Azure, AWS) may be sub-processors; must be listed in DPA

**Processor Responsibilities:**
- Process personal data only on instructions from Trust
- Implement technical and organisational security measures (encryption, access controls, audit logging)
- Assist Trust with data subject rights requests (access, deletion, portability)
- Notify Trust immediately of suspected data breaches
- Allow Trust audit rights and inspections
- Do not use personal data for own purposes (secondary use requires separate lawful basis and Trust consent)

**Data Processing Addendum (DPA):**
- **Mandatory:** If any external vendor or cloud provider processes patient data
- **Content:** Must specify personal data processed, processing activities, security measures, sub-processors, data location, retention, deletion procedures, audit rights, breach notification
- **Status:** Not yet negotiated; required before system deployment (Gate 4)

---

### 2.3 Data Categories and Retention

**Personal Data Processed:**

| Data Category | Description | Retention Period | Justification |
|---|---|---|---|
| **Identifiable Patient Data** | Patient name, NHS number, hospital ID, admission date, ward/bed | Active admission + 30 days | Required for alert delivery and clinical action; deleted 30 days after discharge |
| **Vital Signs** | Temperature, heart rate, blood pressure, respiratory rate, oxygen saturation, consciousness level | Active admission + 90 days | Required for model input and monitoring; retrospective audit of system performance requires 90-day look-back |
| **Observations** | Nursing observations, urine output, fluid balance, clinical notes | Active admission + 90 days | Required for model input and clinical context; retained as per EPR retention policy |
| **Laboratory Results** | Full blood count, chemistry, coagulation, blood gases | Active admission + 90 days | Required for model input; retained as per EPR/pathology retention policy |
| **Clinical Events** | Medications, medication changes, falls, infections, procedures | Active admission + 90 days | Required for model input and clinical context |
| **Model Predictions (Risk Scores)** | AI model output, risk score, alert generation time, alert threshold met | Active admission + 90 days | Required for system performance monitoring, clinical audit, incident investigation |
| **Alert Response Logs** | Clinician alert override, action taken, clinical notes documenting response | Active admission + 90 days | Required for audit trail and clinical decision accountability |
| **Aggregated/Anonymised Data** | De-identified performance metrics, alert rates, outcomes statistics | Indefinite | Non-personal; retained for operational monitoring and research |

**Retention Justification:**
- During admission + 30 days: patient may be readmitted; recent data may be clinically relevant
- Up to 90 days: enables retrospective performance audit and incident investigation
- Longer retention (>90 days): not necessary for clinical purpose; deleted or anonymised after period

**Deletion Procedure:**
- Automatic deletion scheduled 90 days post-discharge using EPR audit trail
- Exception: if incident investigation ongoing, data retained under legal hold until investigation completed (notified to data subject if required)
- Data subject may request earlier deletion (subject access/deletion right); deletion processed within 30 days unless clinical reason to retain

**Special Category Data (Health Data):**
- All vital signs, observations, and laboratory results are health data under GDPR Article 9
- Processing justified under healthcare exemption (Article 9(2)(h)) for health management purposes

---

## 3. Stakeholders and Data Subjects

**Data Subjects:** Hospitalised patients admitted to wards where the AI system is deployed

**Stakeholders:**
- **Patients:** Data subjects; entitled to information and data subject rights
- **Healthcare Staff:** Nurses, doctors, ward managers using system to make clinical decisions
- **Clinical Governance:** Clinical Safety Lead, Infection Control, Data Protection Lead
- **Management:** Ward Managers, Hospital Management accountable for patient safety
- **Vendor/Cloud Provider:** Processes patient data under contract (DPA); responsible for data security

---

## 4. Assessment of Processing Activities

### 4.1 Data Flow and Processing Steps

```
EPR (data source)
  ↓ (continuous data extraction)
Data Pipeline (ELT/ETL)
  ↓ (cleaning, validation, feature engineering)
Model Input Layer
  ↓ (inference; model processes features)
AI Model
  ↓ (produces risk prediction)
Risk Score (0-100%)
  ↓ (compared to alert threshold)
Alert Logic
  ↓ (if risk > threshold)
Clinical Alert
  ↓ (delivered to nursing staff)
EPR Alert Log (audit trail)
```

**Data Processing Activities:**

1. **Extraction:** EPR queries automated vital signs, observations, labs, events for all admitted patients daily; data extracted in near-real-time or batch (hourly/daily)
2. **Cleaning & Validation:** Missing values imputed or handled; data type conversions; outlier detection (e.g., impossible vital signs marked as errors)
3. **Feature Engineering:** Raw data transformed to model-ready features (e.g., vital signs averaged over 6-hour windows; trends calculated)
4. **Model Inference:** AI model processes features and generates probabilistic risk score (0–100%) and alert decision
5. **Alert Generation:** If risk score exceeds threshold (e.g., >20%), alert generated and delivered to ward system
6. **Logging:** Alert records logged in EPR and audit trail (timestamp, patient ID, alert threshold met, alert action, clinician response)
7. **Monitoring & Audit:** Real-time and retrospective analysis of alert patterns, performance metrics, patient outcomes
8. **Deletion:** 90 days post-discharge, patient identifiable data and model outputs deleted (aggregated/anonymised metrics retained)

**Data Location and Transfers:**

**Scenario 1 (On-Premise Model):**
- Data remains in UK EPR system and Trust data centre
- No cross-border transfer
- Risk: Low (data within NHS Trust governance)

**Scenario 2 (Cloud-Hosted Model, UK Data Centre):**
- Data extracted to cloud platform (e.g., Azure UK South, AWS London)
- Processing occurs in UK data centre
- Data returned to Trust EPR for alert delivery
- No cross-border transfer
- Risk: Medium (data shared with cloud provider; mitigated by DPA and encryption)

**Scenario 3 (Cloud-Hosted Model, Non-UK Data Centre):**
- Data transferred to non-UK cloud region (e.g., US, EU)
- Processing occurs outside UK; data returned to UK for alert delivery
- **Cross-Border Transfer Risk:** Personal data transfer outside UK/EEA
- **Adequacy Decision:** If transfer to EEA country with Adequacy Decision (EU/EEA), transfer permitted
- **If Transfer to US or Other Non-Adequate Country:** Transfer requires International Data Transfer Agreement (e.g., Standard Contractual Clauses); must assess US/third-country surveillance risk (Schrems II ruling)

**Data Protection Baseline:**
- All transfers must include encryption in transit (TLS 1.2+) and at rest
- Data Processing Addendum must document transfer mechanism and safeguards
- Patient data not to be transferred outside necessary scope (e.g., not for vendor's analytics or secondary use)

**Status:** Cloud platform and data location not yet finalised; must be specified before deployment to determine transfer risk level

---

### 4.2 Access Controls and Operational Security

**Who has Access to Patient Data:**

| Role | Access Scope | Purpose | Security Controls |
|---|---|---|---|
| **EPR Administrators** | All patient data in EPR (current system) | System maintenance, user management | Already controlled by EPR governance; no change for AI system |
| **AI Model Developers** | Aggregate/anonymised historical data (ONLY; not individual patient identifiers) | Model training and validation | Code of confidentiality; data anonymisation protocols; access restricted to development environment |
| **Data Steward** | De-identified performance data (alert rates, outcomes) | System monitoring, performance audit | Confidentiality agreement; monitoring dashboard (no individual patient identifiers) |
| **Clinical Informatics** | Risk scores and alerts (for pilot and audit purposes) | Validation and clinical audit | Confidentiality agreement; access limited to audit team; all data handling logged |
| **Vendor/Cloud Provider** | Individual patient data (vital signs, observations, labs) required for model processing | Model inference and monitoring | Data Processing Addendum; encryption; access controls; audit rights |
| **Vendor Support/Infrastructure** | None (routine system support on aggregated data only; patient data not accessible to human support staff) | Technical troubleshooting | DPA must restrict support staff access; incident response procedures to minimize data exposure if troubleshooting required |
| **Audit/Compliance** | De-identified performance data and anonymised alert logs | Governance audit, compliance verification | Confidentiality agreements; access controlled to audit findings only; individual patient data not disclosed |

**Access Control Measures:**
- **Role-Based Access Control (RBAC):** Restrict access based on job role (clinicians access alerts for their patients; data stewards see aggregate metrics only; model developers never see individual patient identifiers)
- **Principle of Least Privilege:** Grant minimum access necessary for job function
- **Logging & Monitoring:** All access to patient data logged; audit trail retained for ≥1 year; suspicious access patterns escalated to Information Security
- **Encryption:**
  - **In Transit:** TLS 1.2+ for all data transfers (EPR to model, model to alert system)
  - **At Rest:** Patient data encrypted in cloud storage (AES-256 or equivalent); encryption keys managed by cloud provider or Trust (depending on model implementation)
- **Authentication:** Multi-factor authentication (MFA) for all staff accessing patient data systems
- **Network Isolation:** AI model environment separated from public internet; access via VPN or secure gateway only

---

### 4.3 Data Sharing with Third Parties

**Data Processors (Data Shared):**

| Third Party | Data Shared | Justification | Legal Mechanism | Risk Level |
|---|---|---|---|---|
| **Vendor (Model Provider)** | Individual patient vital signs, observations, labs, events; risk scores and alert outputs | Model inference and monitoring | Data Processing Addendum (DPA) | Medium (vendor access to sensitive health data; mitigated by DPA, encryption, audit rights) |
| **Cloud Infrastructure Provider (e.g., Microsoft Azure, AWS)** | Patient data stored in vendor's cloud; infrastructure provider acts as sub-processor | System processing and storage | DPA (naming cloud provider as sub-processor); Standard Contractual Clauses if non-UK data centre | Medium-High (data on US/non-UK infrastructure; requires cross-border transfer agreement) |
| **Clinical Governance Committee** | De-identified performance data and anonymised audit findings | Governance and safety oversight | Confidentiality agreements; internal governance | Low (data already anonymised) |
| **External Clinical Audit Firm** | De-identified patient outcome data and alert logs (if independent audit commissioned) | Clinical audit and assurance | Data Processing Addendum or Confidentiality Agreement | Medium (third-party health researchers; mitigated by DPA and anonymisation) |
| **Regulator (ICO, CQC)** | De-identified performance data and compliance documentation (if regulatory inspection or breach notification required) | Regulatory compliance and investigation | Legal obligation; GDPR Article 6 and DPA 2018 | Low (only disclosed if legally required) |

**Data Sharing NOT Permitted Without Additional Consent:**
- Commercial model improvement (vendor retraining its model on Trust patient data)
- Secondary research or publication
- Direct marketing
- Sale or licensing of aggregated datasets
- Sharing with health insurance companies, employers, or other third parties outside NHS care

**Data Sharing Policy:**
- Default: Patient data not shared beyond Trust, processor, and necessary healthcare providers
- Exception: Secondary use requires separate explicit patient consent or lawful basis (research exemption, anonymisation)
- Documentation: All data sharing agreements must be documented in Data Sharing Register

---

## 5. Privacy Risk Assessment

### 5.1 Data Protection Risks and Mitigations

| Risk | Description | Likelihood | Severity | Mitigation | Residual Risk |
|---|---|---|---|---|---|
| **Unauthorised Access to Patient Data (Vendor or Cloud)** | Vendor or cloud provider employee accesses patient data without authorisation; data exfiltration | Medium | High | DPA restricts access; encryption; audit rights; vendor security certifications (ISO 27001); breach notification procedures | Medium (mitigated by DPA and contractual controls) |
| **Data Breach (Cyber Attack)** | Ransomware, hacking, or malware compromises patient data stored in cloud or vendor systems | Low | High | Encryption at rest; secure APIs; vulnerability management; vendor penetration testing; incident response procedures | Low (standard cloud provider protections; requires specific incident to materialise) |
| **Cross-Border Transfer Risk (Non-UK Data Centre)** | Patient data transferred outside UK to non-adequate country (US, etc.); subjected to foreign government surveillance | Medium (if US cloud provider selected) | Medium | Standard Contractual Clauses or Adequacy Decision; encryption (limits surveillance utility); UK data centre preference or data localisation | Medium (Schrems II risk; requires assessment if non-UK cloud provider used) |
| **Inadequate Data Deletion** | Patient data not deleted after 90-day retention period; indefinite storage of health data | Medium | Medium | Automated deletion procedures; audit trail of deletions; exception process for legal hold; annual retention review | Low (implemented as procedural control) |
| **Secondary Use Without Consent** | Vendor or cloud provider uses patient data for own model improvement, analytics, or secondary purposes beyond deterioration prediction | Medium (if DPA not explicit) | High | DPA explicitly restricts processing to stated purpose only; restrictions on secondary use; audit rights allowing Trust to verify compliance; vendor liability for unauthorised use | Low (mitigated by DPA and enforcement mechanisms) |
| **Data Subject Rights Not Honoured** | Patient submits access/deletion request; vendor or Trust does not respond within 30 days; patient data not deleted upon request | Low | Medium | DPA requires processor to assist with requests within 10 days; Trust maintains data subject rights process (SAR register); annual audit of compliance | Low (procedural control; depends on vendor cooperation) |
| **Lack of Transparency (Patient Unaware of Processing)** | Patient not informed via privacy notice that their data is processed by AI system; patient cannot exercise data rights | High (if privacy notice not updated) | Medium | Privacy notice updated to describe AI processing; notice distributed to patients on admission; notice posted on wards; patient information leaflet available | Low (mitigated by privacy notice update) |
| **Fairness and Bias in Processing** | AI model trained on biased historical data; uses features correlated with protected characteristics; systematically discriminates against demographic groups | Medium | High | Fairness assessment in model validation; stratified performance testing; monitoring for bias in real-world operation; data-minimisation (exclude protected characteristics from model features) | Medium (mitigated by fairness governance and monitoring, not data protection law) |
| **Data Quality and Accuracy Issues** | Incorrect or incomplete patient data in EPR leads to unreliable model predictions; patient harmed by inaccurate AI assessment | Medium | High | Data quality audit; validation of EPR data; documentation of data quality issues; clinician training on alert interpretation; ongoing monitoring of prediction accuracy | Medium (mitigated by clinical governance, not data protection) |

---

### 5.2 Privacy Impact by Data Subject

**Impact on Patients:**
- **Continuous Monitoring:** Patient vital signs and health information continuously monitored and analysed by automated system (privacy intrusion)
- **Automated Decision-Making:** AI system generates alerts that may trigger clinical escalation; patient may not be aware system influenced treatment decision
- **Secondary Use Risk:** If data used for purposes beyond stated (e.g., research, model improvement for commercial vendor), patient privacy compromised
- **Data Breach Risk:** If patient data breached, health information could be publicly disclosed or misused

**Mitigation Measures:**
- Transparency: Patient informed via privacy notice of data processing, system purpose, and rights
- Consent Option: While primary processing is task in public interest (no consent required), patients may be offered opt-out for secondary uses
- Security: Encryption and access controls to reduce breach likelihood
- Incident Response: If breach occurs, patients notified and compensated if harm results (GDPR right to compensation)

**Vulnerable Groups:**
- **Patients Lacking Mental Capacity:** May not understand privacy notice; representative (next-of-kin) to be consulted if capacity assessment indicates lack of capacity
- **Non-English Speakers:** Privacy notice and patient information available in multiple languages
- **Literacy/Accessibility:** Plain language summaries and accessible formats (large print, audio) available

---

## 6. Data Protection Compliance Obligations

### 6.1 UK GDPR Compliance

**Article 5 (Data Protection Principles):**
- **Lawfulness:** Processing is lawful (task in public interest); lawful basis documented
- **Fairness:** Processing is fair (patient informed; no deception); transparent purpose
- **Transparency:** Patient informed via privacy notice; processing activities documented
- **Purpose Limitation:** Data used only for deterioration prediction; secondary use prohibited without consent or separate lawful basis
- **Data Minimisation:** Only health data necessary for model input retained; protected characteristics excluded from model features
- **Accuracy:** Data quality controls; deletion of outdated information after retention period
- **Storage Limitation:** Retention limited to 90 days post-discharge; automatic deletion implemented
- **Integrity & Confidentiality:** Encryption, access controls, security measures implemented
- **Accountability:** DPIA completed; processing documented; risks assessed and mitigated

**Status:** Compliance achieved conditional on recommended controls implemented (below)

---

### 6.2 Data Protection Impact Assessment (DPIA) Obligation

**Trigger:** Processing high-risk (continuous monitoring of health data; AI algorithm; large-scale; systematic effects on individuals)

**Legal Requirement:** GDPR Article 35 requires mandatory DPIA before processing begins

**Status:** This document fulfils DPIA requirement

**Outcome:** DPIA identifies privacy risks and proposes mitigations (below); risk acceptable for deployment conditional on mitigations

---

### 6.3 Data Subject Rights

**Rights Enabled by Processes:**

| Right | Mechanism | Timeline |
|---|---|---|
| **Right to Information** | Privacy notice describing system, data use, rights; available on ward and in EPR | Provided on admission |
| **Right of Access (Subject Access Request)** | Patient may request copy of their health data and system outputs; Trust responds within 30 days | Subject Access Request process (standard NHS procedure) |
| **Right to Rectification** | Patient may request correction of inaccurate data; processed within 30 days | Data quality correction in EPR |
| **Right to Erasure** | Patient may request deletion; processed within 30 days (unless legal hold or clinical reason to retain) | Deletion request process; exception for active admission or ongoing clinical use |
| **Right to Restrict Processing** | Patient may request processing limited to storage only (not used for inference/alerts); processed within 30 days | Data processing restriction in EPR (disables alerts for that patient) |
| **Right to Portability** | Patient may request their data in structured format for portability to another healthcare provider; processed within 30 days | Data export in HL7 FHIR or CSV format |
| **Right to Object** | Patient may object to processing on grounds of privacy; processed within 30 days (unless legal override) | Objection process; assessment whether processing can be stopped without patient harm |
| **Right to Automated Decision-Making** | Patient has right not to be subject solely to automated decision-making with legal effect; entitled to human review | Alerts not solely automated; clinician review required before clinical action |

**Responsibility:** Trust Data Protection Officer and Privacy Team to maintain data subject rights processes

---

### 6.4 Privacy Notice and Patient Information

**Current Status:** Privacy notice must be updated to describe AI system

**Required Information in Privacy Notice:**
1. **Identity of Controller:** NHS Trust name and contact details
2. **Processing Purpose:** Predict patient deterioration risk to enable earlier clinical intervention
3. **Legal Basis:** Task in public interest (GDPR Article 6(1)(e); DPA 2018 Schedule 1)
4. **Data Categories:** Vital signs, observations, laboratory results, clinical events; not name or NHS number used in model (identifiers removed)
5. **Recipients:** Vendor (if applicable); cloud provider (if applicable); clinical staff; not shared beyond NHS care provision
6. **Retention:** Retained during admission and 90 days after; automatically deleted after retention period
7. **Data Subject Rights:** Right to access, rectification, erasure, portability, objection; how to exercise rights
8. **Complaint Procedure:** How to lodge complaint with ICO if concerned about data processing
9. **Automated Decision-Making:** System uses AI algorithm; clinician retains authority to override; system does not solely determine clinical decisions

**Patient Information Leaflet:** Separate simple explanation of system for patients (plain language, accessible formats)

**Distribution:**
- Printed notice on ward (multiple languages)
- Electronic notice in EPR
- Patient information leaflet available on admission
- Website information page

**Status:** Privacy notice update required before deployment (Gate 3/4)

---

## 7. Recommended Controls and Mitigation Measures

### 7.1 Contractual Controls

**Data Processing Addendum (DPA) — MANDATORY if vendor/cloud provider processes data**

**Essential Clauses:**
1. **Processing Scope:** Vendor processes data only for stated purpose (deterioration prediction in this Trust's environment); no secondary use without separate written authorisation
2. **Data Categories:** Specifies exact data types vendor can access (vital signs, observations, labs, events; NOT patient name, address, or other identifiers beyond necessary)
3. **Processing Activities:** Describes what vendor does with data (model inference, monitoring, performance reporting; not training own commercial models)
4. **Sub-Processors:** Vendor lists all sub-processors (cloud infrastructure, analytics tools, support contractors); Trust approval required before adding new sub-processors
5. **Data Security:** Vendor implements encryption, access controls, audit logging, vulnerability management; meets ISO 27001 standard or equivalent
6. **Data Location:** Specifies where data stored (UK data centre preferred; if non-UK, requires Standard Contractual Clauses and cross-border transfer risk assessment)
7. **Retention and Deletion:** Vendor deletes patient data upon Trust instruction; demonstrates deletion is complete; retains audit trails for compliance
8. **Audit Rights:** Trust may audit vendor's compliance with DPA (annual audit or on-demand); vendor permits ICO inspection
9. **Breach Notification:** Vendor notifies Trust immediately (<24 hours) of suspected breach or unauthorised access; cooperates with incident response
10. **Assistance with Data Subject Rights:** Vendor assists Trust in responding to subject access requests, deletion requests, data portability requests within 10 days
11. **Termination:** Upon contract termination, vendor securely deletes all patient data or returns data to Trust; provides disposal certificate
12. **Liability:** Vendor liable for breaches of data protection obligations; no inappropriate liability caps that exclude coverage for GDPR or data protection breaches
13. **Governing Law:** DPA governed by UK law; disputes resolved in UK courts

**Model Portability Clause:**
- If vendor provides AI model, DPA must clarify Trust's ownership or right to export model (weights, hyperparameters, training data description)
- Enables Trust to switch to alternative vendor if needed without data lock-in

---

### 7.2 Technical and Organisational Security Measures

**Data Encryption:**
- **In Transit:** TLS 1.2+ for all data transfers (EPR → Model; Model → Alert System)
- **At Rest:** Patient data encrypted in cloud storage (AES-256 or equivalent)
- **Key Management:** Encryption keys managed by Trust or cloud provider (key rotation quarterly; backup keys stored securely)

**Access Controls:**
- **Role-Based Access Control (RBAC):** System restricts access to patient data based on staff role (clinicians see alerts for their patients; administrators see system metrics only)
- **Multi-Factor Authentication (MFA):** All staff accessing patient data required to use MFA (password + phone confirmation or security key)
- **Least Privilege:** Each role granted minimum data access necessary for job function
- **Logging & Auditing:** All access to patient data logged (user ID, timestamp, data accessed, action); audit logs retained for ≥1 year; suspicious activity (access outside normal hours, bulk data downloads) escalated to Information Security

**Data Quality and Validation:**
- **EPR Data Audit:** Regular audit of EPR data quality (completeness, accuracy, timeliness); issues escalated to Clinical Data Steward
- **Model Input Validation:** Model input data validated before inference (range checks, missing value handling, outlier detection)
- **Performance Monitoring:** Model predictions compared to actual outcomes; drift detection alerts if model performance degrades

**Incident Response and Breach Notification:**
- **Incident Response Plan:** Procedure for detecting, investigating, and responding to data breaches or security incidents
- **Breach Notification:** If patient data breached, notify affected patients and ICO within 72 hours (per GDPR Article 33)
- **Compensation:** Process for assessing patient harm from breach and providing compensation if required

**Vendor Security Assessment:**
- **Baseline:** Vendor provides evidence of security posture (ISO 27001 certification, SOC 2 report, or security audit)
- **Assessment:** Independent security review of vendor infrastructure and controls; report to Information Security team
- **Ongoing:** Annual reassessment; ad-hoc assessment if vendor notifies of security incident

---

### 7.3 Governance and Transparency Controls

**Data Protection Impact Assessment (This Document):**
- Documents processing activities, risks, and mitigations
- Risk assessment and residual risk statement
- Updated annually or if material changes to processing

**Privacy Impact Assessment (Additional):**
- Complements DPIA with patient and stakeholder perspective
- Engages patient representatives in privacy impact discussions
- Identifies accessibility and equity concerns

**Transparency and Accountability:**
- **Processing Register:** Document all processing activities (purpose, scope, retention, recipients)
- **Governance Decision Register:** Record major privacy-related decisions (vendor selection, data retention changes, incident outcomes)
- **Privacy Notice:** Updated to describe AI system; distributed to all patients on admission
- **Annual Privacy Review:** Review processing activities, incidents, changes; update DPIA and mitigations as needed

**Vendor Oversight:**
- **Vendor Relationship Management:** Designated Vendor Manager responsible for vendor compliance monitoring (SLA, DPA, performance)
- **Quarterly Vendor Reviews:** Assess vendor compliance with contractual obligations; escalate issues to procurement and legal
- **Annual Audit:** Independent audit of vendor security and data protection practices; report to Information Security and Privacy Officer

---

## 8. Residual Privacy Risk Statement

### 8.1 Risk Assessment Summary

| Risk Category | Residual Risk Level | Justification |
|---|---|---|
| **Unauthorised Vendor Access** | Medium | Mitigated by DPA, encryption, audit rights; remains medium because vendor access inherent to cloud-hosted model |
| **Data Breach (Cyber Attack)** | Low | Mitigated by encryption and vendor security controls; low likelihood of materialising |
| **Cross-Border Transfer (Non-UK)** | Medium (if non-UK provider selected) / Low (if UK provider selected) | Depends on cloud provider location; can be reduced by selecting UK data centre |
| **Secondary Use Without Consent** | Low | Mitigated by DPA restrictions; vendor contractually prohibited from secondary use |
| **Data Subject Rights Non-Compliance** | Low | Mitigated by DPA assistance clauses and Trust governance procedures |
| **Patient Privacy Not Informed** | Low | Mitigated by privacy notice update and distribution |
| **Data Retention Creep** | Low | Mitigated by automated deletion procedures and annual retention review |

**Overall Privacy Risk Assessment:** **ACCEPTABLE** for deployment conditional on recommended controls implemented

---

### 8.2 Conditions for Deployment

**Pre-Deployment Requirements (Gate 4 Approval):**

- [ ] Data Processing Addendum negotiated and signed with vendor/cloud provider
- [ ] Vendor security assessment completed; Information Security approves vendor
- [ ] Privacy notice updated and approved; patient information leaflet prepared
- [ ] Data deletion procedures documented and tested
- [ ] Audit logging enabled; access controls configured
- [ ] Data Subject Rights process documented (SAR, deletion, portability)
- [ ] Vendor liability provisions reviewed and approved by Legal
- [ ] Cross-border transfer agreement (Standard Contractual Clauses) in place if non-UK data centre used
- [ ] DPIA approved by Privacy Officer and Data Protection Committee

**Ongoing Monitoring:**

- Annual DPIA review or update if material changes to processing
- Quarterly vendor compliance review
- Incident detection and breach response procedures operational
- Annual privacy audit of processing activities

---

## 9. Compliance Pathways and Alternatives

### 9.1 Lawful Processing Options

**Option A (Recommended): Task in Public Interest**
- **Legal Basis:** GDPR Article 6(1)(e); DPA 2018 Schedule 1 Part 1
- **Advantages:** Does not require patient consent; patient privacy protected through governance (not individual consent); suitable for healthcare where patients may lack capacity
- **Disadvantages:** Requires public interest test; risk of challenge if scope creeps to non-healthcare use
- **Requirement:** Processing limited to healthcare management purpose; secondary use prohibited without separate basis

**Option B: Patient Consent**
- **Legal Basis:** GDPR Article 6(1)(a)
- **Advantages:** Gives patients choice and control
- **Disadvantages:** Creates dependency on consent; patients may withdraw consent, disrupting care; impractical for unconscious/incapacitated patients; consent forms complex
- **Recommendation:** Not primary basis, but can supplement task in public interest (offer patients ability to opt-out of secondary research use)

**Option C: Legitimate Interests**
- **Legal Basis:** GDPR Article 6(1)(f)
- **Advantages:** Allows processing for organisational benefit
- **Disadvantages:** Requires balancing test showing processing does not override patient privacy rights; less robust for healthcare than task in public interest
- **Recommendation:** Not recommended as primary basis; task in public interest more appropriate

**Chosen Approach:** Task in Public Interest (Option A) as primary basis; supplemented by consent for secondary uses (research, publication)

---

### 9.2 Data Minimisation Alternatives

**Option 1 (Implemented): Fully Identified Patient Data**
- Data includes patient identifiers (name, NHS number) required for alert delivery and clinical action
- Risk: Higher privacy risk (identifiable health data; if breached, privacy impact high)
- Benefit: Enables real-time alert delivery and clinical response

**Option 2: Pseudonymised Data**
- Data pseudonymised for model training/validation; re-identified for alert delivery only
- Risk: Modest reduction in privacy risk during development; re-identification needed operationally
- Benefit: Enables training on larger anonymised cohorts; reduces secondary use temptation
- Recommendation: Implement for model development phase; transition to identified data for operational deployment

**Option 3: Fully Anonymised Data**
- All patient identifiers removed; model trained on anonymised historical data only; not feasible for real-time alerting (alerts require patient identification for clinical action)
- Benefit: Eliminates privacy risk during development
- Limitation: Not feasible for operational deployment; requires separate identified data pipeline
- Recommendation: Use for model validation and fairness testing; not primary approach

**Chosen Approach:** Option 1 (fully identified) for deployment; pseudonymisation for model development/validation phase

---

## 10. Patient Engagement and Accountability

### 10.1 Patient Communication Strategy

**Privacy Notice (On-Admission):**
- Printed notice and digital notice in EPR describing AI system, data use, rights
- Plain language summary (7th-grade reading level)
- Multilingual versions (≥5 most common patient languages)
- Accessible formats (large print, audio)

**Patient Information Leaflet:**
- Simple 2-page explanation: "What is the deterioration prediction system? How is your data used? What rights do you have?"
- Includes contact for privacy queries
- Available in multiple formats and languages

**FAQ and Support:**
- Frequently Asked Questions addressing common privacy concerns
- Privacy Officer contact for questions/complaints
- ICO complaint procedure explained

**Patient Representative Engagement:**
- Patient Advisory Group consulted on privacy/transparency aspects
- Feedback from patient representatives incorporated before deployment
- Quarterly patient engagement on AI system effectiveness (if clinical audit conducted)

---

### 10.2 Data Protection Officer (DPO) and Privacy Oversight

**Privacy Officer Responsibilities:**
- Ensure DPIA completed and risks mitigated
- Approve Data Processing Addendum and vendor terms
- Oversee data subject rights compliance
- Monitor vendor compliance with DPA
- Lead privacy incident response and breach notification
- Provide privacy advice to clinical teams and governance
- Annual privacy audit and DPIA review

**Privacy Steering Committee:**
- Quarterly meetings of Privacy Officer, Clinical Safety Lead, Information Security, Clinical Informatics
- Reviews privacy risks, incidents, vendor compliance, compliance updates
- Approves significant privacy decisions

---

## 11. Compliance Checklist

**Pre-Deployment (Before Gate 4 Approval):**

| Item | Owner | Status | Target Date |
|---|---|---|---|
| DPIA completed and approved | Privacy Officer | This document (Draft) | 2026-10-31 |
| Legal basis documented (task in public interest) | Privacy Officer | Required | 2026-10-31 |
| Privacy notice updated | Privacy Officer | Required | 2026-10-31 |
| Patient information leaflet prepared | Communications | Required | 2026-10-31 |
| Data Processing Addendum negotiated | Vendor Manager | Required | 2026-11-30 |
| Vendor security assessment completed | Information Security | Required | 2026-11-30 |
| Data subject rights procedures documented | Privacy Officer | Required | 2026-11-30 |
| Data deletion procedures tested | IT Operations | Required | 2026-11-30 |
| Access controls and encryption configured | Information Security | Required | 2026-11-30 |
| Incident response procedures operational | Incident Response Lead | Required | 2026-11-30 |
| Cross-border transfer agreement (if applicable) | Legal / Privacy Officer | If required | 2026-12-31 |
| Privacy Officer approval for deployment | Privacy Officer | Required | 2026-12-31 |

**Ongoing (After Deployment):**

| Activity | Frequency | Owner | Status |
|---|---|---|---|
| Privacy incident monitoring | Continuous | Information Security | Operational |
| Vendor compliance review | Quarterly | Vendor Manager | Operational |
| Data subject rights requests | On-demand | Privacy Officer | Operational |
| Annual DPIA review | Annually | Privacy Officer | Scheduled 2027-09-11 |
| Annual privacy audit | Annually | Privacy Officer | Scheduled 2027-09-11 |

---

## 12. Risk Mitigation Summary

**Privacy Risks Eliminated by Design:**
- No personal data used for secondary purposes (commercial, research) without separate consent
- No data shared with parties outside NHS care without legal basis
- Patient privacy protected by confidentiality agreements and contractual restrictions

**Privacy Risks Reduced by Controls:**
- Data breach risk reduced by encryption and access controls
- Vendor misuse risk reduced by Data Processing Addendum and audit rights
- Patient privacy risk reduced by transparency and data subject rights procedures

**Residual Privacy Risks (Accepted by Organisation):**
- Vendor breach (inherent to cloud-hosted model; mitigated by security measures but cannot be eliminated)
- Cross-border transfer risk if non-UK cloud provider selected (can be eliminated by UK data centre choice)

---

## 13. DPIA Approval Decision

**Privacy Assessment:** Data processing is **LAWFUL and PROPORTIONATE** under UK GDPR and Data Protection Act 2018, conditional on recommended controls being implemented before deployment.

**Approval Authority:** Privacy Officer, Data Protection Committee

**Conditions for Approval:**
- [ ] Data Processing Addendum with vendor/cloud provider executed (if applicable)
- [ ] Privacy notice and patient information distributed
- [ ] Data subject rights procedures operational
- [ ] Data deletion and security controls tested
- [ ] Privacy Officer confirms all DPIA recommendations implemented

**Approval Status:** **CONDITIONAL APPROVAL** — System approved for pilot deployment (Gate 5) pending completion of privacy controls (Gate 4)

**Monitoring and Review:**
- Annual DPIA review; update if material changes to processing
- Quarterly vendor compliance review; escalate breaches to Privacy Officer
- Incident response for any data breaches; notification to ICO and patients if required

---

## 14. References and Related Documents

- UK GDPR (https://gdpr-info.eu/)
- Data Protection Act 2018 (c. 12) (https://www.legislation.gov.uk/ukpga/2018/12/contents)
- ICO Data Protection Impact Assessments (https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/data-protection-impact-assessments/)
- ISO/IEC 27001 Information Security Standard
- Use Case: AI-002-patient-deterioration.md
- Risk Assessment: AI-002-patient-deterioration-risk-assessment.md
- Governance Policy: AI-002-patient-deterioration-governance-policy.md
- Clinical Safety Assessment: AI-002-patient-deterioration-clinical-safety-assessment.md

---

**Prepared by:** Privacy Officer  
**Approved by:** [Data Protection Committee signature pending]  
**Status:** Ready for Privacy Officer and Data Protection Committee Review  
**Effective Date:** Upon approval and implementation of recommended controls

