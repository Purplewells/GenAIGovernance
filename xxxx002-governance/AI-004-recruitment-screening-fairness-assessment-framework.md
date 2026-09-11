---
title: AI-004 AI Recruitment Screening — Fairness Assessment Framework
date: 2026-09-11
lifecycle_stage: Design & Testing
scope: Methodology and procedures for testing AI recruitment model for discrimination and bias across protected characteristics
decision_requested: Whether proposed fairness assessment framework is adequate to identify discrimination risks before pilot and operation
owner: Data Science Lead
approval_authority: AI Governance Committee
review_date: 2026-12-11
status: Draft for consultation
---

# AI-004 AI Recruitment Screening — Fairness Assessment Framework

## Executive Summary

This framework defines the methodology and procedures for assessing whether the AI recruitment scoring model exhibits discrimination or disparate impact based on protected characteristics (age, gender, ethnicity, disability, sexual orientation, gender reassignment, religion, pregnancy/maternity).

The framework applies the **NIST AI Risk Management Framework MEASURE function** (assess trustworthy AI characteristics) and is aligned with **Equality Act 2010** fairness obligations and **ICO algorithmic fairness guidance**.

## Assessment Phases

**Phase 1 — Pre-Pilot Fairness Assessment:** Before any applicant data processed; audit model design and training data  
**Phase 2 — Pilot Testing Assessment:** During pilot; monitor fairness metrics on live applicant data  
**Phase 3 — Pre-Production Fairness Audit:** Before production rollout; comprehensive analysis of pilot outcomes  
**Phase 4 — Ongoing Monitoring:** Quarterly fairness audits in operation

---

## Phase 1: Pre-Pilot Fairness Assessment

### Objective

Establish baseline understanding of model bias and discrimination risk before deploying system on live applicants.

### Activities

#### 1.1 Training Data Audit

**Objective:** Understand composition of training data by protected characteristic; identify underrepresented groups.

**For vendor-supplied models:**
- Request training data documentation from vendor (data composition, sources, time period)
- Analyse demographic breakdown: age distribution (cohorts: 18–30, 31–45, 46–55, 56+), gender (M/F/non-binary), ethnicity, disability status, other protected characteristics
- Identify underrepresented groups (e.g., if ethnic minorities <15% of training data, model performance on this group may be poor)
- Document known biases in training data (e.g., if vendor trained on historical UK recruitment data, data likely includes historical discrimination patterns)
- Request vendor attestation that training data does not include explicit discrimination or fairness concerns

**For internally-developed models:**
- Audit internal training data (historical hiring decisions or external recruitment datasets used)
- Analyse demographic composition
- Assess representativeness of Trust's applicant pool (e.g., if Trust hires many women for nursing roles but training data is 30% women, model may underperform on women)
- Document any known biases or data quality issues

**Output:** Training Data Audit Report documenting:
- Data sources and time period
- Sample size and composition
- Demographic breakdown (percentages for each cohort)
- Underrepresented groups
- Known biases or limitations
- Representativeness compared to Trust applicant demographics

#### 1.2 Model Performance Testing

**Objective:** Assess model accuracy and fairness across demographic cohorts; identify performance gaps.

**Scope:** Test model on held-out test data (not training data) stratified by protected characteristic.

**Methodology:**
1. **Obtain test data:** If vendor model, request vendor test dataset or use external fairness benchmark (if available). If internal model, use held-out test set (20–30% of training data).
2. **Stratify by demographic cohort:** Create subgroups by age (18–30, 31–45, 46–55, 56+), gender, ethnicity, disability (if available in data).
3. **Calculate performance metrics for each cohort:**
   - Accuracy (% correct predictions)
   - Precision (% recommended candidates who are actually good fits)
   - Recall (% actual good fits recommended)
   - False-positive rate (% false recommendations)
   - False-negative rate (% missed good candidates)
   - Mean score, median score, score distribution

