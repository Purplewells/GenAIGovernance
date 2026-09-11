---
title: AI-004 AI Recruitment Screening — Data Protection Impact Assessment (DPIA)
date: 2026-09-11
lifecycle_stage: Design
scope: Assessment of data protection risks and compliance with UK GDPR and Data Protection Act 2018 for AI recruitment screening system
decision_requested: Whether data protection risks are adequately mitigated to permit lawful processing of applicant personal data and special categories
owner: Data Protection Officer
approval_authority: Data Protection Officer and HR Director
review_date: 2026-12-11
status: Ready for DPO review
---

# AI-004 AI Recruitment Screening — Data Protection Impact Assessment (DPIA)

## 1. Introduction & Legal Requirement

**Legal Basis:** UK GDPR Article 35 (Data Protection Impact Assessment)  
**Trigger:** Processing of special category data (demographics) and automated decision-making likely to significantly affect applicants' rights

**Assessment Required Because:**
- System processes personal data (name, contact, employment history, qualifications)
- System processes special category data (ethnicity, disability, sexual orientation, religion, pregnancy if disclosed)
- System makes automated scoring decision affecting applicant rights (interview opportunity, employment decision)
- Fairness and discrimination risks identified require privacy-protective controls

---

## 2. Data Processing Description

### 2.1 Purpose of Processing

Screening applicant CVs and applications to identify qualified candidates for interview; reducing recruitment time; standardising screening decisions; enabling HR staff to focus on interview and candidate experience.

### 2.2 Personal Data Processed

**Mandatory Fields:**
- Applicant name
- Contact information (email, phone, address)
- Employment history (employers, job titles, dates)
- Educational qualifications (institutions, dates, grades)
- Experience and skills summary
- Years of experience

**Optional Fields (If Provided by Applicant):**
- Date of birth or age
- Ethnicity (equal opportunities form)
- Disability status (equal opportunities form)
- Sexual orientation, gender reassignment, religion/belief (equal opportunities form)
- Pregnancy/maternity status (if stated in CV)
- Marital/family status (if stated in CV)

### 2.3 Special Category Data

Data that requires explicit legal basis under GDPR Article 9:

- **Ethnicity/Race:** If applicant provides on equal opportunities form
- **Disability Status:** If applicant discloses or if inferred from CV (employment gaps, health-related career breaks)
- **Sexual Orientation & Gender Reassignment:** If applicant discloses
- **Religion/Belief:** If applicant discloses
- **Pregnancy/Maternity:** If applicant discloses or inferred from employment gap
- **Sex/Gender:** If applicant provides on equal opportunities form

### 2.4 Data Retention Period

| Category | Retention | Legal Basis |
|---|---|---|
| **Successful applicants (hired)** | 2 years post-hire (or end of employment + 1 year) | Employment law; tax compliance |
| **Unsuccessful applicants** | 6 months post-decision | Recruitment record-keeping |
| **Voluntary equal opportunities data** | 6 months post-decision (separate deletion) | Deleted earlier to minimise risk |

### 2.5 Processing Activities

1. **Data receipt:** Applicants submit CV/application via online portal or email
2. **Data entry:** Portal ingests and parses CV (OCR if PDF)
3. **Data extraction:** Information extraction (names, dates, qualifications, skills)
4. **Data processing:** AI scoring model processes extracted data; generates score
5. **Data review:** HR staff review AI score and applicant data; make interview recommendation
6. **Data storage:** Applicant data retained in recruitment system during hiring process; deleted per retention schedule
7. **Data access:** HR staff access applicant data to review recommendations; hiring managers access to make final decisions
8. **Third-party processing:** If vendor-supplied model, vendor cloud platform processes data; if cloud-hosted (Azure, AWS, Google), cloud provider processes data

---

## 3. Lawfulness Assessment

### 3.1 Legal Basis for Processing Ordinary Personal Data (GDPR Article 6)

**Legal Basis:** **Contract (Article 6(1)(b))** — Processing necessary to take steps before entering into contract of employment

**Rationale:** Applicant submits CV and application as part of recruitment process; processing necessary to assess suitability for employment and decide whether to offer interview.

**Alternative/Supplementary:** **Legitimate Interest (Article 6(1)(f))** — Organisation's legitimate interest in efficiently screening applicants and making fair hiring decisions.

**Conclusion:** **Lawful** — Contract basis is primary; legitimate interest is supplementary.

### 3.2 Legal Basis for Processing Special Category Data (GDPR Article 9)

