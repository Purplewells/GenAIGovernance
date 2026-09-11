---
title: AI-004 AI Recruitment Screening — Control Matrix
date: 2026-09-11
lifecycle_stage: Design & Testing
scope: Actionable controls to mitigate discrimination and fairness risks in AI recruitment screening
decision_requested: Whether proposed controls are adequate, feasible, and assigned to clear owners with measurable success criteria
owner: Head of AI Governance
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Draft for consultation
---

# AI-004 AI Recruitment Screening — Control Matrix

## Overview

This document defines specific, actionable controls to mitigate the fairness and discrimination risks identified in the Risk Assessment (REC-AI-001 through REC-AI-012). Each control specifies:

- **Objective:** What risk it mitigates
- **Control Activity:** Specific action or procedure
- **Owner:** Named responsible party
- **Trigger:** When the control is activated
- **Procedure:** Step-by-step implementation
- **Evidence:** How effectiveness is demonstrated
- **Test Method:** How control is tested or verified
- **Success Criteria:** Measurable threshold for control effectiveness
- **Residual Risk:** Risk level if control effective
- **Status:** Design / Ready for Test / Operating / Suspended

---

## CONTROL 1: Fairness Baseline Assessment (Pre-Pilot)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-001 |
| **Risk Mitigated** | REC-AI-001, REC-AI-002, REC-AI-003, REC-AI-004, REC-AI-006, REC-AI-010 (discrimination and proxy bias) |
| **Objective** | Establish baseline understanding of model performance and bias before any applicant data is processed; identify discrimination risks in design |
| **Control Activity** | Independent fairness assessment of recruitment model (if vendor-supplied) or planned model architecture (if internal development). Test includes: (a) Training data audit (demographic composition, representation of protected groups), (b) Model performance testing across demographic cohorts (age, gender, ethnicity, disability), (c) Proxy variable identification and correlation analysis, (d) Disparate impact calculation, (e) Explainability assessment |
| **Owner** | Data Science Lead (in consultation with AI Governance, HR, and independent fairness auditor) |
| **Trigger** | Before pilot testing begins; before any applicant data processed |
| **Procedure** | **Step 1:** If vendor model: request training data composition and fairness testing results from vendor; conduct independent verification. **Step 2:** If internal model: audit training data composition by demographic group. **Step 3:** Test model performance (accuracy, precision, recall, F1 score) for each demographic cohort (age 18–30, 31–45, 46–55, 56+; gender M/F/non-binary; ethnicity categories as appropriate; disability status if available). **Step 4:** Calculate false-positive and false-negative rates by cohort. **Step 5:** Identify all proxy variables used by model; assess correlation with protected characteristics. **Step 6:** Calculate disparate impact ratios (recommendation rate for group / recommendation rate for comparison group); flag if <0.8. **Step 7:** Test explainability of model; verify HR can interpret scores. **Step 8:** Document all findings; flag high-risk biases requiring model adjustment. |
| **Evidence** | Fairness Assessment Report including: (a) Training data composition table, (b) Model performance by demographic cohort (accuracy, precision, recall, false-positive, false-negative rates), (c) Proxy variable audit with correlation coefficients, (d) Disparate impact ratios by group, (e) Explainability test results, (f) Recommendations for model adjustment or risk acceptance, (g) Sign-off by Data Science Lead and independent auditor |
| **Test Method** | **Design adequacy:** Fairness report reviewed for completeness and rigor by AI Governance Committee and independent auditor. **Implementation:** Fairness assessment conducted by independent third party (not model vendor or developer) with expertise in fairness, discrimination, and recruitment. **Operating effectiveness:** Report demonstrates model performance across demographic cohorts; disparate impact ratios calculated with 95% confidence intervals; recommendations are specific and testable. |
| **Success Criteria** | 1. **No statistically significant disparate impact identified** (impact ratio ≥0.8 for all protected groups at p<0.05). 2. **False-negative rates within acceptable range** across demographic cohorts (e.g., <15% difference between highest and lowest rate). 3. **Proxy variables identified and justified** (e.g., educational institution used only if directly relevant to job requirements). 4. **Explainability demonstrated** (HR can interpret top 3 factors contributing to score for sample applicants). 5. **Report signed off by independent auditor** confirming assessment rigor. **If criteria not met:** Model requires adjustment before pilot testing; escalate to AI Governance and Data Science Lead for remediation plan. |
| **Residual Risk** | REC-AI-001/002/003/004/006/010: MEDIUM (mitigated from HIGH) — Control provides early warning of discrimination risks; allows model adjustment before live use. Residual risk remains MEDIUM pending ongoing monitoring in operation. |
| **Status** | ⏳ DESIGN — Awaiting fairness assessment methodology approval |
| **Timeline** | Start: Upon governance approval; Complete: Before pilot data collection begins (target: 2 weeks) |
| **Dependencies** | Model design finalised; training data available (if vendor, obtained from vendor; if internal, data accessible) |
| **Owner Sign-Off** | *[Data Science Lead]* |
| **Approval Sign-Off** | *[AI Governance Lead]* |

