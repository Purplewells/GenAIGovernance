---
title: AI-004 AI Recruitment Screening — Risk Assessment
date: 2026-09-11
lifecycle_stage: Use-Case Assessment
scope: AI system for screening applicant CVs and applications against job requirements, scoring candidates, and recommending for interview
decision_requested: Whether inherent risks are understood and whether proposed controls are adequate to reduce residual risk to acceptable tolerance
owner: Head of AI Governance
approval_authority: AI Governance Committee and Data Protection Officer
review_date: 2026-12-11
status: Draft for consultation
---

# AI-004 AI Recruitment Screening — Risk Assessment

## Executive Summary

This risk assessment evaluates the AI recruitment screening system using the NIST AI Risk Management Framework 1.0 (MAP and MEASURE functions). The system presents **HIGH inherent risk** due to:

1. **Discrimination and disparate impact** — Risk of systematically disadvantaging applicants based on protected characteristics (age, gender, ethnicity, disability)
2. **Data protection violations** — Processing and retention of applicant demographics without adequate consent or legal basis
3. **Fairness and transparency failures** — Lack of explainability and applicant challenge mechanisms
4. **Model bias and accuracy concerns** — Unknown model performance on underrepresented groups

**With effective controls**, residual risk can be reduced to **MEDIUM**, acceptable for pilot testing pending evidence from fairness validation and monitoring.

---

## Risk Assessment Methodology

**Framework:** NIST AI Risk Management Framework 1.0, MAP and MEASURE functions  
**Supporting References:**
- Equality Act 2010 (direct and indirect discrimination)
- UK GDPR and Data Protection Act 2018 (lawful processing, special categories)
- ICO AI and Data Protection Guidance (algorithmic fairness, transparency)
- OWASP AI Security and Fairness considerations

**Risk Evaluation:**
- **Inherent Risk** = Risk without controls, based on system design, training data, and operating environment
- **Residual Risk** = Risk after controls are implemented and operating effectively
- **Risk Tolerance** = Level of risk the organisation is willing to accept

**Scoring:**
- **Likelihood:** Rare (1) → Unlikely (2) → Possible (3) → Likely (4) → Very Likely (5)
- **Impact:** Negligible (1) → Minor (2) → Moderate (3) → Major (4) → Severe (5)
- **Risk = Likelihood × Impact:** 1–5 (Low), 6–12 (Medium), 13–25 (High)

---

## Risk Register

### INHERENT RISK 1: Disparate Impact by Age

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-001 |
| **Title** | Discrimination by Age — Disparate Impact on Older Applicants |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | The AI model systematically scores applicants differently based on inferred or stated age. Older applicants may be scored lower due to: (a) training data reflecting age bias in hiring, (b) proxy variables (e.g., graduation dates, employment gaps, career progression patterns) that correlate with age, (c) linguistic patterns in CVs that age proxies capture. This results in disparate impact: older applicants recommended for interview at lower rates than younger applicants, even when equally qualified. This violates the Equality Act 2010 (direct and indirect discrimination). |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Age bias is well-documented in AI systems and recruitment data; graduation dates and employment history are strong age proxies. |
| **Impact** | **Major (4)** — Loss of qualified candidates; legal liability under Equality Act 2010; reputational damage; applicant complaints and formal grievances; regulatory concern; compensation claims. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Training data reflects historical hiring bias; Age Concern research shows age discrimination is common in UK recruitment.
- *Unknown:* Actual training data composition (if vendor model) or internal training data representation.

**Root Causes:**
1. Age proxy variables (graduation date, employment history, career progression) used indirectly in scoring
2. Training data includes historical hiring decisions with age bias
3. No fairness testing across age cohorts before deployment
4. No monitoring for age disparities in operation

**Proposed Controls:**
- [ ] Fairness assessment: Test model on data stratified by age (e.g., 18–30, 31–45, 46–55, 56+); compare accuracy, false-positive, false-negative rates
- [ ] Model audit: Identify and document proxy variables; assess impact on different age groups
- [ ] Human oversight: HR review all recommendations; record override rate by age cohort
- [ ] Monitoring: Track interview recommendation rate and job offer rate by age; alert on disparate impact (e.g., <0.8 impact ratio)
- [ ] Transparency: Provide applicants with explanation of score or opportunity to request human review
- [ ] Escalation: If disparate impact detected, escalate to AI Governance and HR Director; consider model adjustment or retirement

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending fairness validation results