**Special Category Processing Required Because:**
- System may process or infer ethnicity, disability, sexual orientation, religion, pregnancy

**Legal Basis to Consider:**

1. **Explicit Consent (Article 9(2)(a)):**
   - Obtain written consent from applicant for processing of special category data
   - Must be informed and freely given
   - Applicant can withdraw at any time
   - Recommended approach: Include consent request in online application form and privacy notice

2. **Employment Law (Article 9(2)(b)):**
   - UK employment law permits processing disability information for reasonable adjustments
   - Equality Act 2010 requires monitoring of protected characteristic hiring patterns
   - Permitted basis: Collect ethnicity, disability, etc. for equal opportunities monitoring (separate from scoring model)

3. **Legal Claim (Article 9(2)(f)):**
   - May process special categories if necessary to defend discrimination claims
   - Not primary basis; supplementary justification

**Recommended Approach:**
- **Primary basis:** Explicit consent for processing demographics in AI scoring model (if used)
- **Alternative/Supplementary:** Employment law basis for collection of equal opportunities data for fairness monitoring (separate from model)
- **Data separation:** Keep optional equal opportunities data separate from AI scoring model to avoid secondary use without consent

**Conclusion:** **Lawful if proper consent obtained and data separated from scoring model**

---

## 4. Assessment of Data Protection Risks

### Risk 1: Unlawful Processing Without Proper Consent

**Description:** If special category data processed without explicit consent or lawful basis, processing is unlawful.

**Likelihood:** Medium (if consent process not formalised or consent not obtained before data processing begins)

**Impact:** High (regulatory enforcement by ICO; fines up to 4% of global revenue; applicant claims; reputational damage)

**Residual Risk (With Mitigations):** Low — If consent process formally documented and verified

**Mitigations:**
- [ ] Formalise consent process: Include consent checkbox in online application form requesting permission to process personal data and special categories
- [ ] Consent request language must be clear and specific (e.g., "I consent to processing of my personal data, including optional information about protected characteristics, by an automated AI system for recruitment screening purposes")
- [ ] Obtain written evidence of consent (checkbox, digital signature, email confirmation)
- [ ] Provide privacy notice before requesting consent; include information about AI processing
- [ ] Offer applicants option to withdraw consent or request manual review
- [ ] Document consent management process

---

### Risk 2: Processing of Special Category Data Without Separate Legal Basis

**Description:** If equal opportunities data processed for fairness monitoring, but no separate legal basis documented, processing may be unlawful.

**Likelihood:** Medium (if data linkage between scoring model and equal opportunities forms not controlled)

**Impact:** High (regulatory concern; fairness monitoring not possible without demographic data)

**Residual Risk (With Mitigations):** Low — If separate legal basis documented (employment law) and data separation implemented

**Mitigations:**
- [ ] Document employment law legal basis for collection of equal opportunities data (Equality Act 2010 requires monitoring)
- [ ] Separate equal opportunities data from AI scoring model (different systems or databases; linked only by secure applicant ID for monitoring purposes)
- [ ] Implement access controls: Only authorised staff (AI Governance, Data Analytics) can access linked data for fairness monitoring; HR reviewers cannot see demographics
- [ ] Purge equal opportunities data separately on accelerated schedule (3 months post-decision vs. 6 months for application data) to minimise risk
- [ ] Obtain consent for separate processing if using linked data for fairness purposes

---

### Risk 3: Excessive Data Retention

**Description:** If applicant data retained longer than necessary, retention becomes unlawful (GDPR storage limitation principle).

**Likelihood:** Medium (if no formal retention policy or automated deletion procedures)

**Impact:** Medium (regulatory concern; data security risk increases with retention period)

**Residual Risk (With Mitigations):** Low — If retention policy formalised and automated deletion implemented

**Mitigations:**
- [ ] Formalise data retention policy: Unsuccessful applicants — 6 months; successful applicants — 2 years post-hire
- [ ] Implement automated deletion: Recruitment system configured to automatically delete records per retention schedule
- [ ] Manual audit: Quarterly audit to verify deletion working correctly
- [ ] Documentation: Maintain deletion logs; evidence of compliance with retention policy

---

### Risk 4: Secondary Use of Applicant Data Without Consent

**Description:** If vendor or cloud provider uses applicant data for purposes beyond recruitment (e.g., model improvement, analytics, research), secondary use occurs without consent.

**Likelihood:** Medium-High (if vendor agreements not carefully negotiated)

**Impact:** High (applicant privacy violation; regulatory enforcement; breach of applicant trust)