---

## CONTROL 2: Data Minimisation & Separation

| Attribute | Detail |
|---|---|
| **Control ID** | CON-002 |
| **Risk Mitigated** | REC-AI-003 (ethnicity discrimination via name analysis), REC-AI-004 (disability discrimination), REC-AI-005 (sexual orientation, religion, pregnancy), REC-AI-008 (GDPR lawfulness) |
| **Objective** | Minimise sensitive personal data processed by scoring model; separate optional equal opportunities data from scoring; ensure lawful processing of special categories |
| **Control Activity** | Design AI scoring model to use only job-relevant data (qualifications, experience, skills); exclude or mask: applicant name (no name-based ethnicity inference), ethnicity/race, disability status, sexual orientation, religion/belief, pregnancy/maternity information, age (if age can be inferred from education dates, implement age-agnostic scoring). Maintain optional equal opportunities data in separate system; use only for monitoring and reporting (not for scoring). |
| **Owner** | Data Science Lead (model design); Data Protection Officer (lawfulness review) |
| **Trigger** | Model design phase; before development begins |
| **Procedure** | **Step 1:** List all data fields available in applicant CV/application. **Step 2:** Classify each field as: job-relevant (necessary for scoring) or sensitive (not necessary; risks discrimination or privacy harm). **Step 3:** For job-relevant fields, assess whether they indirectly reveal protected characteristics (proxy analysis). **Step 4:** Remove or mask sensitive fields from scoring model. **Step 5:** For job-relevant fields with proxy risk (e.g., graduation date revealing age), apply age-agnostic scoring (e.g., years of experience rather than graduation year). **Step 6:** If equal opportunities data collected, store separately in access-controlled system; link to applicant ID only when needed for monitoring, not scoring. **Step 7:** Document data minimisation rationale; review with DPO and Legal. |
| **Evidence** | (a) Data classification matrix (all fields identified and classified), (b) Justification for each job-relevant field (why necessary for recruitment decision), (c) Confirmation that scoring model excludes sensitive fields and proxies, (d) Separate data storage architecture diagram, (e) DPO sign-off on lawfulness and necessity, (f) Technical control implementation (code review confirming fields excluded) |
| **Test Method** | **Design adequacy:** Data classification matrix reviewed by DPO and AI Governance for completeness and proportionality. **Implementation:** Code review confirms sensitive fields not passed to scoring model; data access logs confirm separation. **Operating effectiveness:** Monthly audit of data stored in scoring system; verify no sensitive fields present. |
| **Success Criteria** | 1. **All sensitive personal data excluded from scoring model** (verified by code review). 2. **Age-agnostic scoring implemented** (graduation date and date of birth not used; years of relevant experience used instead). 3. **Equal opportunities data separated from scoring** (different database or system; linked only by secure applicant ID). 4. **DPO confirmation** that data minimisation is lawful and sufficient. 5. **No sensitive data fields found in pilot audit** (100% compliance). |
| **Residual Risk** | REC-AI-003/004/005/008: MEDIUM (mitigated from HIGH) — Data minimisation reduces discrimination risk by eliminating direct access to protected characteristics. Residual risk remains if proxy variables still present. |
| **Status** | ⏳ DESIGN — Awaiting model architecture design |
| **Timeline** | Start: Model design phase; Complete: Before development begins |
| **Dependencies** | Model requirements and architecture finalised |
| **Owner Sign-Off** | *[Data Science Lead]* |
| **Approval Sign-Off** | *[Data Protection Officer]* |

---