---

### INHERENT RISK 2: Disparate Impact by Gender

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-002 |
| **Title** | Discrimination by Gender — Disparate Impact on Women or Men |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | The AI model systematically scores applicants differently based on inferred or stated gender. Gender bias may arise from: (a) training data reflecting gendered hiring patterns (e.g., certain roles historically male- or female-dominated), (b) proxy variables (e.g., job titles, career breaks for childcare, linguistic differences), (c) role-specific biases (e.g., clinical roles vs. admin roles). Women in male-dominated fields or vice versa may be scored lower. This violates the Equality Act 2010. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Gender bias in hiring and AI systems is well-documented; proxy variables (career breaks, job titles, linguistic patterns) are common. |
| **Impact** | **Major (4)** — Loss of qualified candidates; legal liability under Equality Act 2010; reputational damage; applicant complaints; regulatory concern; compensation claims. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Training data reflects historical hiring bias; gender discrimination in UK recruitment is documented.
- *Unknown:* Actual training data composition; model's sensitivity to gender-associated linguistic patterns.

**Root Causes:**
1. Gender proxy variables (career breaks, job titles, linguistic patterns, industry sectors) used indirectly
2. Training data includes historical hiring decisions with gender bias
3. No fairness testing across gender cohorts before deployment
4. No monitoring for gender disparities in operation

**Proposed Controls:**
- [ ] Fairness assessment: Test model on data stratified by gender (male, female, non-binary); compare scores and recommendations
- [ ] Linguistic analysis: Audit CV text processing for gender-coded language (e.g., "ambitious" vs. "supportive")
- [ ] Proxy variable audit: Identify variables correlated with gender (career breaks, job titles, sectors); assess impact
- [ ] Human oversight: HR review all recommendations; record override rate by gender
- [ ] Monitoring: Track interview recommendation rate, job offer rate, and job performance by gender; alert on disparate impact
- [ ] Escalation: If disparate impact detected, escalate to AI Governance and HR Director

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending fairness validation

---

### INHERENT RISK 3: Disparate Impact by Ethnicity

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-003 |
| **Title** | Discrimination by Ethnicity/Race — Disparate Impact on Ethnic Minorities |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | The AI model systematically scores applicants differently based on inferred or stated ethnicity. Ethnic bias may arise from: (a) training data reflecting ethnic hiring patterns or stereotypes, (b) proxy variables (e.g., name analysis, educational institution prestige varying by ethnicity, employment patterns), (c) linguistic patterns in CVs. Applicants from ethnic minorities may be scored lower. This violates the Equality Act 2010 and UK race discrimination law. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Ethnic bias in hiring is documented; resume screening by name is known to bias against ethnic minorities; training data likely includes ethnic hiring patterns. |
| **Impact** | **Major (4)** — Loss of qualified candidates; legal liability under Equality Act 2010; reputational damage; applicant complaints; regulatory concern; compensation claims. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Training data reflects ethnic hiring bias; name-based ethnic discrimination in recruitment is well-documented.
- *Unknown:* Actual training data; whether applicant names are processed; proxy variables correlated with ethnicity.

**Root Causes:**
1. Name-based ethnicity inference or explicit ethnicity data in training
2. Educational institution prestige and employment patterns correlated with ethnicity
3. Training data includes historical hiring patterns with ethnic bias
4. No fairness testing across ethnic cohorts before deployment

**Proposed Controls:**
- [ ] Data minimisation: Exclude or mask applicant names and ethnicity data from scoring model
- [ ] Fairness assessment: Test model on synthetic data stratified by ethnicity and names; identify ethnic-correlated proxy variables
- [ ] Audit proxy variables: Educational institutions, employment sectors, linguistic patterns correlated with ethnicity
- [ ] Human oversight: HR review all recommendations; record override rate by ethnicity (if known)
- [ ] Monitoring: If ethnicity data available (e.g., voluntary equal opportunities form), track recommendation rate by ethnic group; alert on disparate impact
- [ ] Escalation: If disparate impact detected, escalate to AI Governance, HR Director, and Data Protection Officer

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending fairness validation and data minimisation

---