**Residual Risk (With Mitigations):** Low — If Data Processing Agreements (DPA) explicitly restrict use

**Mitigations:**
- [ ] Data Processing Agreement (DPA) with vendor or cloud provider must explicitly state: "Applicant data may be used ONLY for recruitment screening on behalf of Telleion Hospitals NHS Foundation Trust. Vendor may NOT use data for model improvement, analytics, research, or any other secondary purpose. Applicant data must be deleted per retention schedule."
- [ ] Audit vendor compliance: Include audit rights in contract; periodically verify vendor not using data for secondary purposes
- [ ] If vendor trains models on applicant data, obtain explicit consent from applicants; document consent in DPA
- [ ] Include data isolation requirements: Applicant data must be segregated from other customer data; no aggregation or analytics across customers

---

### Risk 5: Inadequate Data Security

**Description:** If personal data (including sensitive demographics) not adequately protected, risk of unauthorised access, breach, or data loss.

**Likelihood:** Medium (if security controls not implemented for recruitment system)

**Impact:** High (data breach notification required; regulatory enforcement; applicant harm)

**Residual Risk (With Mitigations):** Medium — If security controls implemented (but residual risk remains given sensitivity of data)

**Mitigations:**
- [ ] Encryption: Personal data encrypted at rest (database encryption) and in transit (TLS)
- [ ] Access controls: Only authorised HR staff and system administrators access applicant data; role-based access control implemented
- [ ] Audit logging: All access to applicant data logged; audit logs retained for 12 months
- [ ] Background checks: HR staff with access to applicant data subject to background checks
- [ ] Breach response: Incident response plan established; breach notification procedure (to ICO and applicants within 72 hours) documented
- [ ] Vendor security: If cloud-hosted, vendor must provide ISO 27001 certification or equivalent; conduct security assessment

---

### Risk 6: Applicant Rights Not Honoured

**Description:** If applicants cannot exercise GDPR rights (access, rectification, erasure, portability), processing is unfair and may be unlawful.

**Likelihood:** Medium (if procedures for handling rights requests not formalised)

**Impact:** Medium (applicant complaints; regulatory enforcement; reputational damage)

**Residual Risk (With Mitigations):** Low — If procedures documented and operationalised

**Mitigations:**
- [ ] Subject Access Request (SAR) procedure: Applicants can request copy of personal data; must respond within 30 days; provide data in portable format (CSV, JSON)
- [ ] Rectification procedure: Applicants can request correction of inaccurate data (e.g., wrong dates, qualifications)
- [ ] Erasure procedure: Applicants can request deletion of data (right to be forgotten); must comply per retention policy
- [ ] Portability procedure: Applicants can request data in portable format; must provide within 30 days
- [ ] Objection procedure: Applicants can object to processing (e.g., AI scoring); must consider objection and may suspend scoring
- [ ] Escalation: Rights requests sent to Data Protection Officer for handling; response tracked; compliance monitored

---

### Risk 7: Applicants Unaware of AI Processing

**Description:** If applicants not informed that AI used in screening, transparency principle violated; applicants cannot exercise rights.

**Likelihood:** High (if no privacy notice or disclosure provided before data collection)

**Impact:** Medium (transparency violation; applicant concerns; regulatory guidance non-compliance)

**Residual Risk (With Mitigations):** Low — If privacy notice provided before application submission

**Mitigations:**
- [ ] Privacy notice: Develop and publish comprehensive privacy notice covering: (a) What data collected, (b) AI screening used, (c) Legal basis for processing, (d) Retention period, (e) Rights available, (f) How to request explanation or human review, (g) Escalation for concerns
- [ ] Timing: Privacy notice must be provided BEFORE applicant submits CV; include in job application portal or email cover letter
- [ ] Language: Use clear, non-technical language; aim for accessibility (reading level 8–9)
- [ ] Transparency: Explain what AI does, how decisions made, what factors considered, what applicants can do if concerned
- [ ] Alternative: Applicants can request human review instead of AI screening; provide opt-out or alternative process

---

### Risk 8: Automated Decision-Making Without Human Review

**Description:** If AI score automatically results in rejection without HR review, applicant has no human oversight; violates GDPR Article 22 (right to human review of automated decisions with legal effect).

**Likelihood:** High (if system designed with auto-reject threshold)

**Impact:** Medium-High (transparency violation; applicant rights not honoured; regulatory guidance non-compliance)

**Residual Risk (With Mitigations):** Low — If human review procedure implemented (see Control 003 in Control Matrix)