## CONTROL 3: Human Review Procedure (No Auto-Rejection)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-003 |
| **Risk Mitigated** | REC-AI-009 (human oversight failure); supports mitigation of all discrimination risks through human review gate |
| **Objective** | Ensure meaningful human review of all AI recommendations; prevent auto-rejection of applicants; preserve HR judgment in final interview decision |
| **Control Activity** | Formalise HR procedure requiring: (a) ALL applicants receiving AI score reviewed by HR before any recommendation to interview or rejection, (b) HR review includes AI score, key factors contributing to score, and applicant CV/application, (c) HR staff empowered and trained to override AI recommendations, (d) HR documents review decision (accept AI recommendation or override with rationale), (e) No auto-rejection threshold; all candidates below recommendation threshold presented to HR for individual review, (f) Final interview decision made by HR with human judgment prioritised over AI score |
| **Owner** | HR Manager (Recruitment) in consultation with AI Governance and Data Science |
| **Trigger** | Pilot testing phase and ongoing operation |
| **Procedure** | **Step 1:** Draft HR Recruitment Screening Procedure including: (a) Mandatory HR review checklist, (b) How to interpret AI score and contributing factors, (c) Questions for HR to ask ("Is score consistent with qualifications? Are there extenuating circumstances for employment gap? Does applicant have hidden potential?"), (d) Override decision form (record HR decision, rationale, reason for override if applicable), (e) Escalation for bias concerns. **Step 2:** Train all HR staff using new procedure; test understanding. **Step 3:** Implement in pilot testing; monitor compliance and review quality. **Step 4:** Refine procedure based on pilot feedback. **Step 5:** Continue in production with monthly audit of review quality. |
| **Evidence** | (a) Signed HR Recruitment Screening Procedure (approved by HR Director and AI Governance), (b) Training attendance records, (c) Override decision forms (sample 10% of decisions), (d) Monthly audit report (compliance with procedure, override rates by demographic group), (e) HR feedback on procedure effectiveness |
| **Test Method** | **Design adequacy:** Procedure reviewed by HR Director, AI Governance, and legal counsel for clarity and compliance. **Implementation:** HR staff training completed; understanding assessed via test scenarios. **Operating effectiveness:** Monthly audit of 10% of review decisions; verify procedure followed, review quality adequate, override rationale documented. Quarterly analysis of override rate by demographic group (alert if varies significantly, indicating potential bias in HR judgment or AI scoring). |
| **Success Criteria** | 1. **100% of AI recommendations reviewed by HR** (verified by audit). 2. **Override rate ≥5%** (indicates meaningful review; if <5%, suggests over-reliance on AI). 3. **Override rate consistent across demographic groups** (alert if override rate for women <5% but for men >10%, suggesting gender bias in HR judgment). 4. **HR staff training completed** and understanding demonstrated. 5. **Procedure followed in ≥95% of cases** (verified by audit). 6. **No auto-rejections** (all candidates below threshold reviewed by HR for possible override). |
| **Residual Risk** | REC-AI-009: MEDIUM (mitigated from MEDIUM-HIGH); All discrimination risks: MEDIUM (human review gate provides opportunity to catch and correct AI errors) |
| **Status** | ⏳ DESIGN — Awaiting HR procedures design |
| **Timeline** | Start: Before pilot begins; Complete: HR training complete and procedure operational |
| **Dependencies** | HR staffing and training capacity; AI explainability implemented |
| **Owner Sign-Off** | *[HR Manager]* |
| **Approval Sign-Off** | *[HR Director]* |

---

## CONTROL 4: Explainability & Transparency

| Attribute | Detail |
|---|---|
| **Control ID** | CON-004 |
| **Risk Mitigated** | REC-AI-007 (black box scoring); supports all fairness and accountability objectives |
| **Objective** | Ensure AI scoring model provides transparent, understandable explanations of candidate scores; enable HR staff and applicants to understand scoring rationale |
| **Control Activity** | (a) Implement or require explainability techniques (SHAP values, feature importance, decision trees, rule-based models) that identify top factors contributing to each score, (b) Generate explanation summary for HR (e.g., "Candidate matched 5/6 essential qualifications, exceeded minimum experience by 2 years, skill gaps in area X"), (c) Provide applicant with explanation if requested (right to explanation under GDPR Article 22), (d) Document and audit scoring logic regularly |
| **Owner** | Data Science Lead (implementation); AI Governance (policy and applicant transparency) |
| **Trigger** | Model development; testing before pilot; operational on ongoing basis |
| **Procedure** | **Step 1:** Evaluate model architecture for interpretability; if black box (neural network, ensemble), implement explainability technique (SHAP, LIME, permutation importance). **Step 2:** For each applicant scored, generate explanation summary highlighting top 3–5 factors contributing to score, both positive and negative. **Step 3:** Ensure HR interface displays explanation alongside score and CV. **Step 4:** Train HR staff to interpret explanations and identify potential bias signals. **Step 5:** If applicant requests explanation, provide summary via formal response (e.g., email from HR/AI Governance within 10 days). **Step 6:** Document scoring methodology in system documentation; make available to applicants upon request. |
| **Evidence** | (a) Explainability methodology documentation (SHAP/LIME/other technique), (b) Sample score explanations reviewed for clarity and accuracy, (c) HR interface screenshots showing score + explanation, (d) Applicant communication template for explanation requests, (e) Scoring methodology document, (f) HR training materials on interpreting explanations |
| **Test Method** | **Design adequacy:** Explainability methodology reviewed by data scientist and HR for clarity and usefulness. **Implementation:** Sample applicants scored; explanations reviewed by HR for understandability and accuracy. **Operating effectiveness:** Monthly review of explanation quality (sample 10 explanations); verify explanations are specific, non-technical, and useful for HR and applicant understanding. Applicant request response time audit (≤10 days). |
| **Success Criteria** | 1. **Explanations are understandable** to HR staff without data science background (verified by user testing). 2. **Explanations are accurate** (verified by spot-check against actual scoring model and applicant CV). 3. **Top 3–5 factors captured** for each score (not generic). 4. **Applicant explanation requests processed within 10 days**. 5. **No applicant complaints** about lack of clarity or inaccuracy in explanation. |
| **Residual Risk** | REC-AI-007: MEDIUM (mitigated from HIGH); supports accountability and HR oversight for all discrimination risks |
| **Status** | ⏳ DESIGN — Awaiting model selection and architecture confirmation |
| **Timeline** | Start: Model development; Complete: Before pilot begins |
| **Dependencies** | Model architecture finalised; explainability tools evaluated and selected |
| **Owner Sign-Off** | *[Data Science Lead]* |
| **Approval Sign-Off** | *[AI Governance Lead]* |