### INHERENT RISK 4: Disability Discrimination

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-004 |
| **Title** | Discrimination by Disability Status — Disparate Impact on Disabled Applicants |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | The AI model systematically scores applicants with disabilities lower. Bias may arise from: (a) employment gaps or career interruptions documented in CV (often related to disability-related treatment or support needs), (b) proxy variables (e.g., shorter employment history, certain medical certifications), (c) training data reflecting historical disability discrimination in hiring. Disabled applicants may be scored lower even when equally qualified. This violates the Equality Act 2010 (disability discrimination) and UK employment law. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Disability discrimination in hiring is documented; employment gaps correlate with disability; training data likely includes disability bias. |
| **Impact** | **Major (4)** — Loss of qualified candidates; legal liability under Equality Act 2010; reputational damage; applicant complaints; regulatory concern; compensation claims. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Training data reflects historical disability discrimination; employment gaps correlated with disability disclosure.
- *Unknown:* Whether applicants disclose disability; correlation between disability and employment history in training data.

**Root Causes:**
1. Proxy variables (employment gaps, shorter employment history, specific certifications) correlate with disability
2. Training data includes historical disability discrimination in hiring decisions
3. No fairness testing across disability status before deployment
4. Possible direct processing of disability information if applicant discloses (special category data)

**Proposed Controls:**
- [ ] Data minimisation: Avoid collecting or processing disability information unless relevant and consented
- [ ] Proxy variable audit: Identify employment-gap patterns and other proxies correlating with disability; assess impact
- [ ] Fairness assessment: Test model on data with simulated employment gaps; compare scores
- [ ] Human oversight: HR review all recommendations; don't auto-reject on employment gaps; encourage interview for qualified candidates
- [ ] Monitoring: Track interview recommendation rate for applicants with employment gaps; monitor for disability discrimination complaints
- [ ] Reasonable adjustments: Ensure disabled applicants can request human review or explanation of score; adjust recruitment process if needed
- [ ] Escalation: If disability-related complaints received, escalate to AI Governance, HR, and Data Protection Officer

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending fairness validation and disability representation testing

---

### INHERENT RISK 5: Other Protected Characteristics (Sexual Orientation, Gender Reassignment, Religion, Pregnancy)

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-005 |
| **Title** | Discrimination by Sexual Orientation, Gender Reassignment, Religion, Pregnancy/Maternity |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | The AI model may systematically discriminate against applicants based on sexual orientation, gender reassignment, religion/belief, pregnancy, or maternity status. These characteristics may be inferred from CV information (e.g., pronoun use, religious affiliations, gaps in employment for pregnancy/maternity) or disclosed in optional equal opportunities forms. Proxy variables or training data biases may result in lower scores. This violates the Equality Act 2010. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Unlikely (2)** — Less commonly inferred from CV data; more likely if applicant voluntarily discloses. However, pregnancy/maternity gaps are detectable. |
| **Impact** | **Major (4)** — Legal liability under Equality Act 2010; reputational damage; applicant complaints; regulatory concern. |
| **Inherent Risk** | **MEDIUM-HIGH (8)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **MEDIUM** — Requires controls |

**Evidence:**
- *Assumption:* Applicants may disclose sexual orientation, religion, or gender reassignment in optional equal opportunities sections; pregnancy/maternity gaps may be inferred.
- *Unknown:* Whether applicants voluntarily provide this information; proxy variables correlated with these characteristics.

**Root Causes:**
1. Proxy variables (employment gaps, pronoun use, organisational affiliations) may correlate with these characteristics
2. If applicants disclose in equal opportunities forms, data may be linked to scoring model
3. Training data may include historical discrimination patterns

**Proposed Controls:**
- [ ] Data separation: Keep equal opportunities data separate from applicant scoring model; ensure fair scoring based on qualifications only
- [ ] Proxy variable audit: Test for proxy variables correlated with pregnancy, maternity, religion, sexual orientation, gender reassignment
- [ ] Fairness assessment: Test model on data with simulated maternity gaps; compare scores
- [ ] Human oversight: HR review all recommendations; no auto-rejection for employment gaps unrelated to job requirements
- [ ] Monitoring: Track interview recommendation rate for applicants with maternity/pregnancy-related gaps
- [ ] Escalation: If discrimination complaints received, escalate to AI Governance, HR, and Data Protection Officer

**Residual Risk (With Controls):** LOW-MEDIUM (4–8) — Acceptable for pilot testing

---

