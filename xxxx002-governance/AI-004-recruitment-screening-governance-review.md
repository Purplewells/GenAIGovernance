---
title: AI-004 AI Recruitment Screening — Governance Review & Approval Decision
date: 2026-09-11
lifecycle_stage: Idea/Use-Case Assessment → Pilot Testing
scope: AI-powered recruitment screening system for clinical and non-clinical roles at Telleion Hospitals NHS Foundation Trust
decision_requested: Whether the AI recruitment screening system can proceed to pilot testing with fairness validation, and under what controls, evidence, and accountability arrangements
owner: Head of AI Governance
approval_authority: AI Governance Committee and Executive Sponsorship (HR Director and Trust Board)
review_date: 2026-12-11
status: Ready for Governance Committee review
---

# AI-004 AI Recruitment Screening — Governance Review & Approval Decision

## Executive Summary

Telleion Hospitals NHS Foundation Trust proposes implementing an AI-powered recruitment screening system to improve hiring efficiency and reduce time-to-hire. The system would screen CVs and applications, extract candidate information, score applicants against job requirements, and recommend candidates for interview.

**Risk Rating:** HIGH (inherent) → MEDIUM (residual, with effective controls)

**Recommended Decision:** The system **can proceed to pilot testing** conditional on:

1. **Fairness validation** before any applicant data is processed
2. **Robust human oversight** with HR review of all AI recommendations and override capability
3. **Transparent decision-making** with explanation capability for applicants
4. **Continuous monitoring** for disparate impact by protected characteristic
5. **Data protection compliance** with UK GDPR and employment law
6. **Clear accountability** with named owners for each control

## Risk Summary

### Inherent Risks (Without Controls)

| Risk Area | Inherent Risk | Trigger |
|---|---|---|
| **Discrimination & Disparate Impact** | HIGH | Age bias, gender bias, ethnic bias, disability bias, indirect discrimination through proxy variables |
| **Data Protection & Privacy** | HIGH | Unauthorised processing, retention, sharing of applicant demographics |
| **Fairness & Transparency** | HIGH | Unexplainable scores, inability to challenge decisions, applicants unaware of AI use |
| **Human Oversight Failure** | MEDIUM-HIGH | Over-reliance on AI scores, reduced human judgment, applicants auto-rejected |
| **Model Accuracy & Bias** | MEDIUM-HIGH | Unknown model performance on underrepresented groups, false-negative rates affecting good candidates |
| **Vendor Lock-in & Exit Risk** | MEDIUM | Dependency on vendor model, limited audit rights, data extraction difficulty |

### Key Controls (Reducing Risk)

| Control | Effectiveness | Owner | Status |
|---|---|---|---|
| **Fairness assessment before pilot** | HIGH | Data Science & HR | Required before data processing |
| **Human review of all recommendations** | HIGH | HR Manager (Recruitment) | Operating procedure required |
| **Applicant explanation rights** | HIGH | AI Governance + Legal | Policy & system design required |
| **Bias monitoring dashboard** | HIGH | Data Analytics | Implement before go-live |
| **GDPR compliance & data minimisation** | HIGH | Data Protection Officer + HR | DPA & consent required |
| **Vendor audit rights & liability** | MEDIUM-HIGH | Procurement & Legal | Contract term requirement |
| **Regular fairness audit (quarterly)** | MEDIUM-HIGH | Independent audit team | Assurance plan required |
| **Escalation process for bias detection** | MEDIUM | AI Governance + HR Director | Incident response procedure |

### Residual Risk Assessment

| Risk | Residual Level | Tolerance | Status |
|---|---|---|---|
| Discrimination by protected characteristic | MEDIUM | MEDIUM | **ACCEPTABLE** with controls |
| Privacy breach / unauthorised use | MEDIUM | MEDIUM | **ACCEPTABLE** with GDPR compliance |
| Applicant harm from unfair scoring | MEDIUM | MEDIUM | **ACCEPTABLE** with human oversight |
| Model performance on underrepresented groups | MEDIUM | MEDIUM-HIGH | **ACCEPTABLE** with monitoring |
| Vendor liability for discriminatory outcomes | MEDIUM-HIGH | HIGH | **CONDITIONAL** — contract terms required |

---

## Governance Requirements

### Decision Authority & Accountability

| Role | Responsibility | Review Cadence |
|---|---|---|
| **HR Director** | Business case approval, human oversight procedures, disclosure to applicants | Before pilot launch |
| **AI Governance Committee** | Risk assessment review, control adequacy, fairness methodology sign-off | Before pilot launch |
| **Data Protection Officer** | Privacy compliance, GDPR legal basis, applicant consent, data retention | Before pilot launch |
| **Head of AI Governance** | Monitoring of fairness metrics, bias detection, escalation decisions, compliance | Monthly (pilot); Quarterly (post-launch) |
| **Data Scientist / ML Ops** | Model validation, fairness testing, bias monitoring | Ongoing |
| **Independent Audit Function** | Periodic fairness audit, control effectiveness testing, recommendations | Quarterly |

### Evidence Requirements for Approval

**Before Pilot Launch:**

- [x] Risk assessment completed and approved by AI Governance Committee
- [ ] Model fairness validation report (test data with demographic breakdown by protected characteristic)
- [ ] GDPR Data Protection Impact Assessment (DPIA) completed
- [ ] Applicant fairness disclosure and consent documentation
- [ ] HR procedures for human review and override of AI recommendations
- [ ] Monitoring plan with fairness metrics and alert thresholds
- [ ] Vendor assessment (if vendor-supplied model) including fairness commitments and audit rights
- [ ] Data retention and deletion procedures aligned with recruitment lifecycle
- [ ] Incident response procedure for bias detection or discrimination complaints