---

## CONTROL 5: Data Protection Impact Assessment (DPIA)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-005 |
| **Risk Mitigated** | REC-AI-008 (GDPR and data protection violations) |
| **Objective** | Identify and mitigate data protection risks; ensure lawful processing of applicant personal data and special categories; demonstrate GDPR compliance |
| **Control Activity** | Complete formal Data Protection Impact Assessment (DPIA) per UK GDPR Article 35, covering: (a) Legal basis for processing (contract for recruitment, consent, employment law), (b) Special category data (demographics, disability) — explicit lawful basis and consent process, (c) Data retention and deletion schedule, (d) Applicant rights procedures (access, rectification, erasure, portability), (e) Third-party data sharing (vendors, cloud providers) and Data Processing Agreements, (f) Data security measures, (g) Incident management and breach notification, (h) Applicant transparency (privacy notice, disclosure of AI use), (i) Risk assessment and mitigation |
| **Owner** | Data Protection Officer (in consultation with HR, IT Security, AI Governance) |
| **Trigger** | Before any applicant data collection begins |
| **Procedure** | **Step 1:** DPO completes DPIA questionnaire per ICO DPIA guidance. **Step 2:** Identify high-risk processing (e.g., automated decision-making, special category data, decision affecting legal rights). **Step 3:** For each high-risk item, document mitigations (technical and organisational controls). **Step 4:** Assess residual data protection risk. **Step 5:** Determine if Data Protection Impact Assessment consultation with ICO needed (high residual risk). **Step 6:** Obtain sign-off from HR Director and AI Governance. **Step 7:** If consultation needed, submit to ICO; implement their recommendations. **Step 8:** Maintain DPIA as living document; update upon material changes (model changes, vendor changes, data use changes). |
| **Evidence** | (a) Completed DPIA form and documentation, (b) Privacy Notice for applicants (describing AI use, data processing, rights), (c) Consent form (if consent-based legal basis), (d) Data retention schedule, (e) Applicant rights procedures documentation, (f) Data Processing Agreements with vendors/cloud providers, (g) IT Security assessment of data protection measures, (h) DPO, HR Director, and AI Governance sign-off, (i) ICO consultation documentation (if applicable) |
| **Test Method** | **Design adequacy:** DPIA reviewed by independent DPO (not Trust employee) for completeness and compliance with GDPR. **Implementation:** Privacy Notice reviewed for applicant clarity; consent form tested for informed consent. **Operating effectiveness:** Annual review of DPIA; update for any material changes. Incident management: track data breaches or rights requests; verify procedures followed. |
| **Success Criteria** | 1. **DPIA completed and approved** by DPO before any data collection. 2. **Privacy Notice published** and provided to applicants before CV submission. 3. **Consent obtained** (if consent-based legal basis) or lawful basis documented. 4. **Data retention schedule implemented** (automated deletion per schedule, e.g., 6 months for rejected applicants). 5. **Applicant rights procedures operational** (data access within 30 days, deletion honoured, etc.). 6. **No data protection breaches or ICO enforcement** during pilot. |
| **Residual Risk** | REC-AI-008: MEDIUM (mitigated from HIGH) — DPIA provides evidence of lawful processing and risk management. Residual risk remains if controls not implemented or breaches occur. |
| **Status** | ⏳ DESIGN — Awaiting DPIA commencement |
| **Timeline** | Start: Before any applicant data collected; Complete: Before pilot begins |
| **Dependencies** | Legal basis determined; Privacy Notice drafted; consent process designed; data retention policy defined |
| **Owner Sign-Off** | *[Data Protection Officer]* |
| **Approval Sign-Off** | *[HR Director]* |

---