### INHERENT RISK 6: Proxy Variable Discrimination (Indirect Discrimination)

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-006 |
| **Title** | Indirect Discrimination Through Proxy Variables |
| **Category** | Fairness & Discrimination; Legal/Compliance |
| **Description** | Even if the model explicitly excludes protected characteristics, it may use proxy variables that are highly correlated with protected characteristics, resulting in indirect discrimination. Examples: (a) Educational institution prestige (correlates with ethnicity and socioeconomic status), (b) Employment gaps (correlate with age, gender/maternity, disability, caregiving responsibilities), (c) Career progression rate (correlates with age, gender, motherhood penalties), (d) Geographic location (correlates with ethnicity and socioeconomic status). Using these proxies may have a disproportionate adverse effect on protected groups without being justified by business necessity. This violates the Equality Act 2010 (indirect discrimination). |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Very Likely (5)** — Proxy variables are almost always present in recruitment data; ensuring they don't cause disparate impact is technically difficult. |
| **Impact** | **Major (4)** — Systematic indirect discrimination; legal liability; regulatory concern; loss of qualified candidates; reputational damage. |
| **Inherent Risk** | **HIGH (20)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Proxy variables are present in CV data; many correlate with protected characteristics.
- *Unknown:* Strength of correlation; model's use of proxy variables; impact on different groups.

**Root Causes:**
1. Proxy variables are available and predictive of job suitability (or apparent suitability based on training data)
2. Model cannot distinguish between legitimate business use and discriminatory proxy use
3. No audit of proxy variable impact by protected characteristic
4. No evidence that proxy variables are justified by business necessity

**Proposed Controls:**
- [ ] Proxy variable audit: Identify all proxy variables in model; test correlation with protected characteristics
- [ ] Disparate impact assessment: Calculate impact ratio for each proxy variable by protected characteristic; flag if <0.8 (indicating potential indirect discrimination)
- [ ] Business justification: Document why each proxy variable is necessary for job suitability; assess whether less discriminatory alternatives exist
- [ ] Fairness testing: Test model performance on data stratified by protected characteristics; identify disparities caused by proxies
- [ ] Model adjustment: Reduce or remove proxy variables with high disparate impact; retrain if necessary
- [ ] Monitoring: Continuously monitor for disparate impact by protected characteristic; escalate if detected
- [ ] Escalation: If disparate impact detected, escalate to AI Governance, Legal, and HR Director for business case review

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending thorough proxy variable audit and fairness testing

---

### INHERENT RISK 7: Lack of Transparency & Explainability

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-007 |
| **Title** | Black Box Scoring — Lack of Transparency and Explainability |
| **Category** | Fairness & Transparency; Accountability |
| **Description** | The AI scoring model may be a "black box" where the basis for scoring individual applicants is opaque. HR staff and applicants cannot understand why a candidate scored low or high. This prevents: (a) HR from effectively reviewing and overriding inappropriate AI recommendations, (b) applicants from challenging unfair decisions, (c) discovery of discriminatory patterns or biases in scoring. This violates principles of fairness, transparency, and accountability in algorithmic decision-making (ICO guidance, GDPR Article 22). |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Many ML models (e.g., deep neural networks, random forests) are difficult to interpret without additional techniques. |
| **Impact** | **Major (4)** — Inability to identify and remedy discrimination; loss of applicant trust; regulatory concern; legal liability; difficulty in HR oversight. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Model type likely to have limited interpretability (if deep learning or complex ensemble).
- *Unknown:* Actual model architecture and explainability techniques planned.

**Root Causes:**
1. Complex model architecture (neural networks, random forests) with limited interpretability
2. No explainability techniques (feature importance, SHAP values, LIME, attention mechanisms) implemented
3. No requirement for transparency in vendor model (if vendor-supplied)
4. No applicant communication about AI scoring logic

**Proposed Controls:**
- [ ] Model interpretability: Require model with built-in explainability (e.g., decision trees, linear models) OR implement explainability techniques (SHAP, LIME, feature importance) for complex models
- [ ] Scoring rationale: Generate summary of top factors contributing to score for each applicant (e.g., "matched skills, experience, and location; weak on qualification requirement X")
- [ ] HR interface: Provide HR staff with explainability information for each recommendation; train on how to interpret and challenge scores
- [ ] Applicant transparency: Inform applicants that AI was used in screening; provide explanation if applicant requests (right to explanation under GDPR Article 22)
- [ ] Documentation: Document model logic, feature importance, decision thresholds; maintain audit trail of scoring
- [ ] Vendor transparency: If vendor-supplied model, require vendor to provide explainability documentation or agree to audit rights
- [ ] Regular audit: Periodic independent audit of scoring logic and fairness implications

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing if explainability techniques proven effective