**Before Production Rollout:**

- [ ] Pilot testing complete (minimum 500 applications across job types)
- [ ] Fairness audit of pilot results (comparison of scores by demographic group)
- [ ] HR override rates and decision analysis by AI score vs. human judgment
- [ ] Evidence of no statistically significant disparate impact for protected characteristics
- [ ] Applicant feedback on AI use disclosure and fairness concerns
- [ ] Legal review confirming Equality Act 2010 and employment law compliance
- [ ] Board approval of residual risk and accountability arrangements

---

## Scope & Exclusions

### In Scope

- Screening of clinical roles (doctors, nurses, allied health)
- Screening of non-clinical roles (admin, support, facilities, IT, leadership)
- Initial selection process (CV to interview recommendation)
- All protected characteristics under Equality Act 2010 (age, sex, race/ethnicity, disability, sexual orientation, gender reassignment, religion/belief, pregnancy/maternity)

### Out of Scope

- Final hiring decision (remains with HR and line managers)
- Internal promotion or redeployment (separate HR process)
- Contractor or agency workforce (to be assessed separately)
- Post-hire employee performance or development decisions

---

## Lifecycle Stages & Gates

### Current Stage: Use-Case Assessment / Governance Review

**Entry criteria met:**
- Business case documented
- Processing flow defined
- Data requirements identified
- Governance questions articulated

**Approval criteria for pilot testing:**
- Risk assessment approved
- DPIA approved
- Fairness validation methodology approved
- Human oversight procedures formalised
- Monitoring plan approved

**Exit criteria for production deployment:**
- Pilot testing complete with fairness results
- No evidence of statistically significant disparate impact
- HR staff trained on AI limitations and bias
- Monitoring and incident response operational
- Board approval of residual risk and accountability

### Next Stage: Detailed Design & Fairness Validation

**Activities:**
- Fairness assessment of model (training data composition, performance by demographic group)
- GDPR compliance assessment and consent design
- HR procedure design for human review and override
- Monitoring dashboard design and data pipeline
- Vendor assessment (if applicable)

**Accountability:**
- Data Science Lead: Model fairness validation
- Data Protection Officer: GDPR compliance
- HR Manager: Procedures and applicant communication
- AI Governance Lead: Oversight and escalation

---

## Framework Alignment

### NIST AI Risk Management Framework (NIST AI RMF 1.0)

**GOVERN Function:**
- Establish governance structure, accountability, and decision rights
- Define risk tolerance and approval authority
- Ensure transparency and accountability to applicants and stakeholders

**MAP Function:**
- Define purpose, intended use, and scope of AI system
- Identify stakeholders, affected groups, and potential harms
- Document data sources, dependencies, and lifecycle boundaries
- Map fairness concerns, discrimination risks, and legal compliance requirements

**MEASURE Function:**
- Assess fairness and bias (training data, model performance, protected characteristics)
- Test for disparate impact and discrimination risk
- Validate human oversight effectiveness
- Monitor performance and bias in operation

**MANAGE Function:**
- Implement controls to mitigate discrimination and fairness risks
- Assign owners and accountability for each control
- Define incident response for bias detection
- Plan for model adjustment, restriction, or retirement if harm detected

### UK Legal & Regulatory Framework

**Equality Act 2010:** Prohibits direct and indirect discrimination based on protected characteristics. AI system must not discriminate in recruitment decisions.

**UK GDPR & Data Protection Act 2018:** Lawful basis for processing applicant data (contract/consent); special categories (demographics) require explicit consent or lawful basis; applicant rights to access, rectification, erasure, portability.

**Employment Rights Act 1996:** Protects applicants' right to fair and non-discriminatory treatment in recruitment.

**ICO AI and Data Protection Guidance:** Transparency, fairness, and accountability in algorithmic decision-making.

---

## Approval Sign-Off

| Role | Name | Date | Approval Status |
|---|---|---|---|
| Head of AI Governance | *[To be assigned]* | *[Pending review]* | ⏳ Awaiting submission |
| Data Protection Officer | *[To be assigned]* | *[Pending review]* | ⏳ Awaiting submission |
| HR Director | *[To be assigned]* | *[Pending review]* | ⏳ Awaiting submission |
| AI Governance Committee Chair | *[To be assigned]* | *[Pending review]* | ⏳ Awaiting submission |

---

## Appendices

- **Appendix A:** AI-004 Risk Assessment (separate document)
- **Appendix B:** AI-004 Control Matrix (separate document)
- **Appendix C:** AI-004 Fairness Assessment Framework (separate document)
- **Appendix D:** AI-004 Data Protection Impact Assessment (separate document)
- **Appendix E:** AI-004 Assurance Plan (separate document)
- **Appendix F:** AI-004 Vendor Assessment Template (if applicable)
- **Appendix G:** Use-Case Definition — AI-004 Recruitment Screening (001-use-cases folder)

---

## Review History

| Version | Date | Author | Status |
|---|---|---|---|
| 0.1 | 2026-09-11 | AI Governance | Draft for consultation |

---

**Document Classification:** Internal Use Only — AI Governance  
**Retention Period:** 7 years (employment records)  
**Last Updated:** 2026-09-11  
**Next Review:** 2026-12-11