## CONTROL 6: Bias Monitoring Dashboard (Ongoing)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-006 |
| **Risk Mitigated** | REC-AI-012 (inadequate monitoring); REC-AI-001/002/003/004/006/010 (all discrimination risks) |
| **Objective** | Implement continuous monitoring for discrimination and bias in operation; detect disparate impact early; trigger escalation for investigation and remediation |
| **Control Activity** | Build automated monitoring dashboard tracking fairness metrics: (a) Interview recommendation rate by demographic group (age cohort, gender, ethnicity if available), (b) Job offer rate by group, (c) Job performance (if available) by group, (d) Override rate by group (HR decisions vs. AI recommendation), (e) Candidate pool demographics vs. interview pool vs. hire pool (funnel analysis), (f) Scoring distribution by demographic group (alert if mean/median scores differ significantly). Compare metrics against baseline and alert on disparate impact (impact ratio <0.8). |
| **Owner** | Data Analytics Lead in consultation with AI Governance and HR |
| **Trigger** | Pilot testing phase; continue through operation |
| **Procedure** | **Step 1:** Design dashboard schema: (a) Data sources (recruitment system, applicant data, HR decisions, outcomes), (b) Demographic data collection process (voluntary equal opportunities form, optional applicant disclosure), (c) Linking applicant demographics to scoring and outcomes, (d) Data governance (privacy, access controls). **Step 2:** Build dashboard with automated data pipeline. **Step 3:** Configure alerts for fairness metrics (impact ratio <0.8, scoring gap >10%, conversion rate gap >15%). **Step 4:** Test dashboard on pilot data; verify calculations and alerts. **Step 5:** Deploy in pilot; monitor weekly. **Step 6:** Establish escalation procedure: alert sent to Data Analytics → AI Governance Lead → HR Director. **Step 7:** Continue monitoring monthly in operation. |
| **Evidence** | (a) Dashboard design and implementation documentation, (b) Fairness metrics defined (formulas, thresholds), (c) Alert configuration and escalation procedures, (d) Weekly/monthly dashboard reports during pilot, (e) Escalation incident log, (f) Investigation and remediation records |
| **Test Method** | **Design adequacy:** Fairness metrics reviewed by statistician and AI Governance for correctness and relevance. **Implementation:** Test dashboard on historical recruitment data; verify calculations match manual audit. **Operating effectiveness:** Weekly dashboard reports reviewed; monthly audit of data quality and alert accuracy; test escalation procedure. |
| **Success Criteria** | 1. **Dashboard operational** before or early in pilot testing. 2. **All fairness metrics calculated and updated** at least weekly. 3. **Alerts triggered correctly** (manual testing confirms alerts fire when metric thresholds crossed). 4. **Demographic data collected** from ≥80% of applicants (or representative sample). 5. **No alerts suppressed or ignored** without documented investigation. 6. **Escalation procedure followed** upon alert (investigation completed, findings documented within 5 days). |
| **Residual Risk** | REC-AI-012: MEDIUM (mitigated from HIGH); all discrimination risks: MEDIUM (monitoring provides early warning and evidence of bias for investigation and remediation) |
| **Status** | ⏳ DESIGN — Awaiting dashboard requirements and data source assessment |
| **Timeline** | Start: Dashboard design during pilot planning; Complete: Live before pilot begins |
| **Dependencies** | Recruitment system data access; demographic data collection process; data analytics resources |
| **Owner Sign-Off** | *[Data Analytics Lead]* |
| **Approval Sign-Off** | *[AI Governance Lead]* |

---

## CONTROL 7: HR Training on AI Bias & Fairness

| Attribute | Detail |
|---|---|
| **Control ID** | CON-007 |
| **Risk Mitigated** | REC-AI-009 (human oversight failure); REC-AI-001/002/003/004/006 (discrimination risks) |
| **Objective** | Ensure HR staff understand AI limitations, bias, fairness concerns, and their role in providing meaningful human oversight |
| **Control Activity** | Develop and deliver training to HR staff before pilot testing covering: (a) What is AI and how does it work in recruitment?, (b) What is bias? Sources of bias (training data, model design, proxy variables, human bias), (c) What is discrimination? Equality Act 2010, direct and indirect discrimination, disparate impact, (d) How to interpret AI scores and explanations, (e) How to identify bias signals (e.g., score seems inconsistent with qualifications), (f) How to exercise override and document rationale, (g) Fairness principles and HR's role in oversight, (h) Real-world examples of AI bias in recruitment, (i) Escalation procedures for bias concerns |
| **Owner** | AI Governance Lead in consultation with HR and Legal |
| **Trigger** | Before pilot testing begins |
| **Procedure** | **Step 1:** Develop training curriculum (1–2 hour classroom or online module) with learning objectives and assessment. **Step 2:** Include real-world case studies of AI bias in recruitment. **Step 3:** Conduct training for all HR staff involved in recruitment screening. **Step 4:** Assess understanding via test scenarios (e.g., "Review this score and explanation; identify bias signals; explain your override decision"). **Step 5:** Document training attendance and assessment results. **Step 6:** Provide job aids and reference materials for ongoing use. **Step 7:** Refresh training annually and upon material system changes. |
| **Evidence** | (a) Training curriculum and materials, (b) Training delivery records (attendance, dates), (c) Assessment results (test scenario performance), (d) HR feedback on training usefulness, (e) Job aids and reference materials (e.g., "How to Spot Bias in AI Scores"), (f) Trainer qualifications (expertise in AI fairness and legal compliance) |
| **Test Method** | **Design adequacy:** Training curriculum reviewed by AI fairness expert and legal counsel for accuracy and completeness. **Implementation:** Training delivered to pilot HR staff; understanding assessed via scenario-based questions. **Operating effectiveness:** 3-month check-in with HR staff to assess knowledge retention; audit of bias signal identification in actual scoring review. |
| **Success Criteria** | 1. **≥95% of HR staff trained** before pilot begins. 2. **≥80% pass assessment** (correct answers to scenario-based test questions). 3. **Positive feedback** on training usefulness (survey >3.5/5 rating). 4. **Correct identification of bias signals** in audited scoring reviews (sample 5; ≥4/5 identified signals). 5. **No feedback from HR** that training inadequate after pilot begins (exit survey). |
| **Residual Risk** | REC-AI-009: MEDIUM (mitigated from MEDIUM-HIGH); discrimination risks: MEDIUM (informed HR staff better able to identify and challenge AI bias) |
| **Status** | ⏳ DESIGN — Awaiting training curriculum development |
| **Timeline** | Start: Curriculum development; Complete: Training delivered before pilot begins |
| **Dependencies** | AI fairness expertise available for curriculum; HR staff availability for training |
| **Owner Sign-Off** | *[AI Governance Lead]* |
| **Approval Sign-Off** | *[HR Director]* |