**Mitigations:**
- [ ] No auto-rejection: All applicants must be reviewed by HR staff, regardless of score
- [ ] Human review procedure: HR reviews AI score and applicant data; exercises human judgment; makes final decision
- [ ] Documentation: HR documents review and decision; maintains rationale for approval or rejection
- [ ] Escalation: If applicant requests human review or challenges decision, provide expedited review by HR Manager
- [ ] Right to explanation: If applicant requests explanation of score, provide clear summary of factors contributing to score
- [ ] Right to object: Applicant can object to AI scoring; request manual human review; opt out of AI process

---

## 5. Risk Mitigation Summary

| Risk | Inherent Risk | Mitigations | Residual Risk |
|---|---|---|---|
| Unlawful processing without consent | High | Formalised consent process; documented evidence | Low |
| Special category data processing without legal basis | High | Separate legal basis (employment law); data separation | Low |
| Excessive data retention | Medium | Retention policy; automated deletion; audit | Low |
| Secondary use of applicant data | High | Data Processing Agreements; audit rights; explicit restrictions | Low |
| Inadequate data security | High | Encryption; access controls; audit logging; incident response | Medium |
| Applicant rights not honoured | Medium | SAR, rectification, erasure, portability procedures; escalation | Low |
| Applicants unaware of AI | High | Privacy notice; transparency; timing (before submission) | Low |
| Auto-reject without human review | High | No auto-reject; HR review procedure; right to explanation | Low |

---

## 6. Compliance Assessment

### 6.1 UK GDPR Compliance

**Assessment:** **COMPLIANT** — if mitigations implemented

**Key Requirements Met:**
- Lawful basis (contract + consent) ✓
- Special category processing with legal basis (employment law + consent) ✓
- Data minimisation (collect only data necessary) ✓
- Purpose limitation (use data only for recruitment) ✓
- Retention limitation (delete per policy) ✓
- Confidentiality and integrity (encryption, access controls) ✓
- Accountability (documented procedures, audit trails) ✓
- Rights (SAR, rectification, erasure, portability, objection procedures) ✓

### 6.2 Data Protection Act 2018 Compliance

**Assessment:** **COMPLIANT** — if mitigations implemented

**Key Requirements Met:**
- Processing principles (lawfulness, fairness, transparency) ✓
- Rights of applicants (access, rectification, erasure) ✓
- Appropriate safeguards (security, confidentiality) ✓
- Accountability (documentation, audit) ✓

### 6.3 Automated Decision-Making (GDPR Article 22) Compliance

**Assessment:** **COMPLIANT** — if human review procedure implemented

**Article 22 Requirement:** Applicants have right not to be subject to automated decision-making with legal effect without human review.

**Compliance Approach:**
- HR reviews all AI recommendations (no auto-reject)
- Applicants can request human review or explanation
- Final decision by HR (human, not automated)
- Documented procedure available to applicants

---

## 7. Data Processor/Vendor Assessments

### 7.1 If Vendor-Supplied AI Model

**Assessment Required:**
- [ ] Where is vendor hosted? (data location; jurisdiction)
- [ ] Does vendor use applicant data for model training? (if yes, explicit consent required)
- [ ] Can vendor access applicant data for any purpose other than recruitment? (if yes, restrict in DPA)
- [ ] Is vendor certified (ISO 27001, SOC 2)? (if no, conduct security assessment)
- [ ] Can applicant data be extracted if contract terminated? (exit strategy)
- [ ] Does vendor process data outside UK/EU? (if yes, adequate safeguards required; Standard Contractual Clauses)

**Data Processing Agreement Requirements:**
- Vendor acts as data processor (not controller)
- Data used ONLY for recruitment screening
- Applicant data not used for model improvement or secondary purposes
- Applicant data isolated from other customers' data
- Data must be deleted per retention schedule
- Trust has audit rights
- Subprocessor list provided; new subprocessors require consent
- Breach notification within 24 hours
- Data transfer outside UK must comply with UK GDPR Chapter V

---

### 7.2 If Cloud-Hosted (Azure, AWS, Google)

**Assessment Required:**
- [ ] Cloud provider's data protection practices (ISO 27001)
- [ ] Data location and jurisdiction
- [ ] Can cloud provider access data? (terms may permit access for support; should require encryption where cloud cannot access)
- [ ] Standard Contractual Clauses for international transfers (if data outside UK)
- [ ] Subprocessors permitted? (identify and audit)

**Data Processing Agreement Requirements:**
- Cloud provider acts as data processor
- Applicant data encrypted end-to-end if possible
- Cloud provider cannot access decrypted data
- Trust retains full control of encryption keys
- Data location specified and restricted
- Trust can request data deletion at any time