---

### INHERENT RISK 8: Data Protection Violations (GDPR & Data Protection Act 2018)

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-008 |
| **Title** | Unlawful Processing of Applicant Data, Including Special Categories |
| **Category** | Data Protection & Privacy; Legal/Compliance |
| **Description** | The system processes personal data (name, contact, employment history, demographics) and potentially special category data (ethnicity, disability, sexual orientation, religion, pregnancy). Risks include: (a) No valid legal basis for processing (e.g., consent not obtained or withdrawn), (b) Processing special category data without explicit lawful basis (GDPR Articles 9, 10), (c) Excessive data retention (holding applicant data longer than necessary), (d) Unauthorised sharing with vendors or subprocessors, (e) Applicant rights violations (access, rectification, erasure, portability not honoured), (f) No Data Protection Impact Assessment, (g) Insufficient security or risk of data breach. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Common in new recruitment systems; consent and lawful basis often overlooked; DPIA frequently incomplete. |
| **Impact** | **Major (4)** — Regulatory enforcement by ICO, fines up to 4% revenue or €20M (GDPR), legal liability to applicants, reputational damage, breach of trust. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | LOW-MEDIUM (2–6) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Applicant demographics collected for equal opportunities or AI scoring; data retention practices unclear.
- *Unknown:* Current lawful basis, consent practices, vendor data processing, data retention timeline.

**Root Causes:**
1. No formalised consent process for AI screening and data processing
2. No clear lawful basis documented (contract, consent, employment law, etc.)
3. No Data Protection Impact Assessment completed
4. Unclear data retention and deletion procedures
5. Potential sharing with vendors or cloud providers without documented data processing agreements
6. Special category data (demographics) processed without explicit consent

**Proposed Controls:**
- [ ] Lawful basis: Document valid lawful basis for processing applicant data (e.g., contract for recruitment, consent, employment law)
- [ ] Consent: Obtain explicit informed consent for AI screening and use of personal data; allow applicants to opt out or request human review
- [ ] DPIA: Complete Data Protection Impact Assessment; identify high-risk processing and mitigations
- [ ] Data minimisation: Collect only data necessary for recruitment; avoid collecting demographics for scoring model
- [ ] Data separation: Separate optional equal opportunities data from scoring model; handle separately with appropriate protections
- [ ] Vendor agreements: If using vendor or cloud provider, execute Data Processing Agreements (DPA) confirming data will not be used for vendor training or analytics
- [ ] Data retention: Define retention schedule (e.g., successful hires: 2 years; unsuccessful applicants: 6 months); implement automated deletion
- [ ] Applicant rights: Document procedures for subject access requests, data rectification, erasure, portability; respond within 30 days
- [ ] Security: Ensure appropriate technical and organisational security measures (encryption, access controls, audit logs)
- [ ] Subprocessor audit: Identify all subprocessors (cloud providers, third-party tools); ensure Applicant is contractually bound

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing if DPIA approved and controls implemented

---

### INHERENT RISK 9: Human Oversight Failure (Over-Reliance on AI)

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-009 |
| **Title** | Over-Reliance on AI Recommendations; Reduced Human Judgment |
| **Category** | Human Oversight; Governance; Safety |
| **Description** | HR staff may over-rely on AI recommendations and under-utilise human judgment. Risks include: (a) Auto-acceptance of AI recommendations without meaningful review, (b) HR staff lacking training on AI limitations and bias, (c) Threshold set so high that auto-rejection occurs for below-threshold candidates without HR review, (d) No documentation of human review or override decisions, (e) HR incentivised to accept AI recommendations to reduce workload, (f) Loss of opportunity to catch and correct AI errors or bias. This reduces fairness, increases harm to applicants, and undermines accountability. |
| **Lifecycle Stage** | Operation (if deployed) |
| **Likelihood** | **Likely (4)** — HR departments often lack AI literacy; volume-based work incentives can favour accepting AI recommendations. |
| **Impact** | **Moderate (3)** — Qualified applicants unfairly rejected; discrimination not detected; loss of diverse candidates; eroded HR oversight. |
| **Inherent Risk** | **MEDIUM-HIGH (12)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **MEDIUM-HIGH** — Requires controls |