---

## CONTROL 8: Vendor Assessment & Contract Terms (If Applicable)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-008 |
| **Risk Mitigated** | REC-AI-011 (vendor lock-in and audit rights); REC-AI-001/002/003/004/006/010 (discrimination risks if vendor model used) |
| **Objective** | If using vendor-supplied AI recruitment model, ensure vendor commitment to fairness, audit transparency, and data protection; establish strong contract terms protecting Trust |
| **Control Activity** | (a) Require vendor to provide evidence of fairness testing (training data composition, performance by demographic group, fairness audit results), (b) Negotiate audit rights (right to access model, test on Trust data, conduct independent fairness audit), (c) Require Data Processing Agreement confirming vendor will not use Trust applicant data for model improvement or analytics, (d) Include liability clause for discriminatory outcomes, (e) Define model update procedures (vendor must not update model without Trust consent and fairness revalidation), (f) Establish exit strategy (data export, model handover, support for migration), (g) Include fairness performance guarantees (SLA for fairness metrics; vendor must remediate if disparate impact detected) |
| **Owner** | Procurement in consultation with AI Governance, Legal, and Data Protection Officer |
| **Trigger** | Vendor selection phase; before contract signed |
| **Procedure** | **Step 1:** Issue Vendor Fairness Assessment Questionnaire (VAQ) to shortlisted vendors. **Step 2:** Evaluate responses; request evidence (training data composition, fairness testing results, audit rights, liability position). **Step 3:** Conduct independent fairness assessment of vendor model (if possible) or review vendor-provided fairness documentation. **Step 4:** Escalate fairness concerns to Procurement and AI Governance; may disqualify vendor. **Step 5:** For preferred vendor, negotiate contract terms including: (a) Audit rights, (b) Data protection commitments, (c) Fairness guarantees, (d) Liability for discrimination, (e) Exit strategy. **Step 6:** Legal review of contract by Trust legal team. **Step 7:** Execute contract with fairness terms embedded. **Step 8:** Monitor vendor fairness performance during pilot. |
| **Evidence** | (a) Vendor Fairness Assessment Questionnaire (VAQ) and vendor responses, (b) Fairness assessment report (if independent assessment conducted), (c) Contract terms document highlighting fairness clauses, (d) Data Processing Agreement, (e) Legal review sign-off, (f) Vendor fairness performance monitoring reports |
| **Test Method** | **Design adequacy:** VAQ reviewed by AI fairness expert for comprehensiveness; contract terms reviewed by legal counsel. **Implementation:** Vendor responses evaluated against fairness criteria; evidence assessed for credibility. **Operating effectiveness:** Monthly monitoring of vendor model performance against fairness metrics; escalation if vendor fails to meet SLA. Audit of vendor's use of Trust applicant data. |
| **Success Criteria** | 1. **Vendor provides evidence of fairness testing** (training data composition, demographic performance). 2. **Audit rights and transparency commitments secured** in contract. 3. **Data Processing Agreement specifies** vendor will not use Trust applicant data for model improvement. 4. **Vendor liability for discrimination included** in contract (e.g., indemnification for employment law claims). 5. **No evidence of vendor using Trust data improperly** (audited annually). 6. **Vendor fairness performance meets SLA** (e.g., impact ratio ≥0.8). |
| **Residual Risk** | REC-AI-011: MEDIUM (mitigated from MEDIUM-HIGH); discrimination risks: MEDIUM if vendor model (depends on vendor fairness practices) |
| **Status** | ⏳ DESIGN — Awaiting vendor selection decision |
| **Timeline** | Start: Vendor selection; Complete: Contract execution with fairness terms |
| **Dependencies** | Vendor selection decision; legal resources for contract negotiation |
| **Owner Sign-Off** | *[Procurement Manager]* |
| **Approval Sign-Off** | *[AI Governance Lead]* |