4. **Compare performance across cohorts:**
   - Identify performance gaps (e.g., false-negative rate 15% for women vs. 8% for men)
   - Perform statistical tests (t-tests, chi-square) to determine if gaps are significant (p<0.05)
   - Calculate effect sizes (e.g., Cohen's d)

5. **Calculate disparate impact ratios:**
   - Impact Ratio = (Recommendation rate for Group A) / (Recommendation rate for Group B)
   - Threshold: If <0.8, indicates potential indirect discrimination (Uniform Guidelines)
   - Calculate for each demographic group vs. reference group

**Output:** Model Performance Report documenting:
- Performance metrics by demographic cohort (accuracy, precision, recall, FPR, FNR)
- Performance gaps identified and statistical significance
- Disparate impact ratios
- High-risk findings (e.g., FNR 20% for older workers)
- Recommendations (model acceptable, needs adjustment, or too risky to deploy)

#### 1.3 Proxy Variable Audit

**Objective:** Identify variables correlated with protected characteristics that may cause indirect discrimination.

**Methodology:**
1. **List all features used by model:** Extract feature importance or model coefficients if interpretable model.
2. **Identify proxy variables:** Flag features that may correlate with protected characteristics:
   - **Age proxies:** Graduation date, years of experience, career progression rate, employment gaps
   - **Gender proxies:** Career breaks, job titles (e.g., "administrative assistant" skews female), certain industries (e.g., nursing)
   - **Ethnicity proxies:** Educational institutions (prestige often correlates with ethnicity/socioeconomic status), first language, certain industry sectors
   - **Disability proxies:** Employment gaps, shorter employment history, certain certifications
3. **Test correlation:** For each proxy variable, analyse correlation with protected characteristic (if available in test data):
   - Calculate correlation coefficient (Pearson r, Spearman ρ)
   - Flag variables with high correlation (r>0.5 or ρ>0.5)
4. **Assess discriminatory impact:**
   - For each high-correlation proxy, estimate disparate impact (e.g., if "employment gap" is proxy for disability, does model score applicants with employment gaps lower?)
   - Determine if business necessity exists (is proxy necessary for job suitability?)
   - If no business necessity, recommend variable removal or model adjustment

**Output:** Proxy Variable Audit Report documenting:
- List of all model features
- Proxy variables identified and their correlation with protected characteristics
- Disparate impact assessment for each proxy
- Business necessity justification or recommendation to remove
- High-risk proxies requiring model adjustment

#### 1.4 Explainability Assessment

**Objective:** Verify model explanations are interpretable and accurate; assess HR's ability to understand and challenge scores.

**Methodology:**
1. **Generate explanations:** For sample of test applicants (n=20–50), generate score and explanation (top factors contributing to score).
2. **Review clarity:** Assess whether explanations are understandable to HR staff without data science background:
   - Use simple language (avoid jargon)
   - Highlight both positive and negative factors
   - Quantify importance (e.g., "This factor contributed 30% to the score")
3. **Verify accuracy:** Compare explanation against actual model scoring:
   - Do top factors actually contribute most to score (verified by model internals or sensitivity analysis)?
   - Are explanations consistent with model output?
4. **Test interpretability:** Ask sample HR staff (n=5–10) to:
   - Read explanation for sample applicant
   - Explain in own words why applicant scored low/high
   - Identify whether they can challenge score if appropriate
5. **Identify deficiencies:** If explanations unclear or inaccurate, determine if additional explainability techniques needed (SHAP, LIME, feature importance) or model redesign required.

**Output:** Explainability Assessment Report documenting:
- Sample explanations generated
- Clarity assessment (feedback from HR staff)
- Accuracy verification (comparison with model internals)
- Recommendations (explainability adequate or improvements needed)

#### 1.5 Composite Pre-Pilot Fairness Assessment

**Objective:** Synthesise findings from all Phase 1 activities; determine whether model safe to deploy in pilot.

**Decision Framework:**
- **GREEN (Proceed):** No significant fairness concerns identified; model can proceed to pilot with standard monitoring
- **YELLOW (Proceed with Caution):** Minor fairness concerns identified; model can proceed to pilot but with enhanced monitoring and shorter review cycle
- **RED (Do Not Proceed):** Significant disparate impact or discrimination risk identified; model must be adjusted before pilot testing

**Criteria for GREEN:**
- Impact ratio ≥0.8 for all demographic groups (or differences not statistically significant)
- Performance gaps (false-negative rates, accuracy) <10% across demographic cohorts (or not statistically significant)
- No high-correlation proxies used without business justification
- Explanations clear and accurate
- Training data representativeness acceptable (no major underrepresentation of protected groups)

**Criteria for YELLOW:**
- Impact ratio 0.70–0.80 for some groups (borderline disparate impact)
- Performance gaps 10–20% for some cohorts
- Some proxy variables used; business justification documented
- Explanations mostly clear; minor improvements recommended
- Training data underrepresents some groups; model performance acceptable despite underrepresentation

**Criteria for RED:**
- Impact ratio <0.70 for any demographic group (likely unlawful discrimination)
- Performance gaps >20% for demographic cohorts (e.g., FNR 25% for women vs. 5% for men)
- High-correlation proxy variables used without clear business necessity
- Explanations unclear or inaccurate; HR cannot understand or challenge scores
- Training data severely underrepresents protected groups; model performance poor for minorities

**Output:** Composite Fairness Assessment Report documenting:
- Summary of findings from all Phase 1 activities
- Key fairness concerns identified (if any)
- Recommendations for model adjustment (if needed)
- Decision: Proceed to pilot? If YELLOW, what enhanced monitoring required?
- Sign-off by Data Science Lead and independent fairness auditor

---

## Phase 2: Pilot Testing Assessment

### Objective

Monitor fairness metrics during pilot testing; ensure model performs equitably on real applicant data.

### Activities

#### 2.1 Fairness Metrics Monitoring

**Ongoing during pilot (weekly or bi-weekly):**

1. **Recommendation rate by demographic group:**
   - % of applicants recommended for interview in each age cohort, gender, ethnicity (if available)
   - Calculate impact ratios (recommendation rate for group / rate for reference group)
   - Alert if impact ratio <0.80 (potential disparate impact)

2. **Score distribution by demographic group:**
   - Mean score, median score, standard deviation for each cohort
   - Identify scoring gaps (e.g., women average score 55 vs. men 62)
   - Perform t-tests for significance

3. **HR override rates by demographic group:**
   - % of AI recommendations overridden by HR for each cohort
   - Alert if override rate significantly different by group (e.g., women overridden 15% of time, men 5%)
   - Analyse override rationale: do overrides correct for AI bias?

4. **Applicant flow by stage:**
   - Funnel analysis: % of applicants in each cohort advancing from application → AI recommendation → HR review → interview → hire
   - Identify bottlenecks or disparities

#### 2.2 Escalation & Investigation

**Upon alert (impact ratio <0.80 or other fairness concern):**

1. **Verify alert:** Confirm finding is accurate; rule out data quality issues
2. **Investigate root cause:** Is disparate impact due to:
   - Model bias (systematic scoring differences)?
   - Proxy variables (employment gaps, etc.)?
   - Different applicant pool characteristics (e.g., older applicants have fewer matched skills)?
   - HR human bias (override decisions systematically favour one group)?
3. **Assess legality:** Determine whether disparate impact is unlawful discrimination under Equality Act 2010 (illegal unless justified by business necessity)
4. **Recommend remediation:**
   - Model adjustment (retrain on balanced data, adjust thresholds)
   - Proxy variable removal or adjustment
   - HR retraining if human bias detected
   - Expansion of pilot (larger sample may show disparate impact is random variation, not systemic)

#### 2.3 Pilot Interim Fairness Report

**Output (every 4 weeks during pilot):**
- Fairness metrics dashboard (recommendation rate, scores, override rates by cohort)
- Alerts triggered and investigation results
- Trends (improving or worsening fairness?)
- Recommendations for model adjustment (if needed)

---

## Phase 3: Pre-Production Fairness Audit

### Objective

Comprehensive independent audit of pilot outcomes; final determination of whether model safe for production.

### Activities

#### 3.1 Pilot Outcome Analysis

**Conduct after pilot testing complete (minimum 500–1000 applications):**

1. **Analyse final outcomes by demographic group:**
   - Recommendation rate, interview rate, hire rate for each cohort
   - Perform statistical tests (chi-square) for differences
   - Calculate disparate impact ratios with 95% confidence intervals

2. **Perform regression analysis:**
   - Multivariable logistic regression to assess which factors predict recommendation (model features vs. demographics)
   - Calculate standardised coefficients; identify whether demographic variables have independent effect on outcome
   - Control for job-relevant factors; identify whether residual disparity remains

3. **Analyse HR override decisions:**
   - Did HR override AI recommendations at different rates for different groups?
   - Did overrides correct for AI bias?
   - Calculate override consistency (how consistently did HR apply override criteria?)

4. **Analyse hiring outcomes:**
   - For applicants hired, compare job performance by demographic group (if available; e.g., retention, performance rating)
   - Assess whether AI system selected best-performing candidates or just demographic match to historical hires
   - Identify false negatives (qualified applicants rejected by AI; would they have succeeded if hired?)

#### 3.2 Legal Compliance Assessment

**Conduct legal review of pilot outcomes:**

1. **Assess Equality Act 2010 compliance:**
   - Direct discrimination? Did model explicitly use protected characteristics? (Should not)
   - Indirect discrimination? Did model apply neutral criteria that indirectly disadvantage protected group? (Illegal unless justified by business necessity)
   - If disparate impact detected: Is it justified by business necessity? (e.g., if educational qualification required, disparate impact may be justified)

2. **Assess GDPR compliance:**
   - Was personal data processed lawfully (valid consent, contract, etc.)?
   - Were special category data (demographics) processed only with explicit consent/justification?
   - Were applicant rights honoured (access, rectification, erasure)?

3. **Assess fairness principles:**
   - Transparency: Were applicants informed of AI use?
   - Accountability: Can applicants request explanation of decision?
   - Redress: Can applicants challenge AI decision?

#### 3.3 Independent Fairness Audit Report

**Output:**
- Pilot outcome analysis (fairness metrics, disparate impact assessment, statistical significance)
- Legal compliance assessment (Equality Act 2010, GDPR)
- Fairness audit findings (key concerns, if any)
- Auditor recommendation: Proceed to production? If not, what remediation required?
- Sign-off by independent auditor and AI Governance Committee

#### 3.4 Production Decision

**Decision criteria:**

- **APPROVE for production:** No statistically significant disparate impact identified; legal compliance confirmed; fairness concerns addressed
- **APPROVE with enhanced monitoring:** Minor fairness concerns identified; increased monitoring frequency (weekly rather than monthly); shorter review cycle (30 days rather than 90 days)
- **DO NOT APPROVE:** Statistically significant disparate impact or legal non-compliance identified; model requires adjustment; may retest after remediation

---

## Phase 4: Ongoing Fairness Monitoring

### Objective

Continuous monitoring for fairness and discrimination after production deployment.

### Activities

#### 4.1 Monthly Fairness Metrics Reporting

**Ongoing each month:**

1. **Update fairness dashboard:** Recommendation rate, scores, override rates, interview conversion, hiring rate by demographic group
2. **Alert on disparities:** Flag if impact ratio <0.80 or other fairness threshold breached
3. **Trend analysis:** Plot fairness metrics over time; identify improving or worsening trends
4. **Dashboard review:** Present to HR and AI Governance; discuss findings

#### 4.2 Quarterly Independent Fairness Audit

**Every quarter (13-week cycle):**

1. **Statistical testing:** Test for statistically significant disparate impact (chi-square, logistic regression)
2. **Complaint analysis:** Review any discrimination complaints received; assess merit
3. **Root cause analysis:** If disparate impact detected, investigate cause (model bias, proxy variables, human bias, applicant pool characteristics)
4. **Recommendations:** If concerns identified, recommend remediation (model adjustment, HR retraining, proxy variable removal, etc.)
5. **Audit report:** Document findings, recommendations, remediation status of prior findings

#### 4.3 Escalation & Remediation

**Upon fairness concern identified in quarterly audit:**

1. **Immediate actions:** Alert HR and AI Governance; discuss findings
2. **Temporary measures:** If significant disparate impact, consider temporary pause or threshold adjustment while investigating
3. **Investigation:** Root cause analysis (model adjustment, HR bias, proxy variables, applicant pool characteristics)
4. **Remediation plan:** Specific actions to address concern; timeline; owner; success measures
5. **Retest after remediation:** Verify fairness concern resolved
6. **Escalation:** If concern not resolved, escalate to Executive Sponsorship (HR Director, Trust Board)

#### 4.4 Annual Fairness Review

**Annually:**

1. **Comprehensive fairness assessment:** Similar to Phase 3 pre-production audit
2. **Model update assessment:** If model updated/retrained, assess fairness impact
3. **Vendor audit:** If vendor model, audit vendor fairness claims and performance
4. **Policy review:** Update fairness policies and procedures based on operational learnings
5. **Report to Board:** Annual fairness and compliance report to AI Governance Committee and Trust Board

---

## Fairness Metrics & Thresholds

### Metrics

| Metric | Definition | Data Source | Calculation | Threshold |
|---|---|---|---|---|
| **Recommendation Rate** | % of applicants recommended for interview | HR system | (# recommended / # total applicants) × 100 | Compare across groups; alert if ratio <0.8 |
| **Impact Ratio** | Recommendation rate for protected group / reference group | HR system | (RR_group / RR_ref) | ≥0.8 acceptable; <0.8 potential disparate impact |
| **Mean Score Gap** | Difference in mean AI score between groups | Recruitment system | (Mean_score_group - Mean_score_ref) | <10 points acceptable; >15 points investigate |
| **Interview Conversion Rate** | % of recommended applicants interviewed | HR system | (# interviewed / # recommended) × 100 | Compare across groups; alert if ratio <0.8 |
| **Hiring Rate** | % of applicants hired | HR system | (# hired / # total applicants) × 100 | Compare across groups; alert if ratio <0.8 |
| **HR Override Rate** | % of AI recommendations overridden by HR | HR decision log | (# overridden / # total recommendations) × 100 | Compare across groups; alert if differs >5% between groups |
| **False-Negative Rate** (if performance available) | % of high-performing candidates not recommended | Hire/performance data | (# falsely rejected / # total qualified) × 100 | <15% acceptable; >20% investigate |

### Statistical Testing

- **Chi-square test:** Compare recommendation rates across demographic groups; assess independence of group membership and recommendation
- **T-test:** Compare mean scores across groups; test significance of score gaps
- **Logistic regression:** Multivariable analysis; assess independent effect of model features vs. demographics on recommendation
- **Confidence intervals:** Calculate 95% confidence intervals for impact ratios, rates; determine if differences significant

### Alert Thresholds

| Alert Type | Threshold | Action |
|---|---|---|
| **Disparate Impact** | Impact ratio <0.80 for any group | Investigate within 5 days; plan remediation within 10 days |
| **Score Gap** | Mean score difference >15 points | Investigate within 5 days; consider model adjustment |
| **Override Rate Gap** | HR override rate differs >5 percentage points between groups | Review HR review quality; assess for human bias |
| **Interview Conversion Gap** | Conversion rate differs >10 percentage points between groups | Investigate; assess for HR or recruiter bias |
| **Hiring Rate Disparity** | Hire rate differs >10 percentage points between groups | Investigate; assess for hiring manager bias or model impact |

---

## Governance & Accountability

| Role | Responsibility |
|---|---|
| **Data Science Lead** | Implement fairness assessment; report findings; recommend model adjustments |
| **AI Governance Lead** | Oversee assessment; escalate findings; track remediation |
| **Independent Auditor** | Conduct Phase 1, Phase 3, and quarterly audits; verify assessment rigor; audit sign-off |
| **HR Director** | Respond to fairness findings; implement HR training/procedures; make production decision |
| **Data Protection Officer** | Assess GDPR compliance; approve data processing; sign-off on compliance assessment |

---

## Documentation & Records

**Maintain documentation:**
- Phase 1 Pre-Pilot Fairness Assessment Report
- Phase 1 Training Data Audit
- Phase 1 Model Performance Report
- Phase 1 Proxy Variable Audit
- Phase 1 Explainability Assessment
- Monthly Fairness Metrics Dashboards (pilot and operation)
- Monthly Pilot Interim Fairness Reports
- Phase 3 Pre-Production Fairness Audit Report
- Quarterly Fairness Audit Reports (operation)
- Incident log (fairness concerns, investigations, remediation)

**Retention:** 7 years (employment records)

---

## Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | AI Governance | Draft for consultation |

---

**Document Classification:** Internal Use Only — AI Governance  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11