**Evidence:**
- *Assumption:* HR staff may lack AI training; workload incentives may favour accepting AI recommendations.
- *Unknown:* Current HR practices and AI training levels.

**Root Causes:**
1. No formalised HR procedure requiring review and override capability
2. HR staff lack training on AI limitations, bias, and fairness
3. System design allows auto-rejection below threshold without HR review
4. Workload or performance metrics incentivise accepting AI recommendations
5. No oversight mechanism to track human review rates or challenge override rates

**Proposed Controls:**
- [ ] Procedural design: Require HR review of ALL AI recommendations (no auto-rejection); document review and decision
- [ ] HR training: Provide training on AI limitations, bias, fairness, discrimination, and how to effectively challenge AI recommendations
- [ ] Override tracking: Track override rate (how often HR disagrees with AI); analyse patterns by protected characteristic
- [ ] Threshold design: Set threshold conservatively so meaningful proportion of candidates reviewed by HR; avoid auto-rejection
- [ ] Escalation: If override rate by HR differs significantly by protected characteristic (e.g., HR overrides AI recommendations for women at higher rate), escalate to AI Governance for investigation
- [ ] Periodic review: Audit AI-HR agreement rate; assess whether HR is exercising independent judgment
- [ ] Applicant communication: Inform applicants that HR makes final decision; offer opportunity to request human review

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing with robust HR procedures and training

---

### INHERENT RISK 10: Model Accuracy Concerns for Underrepresented Groups

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-010 |
| **Title** | Poor Model Performance on Underrepresented Groups; High False-Negative Rates |
| **Category** | Model Accuracy & Fairness |
| **Description** | The AI model may perform poorly on underrepresented groups in training data (e.g., older applicants, ethnic minorities, disabled applicants, women in male-dominated fields). Risks include: (a) Higher false-negative rate for underrepresented groups (qualified applicants incorrectly scored low and rejected), (b) Higher false-positive rate (unqualified applicants incorrectly scored high and recommended), (c) Inability to identify these disparities without demographic data and testing, (d) Loss of qualified candidates from underrepresented groups, (e) Perpetuation or amplification of hiring biases in training data. |
| **Lifecycle Stage** | Design (pre-pilot); Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Well-documented phenomenon in ML: models perform worse on underrepresented groups. If training data is imbalanced, bias is likely. |
| **Impact** | **Major (4)** — Loss of qualified candidates; reduced diversity; discrimination; eroded talent acquisition. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Training data likely underrepresents older applicants, ethnic minorities, disabled applicants, women in certain fields.
- *Unknown:* Actual training data composition; model performance by demographic group.

**Root Causes:**
1. Training data underrepresents certain demographic groups
2. Model optimised for overall accuracy, not fairness across groups
3. No fairness testing by demographic cohort
4. No baseline for expected fairness performance

**Proposed Controls:**
- [ ] Training data audit: Obtain composition of training data by demographic group (age, gender, ethnicity, disability); identify underrepresented groups
- [ ] Fairness testing: Test model performance (accuracy, precision, recall, false-positive, false-negative rates) for each demographic cohort
- [ ] Parity testing: Compare performance across groups; flag disparities (e.g., false-negative rate 15% for women vs. 8% for men)
- [ ] Model adjustment: If significant performance gaps, consider rebalancing training data, adjusting model parameters for fairness, or using fairness-aware ML techniques
- [ ] Performance monitoring: In operation, track hiring outcomes by demographic group; monitor false-positive and false-negative rates
- [ ] Escalation: If significant performance disparities detected, escalate to Data Science and AI Governance; consider model adjustment or restriction

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing pending fairness testing results

---

### INHERENT RISK 11: Vendor Lock-In & Limited Audit Rights

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-011 |
| **Title** | Vendor Dependency; Limited Audit Rights; Difficulty Exiting |
| **Category** | Vendor Management; Business Continuity |
| **Description** | If using a vendor-supplied AI recruitment model, risks include: (a) Inability to audit model internals or understand how it scores applicants, (b) Vendor unwilling to provide fairness testing results or transparency, (c) Vendor may use Trust's applicant data to improve its model or train on it for other customers, (d) Limited contractual liability if model discriminates, (e) High switching costs; difficult to migrate away from vendor platform, (f) Vendor updates model without Trust oversight; changes may introduce new biases, (g) Vendor goes out of business; platform discontinued with no migration path. |
| **Lifecycle Stage** | Acquisition (if vendor model); Operation (if deployed) |
| **Likelihood** | **Possible (3)** — Depends on vendor choice and contract negotiation; some vendors provide audit rights, others do not. |
| **Impact** | **Moderate-Major (3–4)** — Loss of control over AI system; inability to detect or remedy discrimination; dependency on vendor; potential data loss or system failure. |
| **Inherent Risk** | **MEDIUM-HIGH (9–12)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **MEDIUM** — Requires vendor assessment and strong contract terms |