---

## CONTROL 9: Independent Fairness Audit (Quarterly)

| Attribute | Detail |
|---|---|
| **Control ID** | CON-009 |
| **Risk Mitigated** | All discrimination and fairness risks (REC-AI-001 through REC-AI-010) |
| **Objective** | Conduct periodic independent fairness audits to verify absence of discrimination and effectiveness of controls in operation |
| **Control Activity** | Quarterly independent audit by external auditor (not model developer or Trust employee) assessing: (a) Fairness metrics from monitoring dashboard, (b) Statistical tests for disparate impact by demographic group, (c) HR override decision analysis (rate, rationale, patterns by group), (d) Interview conversion and hiring outcomes by group, (e) Complaints or concerns raised by applicants or HR staff, (f) Control effectiveness (DPIA, data minimisation, explainability, HR procedures), (g) Vendor performance (if vendor model), (h) Recommendations for model adjustment or system changes |
| **Owner** | Independent Audit Function in consultation with AI Governance |
| **Trigger** | End of pilot testing phase; then quarterly in operation |
| **Procedure** | **Step 1:** Quarterly audit planning: define scope (fairness metrics, control checks), data required (recruitment data, HR decisions, outcomes), methodology (statistical analysis, interview sampling). **Step 2:** Data extraction: secure applicant data from recruitment system with appropriate access controls and confidentiality agreements. **Step 3:** Analysis: (a) Calculate fairness metrics for each demographic group, (b) Perform statistical tests for disparate impact (chi-square for recommendation rates, t-tests for scoring gaps), (c) Analyse HR override patterns, (d) Review complaints and escalations, (e) Spot-check control implementation. **Step 4:** Findings and recommendations: draft audit report identifying fairness concerns, control deficiencies, and recommendations. **Step 5:** Present to AI Governance and HR Director; discuss findings and remediation plans. **Step 6:** Follow-up: track remediation of prior quarter findings; verify actions completed. |
| **Evidence** | (a) Quarterly audit reports with fairness analysis, (b) Statistical test results and significance levels, (c) Audit working papers (data extracted, calculations), (d) Auditor credentials (fairness expertise), (e) Audit sign-off by AI Governance, (f) Remediation tracking: prior findings and actions completed |
| **Test Method** | **Design adequacy:** Audit plan reviewed by AI Governance for scope and methodology. **Implementation:** Audit conducted by qualified independent auditor; statistical methods appropriate and correctly applied. **Operating effectiveness:** Quarterly reporting to AI Governance and Audit Committee; trend analysis of fairness metrics over time; follow-up on remediation of findings. |
| **Success Criteria** | 1. **Quarterly audit reports completed** on schedule. 2. **No statistically significant disparate impact identified** in audit (p>0.05). 3. **Control deficiencies identified and remediated** in ≤30 days (escalation if not remediated). 4. **Auditor independence** verified (no conflicts of interest). 5. **Reports reviewed by AI Governance and Audit Committee** before finalised. 6. **No material fairness concerns** identified in audit (or concerns identified and remediation in progress). |
| **Residual Risk** | All discrimination risks: MEDIUM (mitigated through ongoing verification that controls effective and discrimination not occurring) |
| **Status** | ⏳ DESIGN — Awaiting audit resource planning |
| **Timeline** | Start: Post-pilot phase; Complete: Ongoing quarterly |
| **Dependencies** | Independent audit resources available; Audit Committee oversight; access to recruitment data |
| **Owner Sign-Off** | *[Internal Audit Function]* |
| **Approval Sign-Off** | *[Audit Committee]* |

---

## CONTROL 10: Discrimination Complaint & Escalation Procedure