---

## 8. Applicant Communication Strategy

### Privacy Notice (To Be Provided Before Application Submission)

**Key Sections:**
1. **Who we are:** Telleion Hospitals NHS Foundation Trust, HR Department
2. **What data we collect:** Name, contact, employment history, qualifications, skills; optional: demographics, disability
3. **Why we collect it:** To screen applications and assess suitability for recruitment interview
4. **AI screening:** Your application will be reviewed by an automated AI system that scores your suitability. A human HR staff member will review the AI score and make the final decision about interviewing you.
5. **Legal basis:** Contract (necessary for recruitment); employment law (demographics for equal opportunities)
6. **Who can see your data:** HR staff, hiring managers, IT administrators; not shared with external organisations
7. **How long we keep it:** 6 months after recruitment decision; 2 years if you're hired
8. **Your rights:** You can request to see your data, correct errors, ask us to delete it, request explanation of AI score, or ask for human review instead of AI screening
9. **Concerns:** If you have concerns about how we're using your data, contact our Data Protection Officer (DPO contact)

### Opt-Out/Alternative Process

**Option 1 (Recommended):** Applicants can request human review instead of AI screening at any time before or after scoring.

**Option 2:** Applicants can request to be removed from recruitment database and data deleted (if data retention not legally required).

---

## 9. Ongoing Compliance Monitoring

### 9.1 DPIA Review Triggers

Review and update DPIA if:
- AI model changes (new version, retraining on different data)
- Data sources change (new data fields collected)
- Processing purposes change (secondary uses added)
- Vendor changes
- Data retention policy changes
- Data breach occurs
- Applicant complaints received about privacy or fairness
- Regulatory guidance changes

### 9.2 Compliance Audit Schedule

- **Initial audit:** Before pilot testing begins (verify mitigations implemented)
- **Quarterly audit:** During operation (check data retention compliance, security, access logs, breach response)
- **Annual audit:** Comprehensive compliance review; update DPIA if needed
- **Incident audits:** Upon data breach or applicant complaint; investigation and remediation

### 9.3 Responsibilities

| Role | Responsibility |
|---|---|
| **Data Protection Officer** | DPIA ownership; compliance monitoring; vendor oversight; breach response |
| **IT Security** | System security controls; encryption; access controls; audit logging |
| **HR Manager** | Data retention compliance; applicant rights handling; communication |
| **AI Governance** | Monitoring fairness implications of data processing; transparency to applicants |

---

## 10. Recommendations

### Before Proceeding to Pilot Testing

- [ ] **Complete consent process:** Design and test consent form; ensure applicants understand what they're consenting to
- [ ] **Publish privacy notice:** Make privacy notice available to applicants before CV submission
- [ ] **Data separation:** Implement technical controls to separate optional equal opportunities data from scoring model
- [ ] **Data Processing Agreements:** If using vendor or cloud provider, negotiate and execute Data Processing Agreements with privacy-protective terms
- [ ] **Audit logging:** Configure recruitment system to log all access to applicant data
- [ ] **Retention policy:** Document data retention and automated deletion procedures; test deletion process
- [ ] **Rights procedures:** Document procedures for handling subject access requests, rectification, erasure; train HR staff
- [ ] **Breach response:** Develop incident response plan; designate breach notification owner; test notification procedures
- [ ] **Security assessment:** Conduct security review of recruitment system and any vendor platforms; address deficiencies

### Approval

**Recommended Approval Authority:** Data Protection Officer + HR Director

**Approval Criteria:**
- All mitigations implemented (not planned)
- Consent process tested with sample applicants
- Privacy notice reviewed for clarity and completeness
- Data security controls verified
- DPA signed with vendor/cloud provider (if applicable)

---

## 11. Sign-Off

| Role | Name | Approval |
|---|---|---|
| **Data Protection Officer** | *[To be assigned]* | ⏳ Pending |
| **HR Director** | *[To be assigned]* | ⏳ Pending |
| **IT Security Lead** | *[To be assigned]* | ⏳ Pending |

---

## 12. Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | DPO | Draft for review |

---

**Document Classification:** Confidential — Data Protection  
**Retention Period:** 7 years  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11

---

## Appendices

**Appendix A:** Privacy Notice (Draft)  
**Appendix B:** Consent Form (Draft)  
**Appendix C:** Data Processing Agreement Template  
**Appendix D:** Subject Access Request Procedure  
**Appendix E:** Data Retention Policy