**Evidence:**
- *Assumption:* If vendor model selected, vendor terms often favour vendor over customer; audit rights often limited.
- *Unknown:* Which vendor (if any) will be used; current contract terms.

**Root Causes:**
1. Vendor business model depends on proprietary model; limited transparency
2. Weak contract negotiation or insufficient legal review
3. No audit rights or fairness transparency requirements in contract
4. Data processing agreements may allow vendor to use applicant data

**Proposed Controls:**
- [ ] Vendor selection: If using vendor model, require vendor to provide fairness testing results, training data composition, and audit rights
- [ ] Contract terms: Negotiate strong contract terms including: (a) Audit rights and model transparency, (b) Liability for discriminatory outcomes, (c) Commitment to fairness testing and remediation, (d) Data usage restrictions (no use of Trust applicant data for vendor training or analytics), (e) Exit provisions (data export, model transfer, support for migration)
- [ ] DPA: Ensure Data Processing Agreement confirms data will not be used for vendor purposes
- [ ] Periodic audit: Conduct periodic independent audit of vendor model; verify fairness claims
- [ ] Contingency plan: Develop exit strategy; identify alternative platforms or internal development option
- [ ] Escalation: If vendor unable to provide fairness evidence or audit rights, escalate to Procurement and AI Governance; consider alternative vendor or internal development

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing with vendor assessment and strong contract terms

---

### INHERENT RISK 12: Inadequate Monitoring & Bias Detection

| Attribute | Assessment |
|---|---|
| **Risk ID** | REC-AI-012 |
| **Title** | Insufficient Monitoring for Bias and Disparate Impact in Operation |
| **Category** | Monitoring & Assurance |
| **Description** | Post-deployment, the system may exhibit biases or discriminatory patterns that are not detected. Risks include: (a) No monitoring for disparate impact by protected characteristic, (b) Monitoring conducted infrequently or manually, (c) Monitoring data incomplete (e.g., demographic information not captured for all applicants), (d) Alerts or escalation procedures not defined, (e) No independent audit of fairness in operation, (f) Discrimination complaints not systematically tracked or escalated. This allows biases to persist undetected, perpetuating discrimination and liability exposure. |
| **Lifecycle Stage** | Operation (if deployed) |
| **Likelihood** | **Likely (4)** — Many organisations lack maturity in bias monitoring; requires sustained commitment and resources. |
| **Impact** | **Major (4)** — Persistent discrimination; regulatory enforcement; legal liability; reputational damage. |
| **Inherent Risk** | **HIGH (16)** |
| **Risk Tolerance** | MEDIUM (6–12) |
| **Residual Risk without controls** | **HIGH** — Unacceptable |

**Evidence:**
- *Assumption:* Monitoring infrastructure and procedures not yet established for recruitment AI.
- *Unknown:* Current monitoring and escalation procedures.

**Root Causes:**
1. No monitoring plan defined
2. Insufficient data collection (demographic data not linked to outcomes)
3. No automated monitoring or alerting
4. No clear escalation pathway for bias detection
5. No independent audit planned
6. Discrimination complaints not systematically tracked

**Proposed Controls:**
- [ ] Monitoring plan: Define fairness metrics (recommendation rate, interview conversion rate, hiring rate, job performance by demographic group); set alert thresholds (e.g., <0.8 impact ratio)
- [ ] Data collection: Ensure demographic data captured for all applicants (e.g., via optional equal opportunities form or voluntary disclosure)
- [ ] Monitoring dashboard: Build automated dashboard tracking fairness metrics; update weekly or monthly
- [ ] Alerting: Configure alerts if metric falls below threshold; escalate to AI Governance
- [ ] Audit: Conduct independent fairness audit quarterly; compare outcomes by demographic group with statistical testing
- [ ] Complaint tracking: Systematically track discrimination complaints or fairness concerns; analyse patterns; escalate
- [ ] Escalation procedure: Define escalation pathway for bias detection: Data Science → AI Governance Lead → HR Director → Audit Committee
- [ ] Remediation: If bias detected, plan model adjustment, retraining, restriction, or retirement