| Attribute | Detail |
|---|---|
| **Control ID** | CON-010 |
| **Risk Mitigated** | All discrimination risks; enables detection of harm and escalation for remediation |
| **Objective** | Establish clear escalation pathway for applicants or staff to raise discrimination concerns; ensure concerns investigated and remediated promptly |
| **Control Activity** | Define and communicate discrimination complaint procedure: (a) Applicants can request explanation of score or challenge AI recommendation, (b) Applicants or staff can raise formal discrimination complaint, (c) Complaints received by HR and escalated to AI Governance and Data Protection Officer, (d) Formal investigation of complaint (assess whether discrimination occurred, collect evidence), (e) Remediation (applicant reconsideration, model adjustment, system suspension if serious), (f) Communication of findings to applicant and staff, (g) Documentation in incidents log for monitoring trends |
| **Owner** | HR Manager and AI Governance Lead (joint responsibility) |
| **Trigger** | Upon receipt of complaint or concern |
| **Procedure** | **Step 1:** Publicise complaint procedure in recruitment materials and to HR staff (how to report, who to contact, expected timeline). **Step 2:** Upon receipt of complaint: (a) HR logs complaint in incidents database; (b) Assigns investigation owner; (c) Sends acknowledgment to complainant. **Step 3:** Investigation: (a) Gather evidence (applicant data, AI score, HR review, comparison with other applicants), (b) Assess whether AI system used inappropriately or evidence of discrimination, (c) Interview HR staff if relevant, (d) Analyse fairness metrics for similar applicant pool (e.g., if complaint about age discrimination, compare scoring and outcomes for similar-aged applicants). **Step 4:** Findings: (a) Determine whether discrimination occurred; (b) If yes, recommend remediation (applicant reconsideration, score revalidation, model adjustment). **Step 5:** Remediation: (a) Implement findings (e.g., reoffering interview to applicant, adjusting model), (b) Communicate outcome to complainant. **Step 6:** Trend analysis: Quarterly review of complaints by type (age, gender, ethnicity, etc.); identify patterns; escalate if systemic issue identified. |
| **Evidence** | (a) Discrimination Complaint Procedure (published document), (b) Complaints log (incident database), (c) Investigation reports (findings, evidence, remediation), (d) Communications to complainant (acknowledgment, findings, remediation), (e) Quarterly trends analysis, (f) Escalation records |
| **Test Method** | **Design adequacy:** Procedure reviewed by HR and Legal for fairness and compliance with Equality Act 2010. **Implementation:** Test procedure with sample complaint; verify investigation thorough and finding sound. **Operating effectiveness:** Monthly review of complaints received and investigation status; verify investigations completed within defined timeline (e.g., 20 days); verify remediation implemented; quarterly trends analysis for patterns suggesting systemic issues. |
| **Success Criteria** | 1. **Complaint procedure documented and communicated** to applicants and staff. 2. **Complaints tracked in incident database**. 3. **Investigations completed within 20 days** of complaint receipt. 4. **Investigation findings documented** (facts, analysis, conclusion, remediation). 5. **Remediation implemented** (e.g., applicant reoffering, model adjustment) within 10 days of investigation conclusion. 6. **Complainant notified** of findings and remediation. 7. **Trends identified and escalated** if pattern of similar complaints detected. |
| **Residual Risk** | All discrimination risks: MEDIUM (escalation procedure enables detection and remediation of discrimination if it occurs despite preventive controls) |
| **Status** | ⏳ DESIGN — Awaiting procedure development |
| **Timeline** | Start: Before pilot begins; Complete: Procedure operational and communicated |
| **Dependencies** | HR resources for investigation; incident management system |
| **Owner Sign-Off** | *[HR Manager]* |
| **Approval Sign-Off** | *[AI Governance Lead]* |

---

## Control Implementation Timeline

### Before Pilot Testing
- CON-001: Fairness Baseline Assessment
- CON-002: Data Minimisation & Separation
- CON-003: HR Review Procedure
- CON-004: Explainability & Transparency
- CON-005: DPIA
- CON-007: HR Training
- CON-008: Vendor Assessment (if applicable)
- CON-010: Complaint Procedure

### During Pilot Testing
- CON-003: HR Review Procedure (ongoing)
- CON-006: Bias Monitoring Dashboard
- CON-010: Complaint Procedure (ongoing)

### Before Production Rollout
- CON-009: Independent Fairness Audit

### Ongoing (Post-Launch)
- CON-003: HR Review Procedure
- CON-006: Bias Monitoring Dashboard (monthly)
- CON-009: Independent Fairness Audit (quarterly)
- CON-010: Complaint Procedure

---

## Control Ownership & Accountability

| Control | Primary Owner | Supporting Owner(s) | Approval Authority |
|---|---|---|---|
| CON-001 | Data Science Lead | AI Governance, HR | AI Governance Committee |
| CON-002 | Data Protection Officer | Data Science, IT Security | DPO, AI Governance |
| CON-003 | HR Manager | AI Governance | HR Director |
| CON-004 | Data Science Lead | AI Governance | AI Governance Committee |
| CON-005 | Data Protection Officer | HR, IT Security, AI Governance | DPO, HR Director |
| CON-006 | Data Analytics Lead | AI Governance, HR | AI Governance Committee |
| CON-007 | AI Governance Lead | HR, Legal | HR Director |
| CON-008 | Procurement | AI Governance, Legal, DPO | AI Governance Committee |
| CON-009 | Internal Audit Function | AI Governance | Audit Committee |
| CON-010 | HR Manager | AI Governance, DPO | HR Director |

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