**Residual Risk (With Controls):** MEDIUM (6–12) — Acceptable for pilot testing with robust monitoring plan

---

## Summary Risk Matrix

| Risk ID | Risk Title | Inherent | Residual (with controls) | Likelihood | Impact | Status |
|---|---|---|---|---|---|---|
| REC-AI-001 | Age discrimination | HIGH | MEDIUM | Likely (4) | Major (4) | Requires fairness testing |
| REC-AI-002 | Gender discrimination | HIGH | MEDIUM | Likely (4) | Major (4) | Requires fairness testing |
| REC-AI-003 | Ethnic discrimination | HIGH | MEDIUM | Likely (4) | Major (4) | Requires data minimisation |
| REC-AI-004 | Disability discrimination | HIGH | MEDIUM | Likely (4) | Major (4) | Requires proxy analysis |
| REC-AI-005 | Other protected characteristics | MEDIUM-HIGH | LOW-MEDIUM | Unlikely (2) | Major (4) | Requires data separation |
| REC-AI-006 | Proxy variable discrimination | HIGH | MEDIUM | Very Likely (5) | Major (4) | **HIGHEST PRIORITY** |
| REC-AI-007 | Black box scoring | HIGH | MEDIUM | Likely (4) | Major (4) | Requires explainability |
| REC-AI-008 | GDPR violations | HIGH | MEDIUM | Likely (4) | Major (4) | Requires DPIA & consent |
| REC-AI-009 | Human oversight failure | MEDIUM-HIGH | MEDIUM | Likely (4) | Moderate (3) | Requires HR procedures |
| REC-AI-010 | Poor performance on minorities | HIGH | MEDIUM | Likely (4) | Major (4) | Requires fairness testing |
| REC-AI-011 | Vendor lock-in | MEDIUM-HIGH | MEDIUM | Possible (3) | Moderate-Major (3–4) | Requires vendor assessment |
| REC-AI-012 | Inadequate monitoring | HIGH | MEDIUM | Likely (4) | Major (4) | Requires monitoring plan |

---

## Prioritised Risk Mitigation

### Immediate Priorities (Pre-Pilot Testing)

1. **REC-AI-006: Proxy Variable Discrimination** — Complete audit of all proxy variables; test for disparate impact; document business justification or remove proxies
2. **REC-AI-007: Black Box Scoring** — Ensure model has built-in explainability or implement explainability techniques; verify HR can interpret scores
3. **REC-AI-008: GDPR Violations** — Complete DPIA; document lawful basis; obtain consent; establish data retention and deletion procedures
4. **REC-AI-001/002/003/004/010: Fairness Testing** — Test model performance by age, gender, ethnicity, disability; identify false-negative rates; plan model adjustment if disparities found

### Pilot Testing Priorities

1. **Implement all controls** outlined for each risk
2. **Monitor fairness metrics** throughout pilot; escalate if disparate impact detected
3. **Track HR override rates** by demographic group; ensure human oversight effective
4. **Analyse pilot outcomes** for evidence of discrimination before rollout

### Post-Pilot Priorities (Before Production Rollout)

1. **Independent fairness audit** of pilot results
2. **Legal review** confirming Equality Act 2010 compliance
3. **Board approval** of residual risk and accountability
4. **Establish ongoing monitoring** and escalation procedures
5. **Vendor audit** (if vendor model) confirming fairness commitments

---

## Governance & Accountability

**Risk Owner:** Head of AI Governance  
**Mitigation Owner:** Data Science Lead (model fairness); HR Manager (procedures); Data Protection Officer (privacy compliance)  
**Approval Authority:** AI Governance Committee; Data Protection Officer; HR Director  
**Escalation Route:** Bias detection → Data Science → AI Governance Lead → HR Director → Audit Committee  
**Review Cadence:** Monthly (pilot); Quarterly (operation)

---

## Appendices

- **Appendix A:** Proxy Variable Audit Template
- **Appendix B:** Fairness Testing Protocol
- **Appendix C:** Disparate Impact Calculation Method
- **Appendix D:** HR Training Curriculum on AI Bias

---

## Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | AI Governance | Draft for consultation |

---

**Document Classification:** Internal Use Only — AI Governance  
**Retention Period:** 7 years  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11
