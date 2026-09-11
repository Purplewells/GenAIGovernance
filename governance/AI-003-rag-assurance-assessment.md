---
title: AI-003 Generative AI Patient Service Assistant — RAG Assurance Assessment
date: 2026-09-11
lifecycle_stage: Design & Pre-Deployment
scope: Retrieval-Augmented Generation (RAG) system design, approved information sources, information governance, and retrieval quality assurance
decision_requested: Whether the RAG system design and approved information sources are adequate to support patient-safe chatbot responses
owner: Clinical Informatics Lead
approval_authority: Chief Medical Officer & AI Governance Committee
review_date: 2026-12-11
status: Draft
---

# AI-003 Generative AI Patient Service Assistant — RAG Assurance Assessment

## Purpose

This assessment evaluates the design, implementation, and ongoing governance of the Retrieval-Augmented Generation (RAG) system that grounds the patient service assistant chatbot in verified, authoritative Trust information. RAG is the primary control mitigating hallucination and outdated-information risks.

**Objective:** Verify that:
1. RAG architecture is sound and retrieval quality is high
2. Approved information sources are accurate, current, and clinically appropriate
3. Information-governance processes ensure sources remain current
4. Retrieval logs are monitored for quality and misuse

**Outcome:** Recommendation on whether RAG system is ready for deployment.

---

## RAG System Architecture

### Design Overview

The chatbot uses a Retrieval-Augmented Generation (RAG) system:

1. **Information Ingestion:** Approved Trust information (FAQs, policies, procedures, standard responses) ingested into a vector database.
2. **Semantic Search:** Patient enquiry converted to embedding; similarity search performed against knowledge base.
3. **Retrieved Context:** Top-N most relevant documents retrieved and provided as context to the LLM.
4. **Grounded Response:** LLM generates response based on retrieved context, not general training data.
5. **Source Attribution:** Response includes reference to source (FAQ section, policy document).

**Architecture Benefits:**
- Responses grounded in verified Trust information
- Reduced hallucination compared to unrestricted LLM
- Source traceability (response can be audited against source)
- Controlled information (Trust controls what information is available)

### Design Assurance Objectives

| Objective | Assessment Method | Pass Criteria |
|---|---|---|
| **Retrieval Accuracy** | Test with 100 real patient enquiries; measure percentage where top-1 retrieved document is clinically correct. | ≥90% of enquiries retrieve correct source in top-1. |
| **Retrieval Completeness** | Test with known edge cases and less-common enquiry types; verify knowledge base covers expected query space. | ≥85% coverage of expected query types in top-3 results. |
| **Irrelevant Retrieval** | Measure false-positive rate (irrelevant documents retrieved). | <10% of retrievals return irrelevant information. |
| **No Retrieval (Zero-Shot)** | Identify enquiry types where no matching document exists; verify chatbot escalates rather than generates unreliable response. | 100% of zero-shot cases escalated to human staff. |
| **Vector Similarity Threshold** | Verify retrieval only returns documents above minimum similarity threshold; documents below threshold escalated. | Threshold optimised; escalation triggered when confidence insufficient. |

---

## Approved Information Sources

### Scope Definition

**What is included in RAG knowledge base:**
- Appointment booking and cancellation procedures
- Test-result retrieval and explanations
- Visiting arrangements and hours
- Medication information (general education; NOT personalised medication advice)
- Service descriptions and locations
- Facility information (accessibility, parking, amenities)
- Billing and payment questions
- Referral procedures
- Patient rights and complaints process
- Frequently asked health questions (general, non-diagnostic information)

**What is explicitly excluded:**
- Diagnosis or diagnostic advice
- Specific treatment recommendations
- Medication prescribing or adjustment advice
- Clinical decision-making
- Symptom interpretation or triage
- Emergency-care guidance (handled separately)

### Information Source Register

**Objective:** Maintain a complete, authoritative register of all approved sources ingested into the RAG system.

| Source ID | Source Description | Type | Owner | Date Approved | Last Review Date | Next Review Date | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| **FAQ-001** | Appointment booking FAQs | Document | Clinical Scheduling | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | 45 FAQs covering common appointment questions |
| **FAQ-002** | Test-result retrieval FAQs | Document | Pathology | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | Explains how to access results, what results mean (non-diagnostic) |
| **POL-001** | Visiting hours and arrangements policy | Policy | Patient Experience | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | Includes visiting hours, restrictions, accessibility |
| **POL-002** | Medication information sheet (general) | Document | Pharmacy | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | General medication education; NOT personalised advice |
| **PROC-001** | Complaints and patient rights procedure | Document | PALS | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | How patients can make complaints; access to records |
| **SERV-001** | Service descriptions and locations | Document | Communications | 2026-09-11 | 2026-09-11 | 2026-12-11 | Active | List of services, locations, how to access |

### Clinical Review of Sources

**Process:** Every information source must be clinically reviewed and approved before ingestion.

| Activity | Owner | Frequency | Success Criteria |
|---|---|---|---|
| **Initial Clinical Review** | Chief Medical Officer or delegated clinician | Before ingestion | CMO approval documented; source meets clinical accuracy and safety standards. |
| **Annual Clinical Review** | Chief Medical Officer | Annually (minimum) | Sources reviewed against current clinical guidance; any gaps or changes identified. |
| **Change-Triggered Review** | Chief Medical Officer | When guidance/policy changes | Sources updated within 5 business days of policy/guidance change. |
| **Audit Sample Review** | Quality/Assurance team | Quarterly | 10% random sample of sources audited for accuracy and relevance. |

---

## Information Governance & Maintenance

### Change Management

**Trigger:** Any change to Trust policy, procedure, system, or clinical guidance affecting chatbot information.

**Process:**
1. Change detected (e.g. new visiting-hours policy issued).
2. Appropriate staff notified (Clinical Informatics Lead, source owner).
3. Source reviewed and updated.
4. Updated version ingested into RAG system (version tracked).
5. Audit trail maintained (change log, date, reviewer, approval).

**Success Criteria:** All material changes identified and sources updated within 5 business days.

### Information Maintenance Schedule

**Quarterly Review (mandatory):**
- Review all sources for continued accuracy
- Check for policy or procedure changes affecting information
- Identify any outdated information
- Update sources as needed
- Document review outcomes

**High-Change Sources (more frequent review):**
- Appointment procedures: monthly review (due to frequent system updates)
- Visiting hours: monthly review (seasonal and policy changes)
- Service information: quarterly review

**Change Notification Integration:**
- Subscribe to notifications when key systems change (EPR, policies, procedures)
- Automated alerts trigger immediate information review
- Responsible staff respond within 2 business days

### Audit Trail & Version Control

**Requirements:**
- Every information source version-controlled (Git or equivalent)
- Change history maintained (who changed it, when, why)
- Approval dates and reviewer names recorded
- Deletion or archival of outdated sources tracked
- Retrieval logs capture which source version used for each response

---

## Retrieval Quality & Monitoring

### Retrieval Quality Metrics

| Metric | Definition | Target | Monitoring Frequency |
|---|---|---|---|
| **Retrieval Precision** | % of top-3 retrieved documents relevant to enquiry | ≥85% | Daily |
| **Retrieval Recall** | % of correct sources found anywhere in results (top-10) | ≥95% | Weekly |
| **Mean Reciprocal Rank (MRR)** | Average rank of correct document in results | ≥0.80 | Weekly |
| **Similarity Threshold Compliance** | % of responses from documents above minimum similarity threshold | 100% | Daily |
| **Zero-Shot Escalation Rate** | % of enquiries where no matching document found; escalated to staff | Monitored; target <5% | Weekly |

### Monitoring Dashboard

**Real-time dashboard** tracking:
- Retrieval precision (per enquiry type)
- Average relevance score
- Escalation rate (no match found)
- Response latency
- Source coverage (which FAQs/documents most used)
- Alert triggers (precision drops below 85%, escalation rate exceeds 10%, retrieval latency >2 seconds)

### Feedback Loop for Improvement

| Activity | Owner | Frequency | Action |
|---|---|---|---|
| **Patient Feedback Review** | PALS Manager | Weekly | Collect feedback on information accuracy; flag inaccuracies to Clinical Informatics Lead. |
| **Clinician Feedback** | Chief Medical Officer | Monthly | Collect feedback from clinicians on chatbot responses; identify misinformation or gaps. |
| **Metrics Review** | Clinical Informatics Lead | Weekly | Review dashboard metrics; identify precision/recall degradation; adjust retrieval thresholds if needed. |
| **Quarterly Improvement Sprint** | Lead Developer + Clinical Informatics Lead | Quarterly | Analyse low-performing enquiry types; improve retrieval (reindex, add sources, adjust similarity threshold). |

---

## Testing & Validation

### Pre-Deployment Testing

| Test | Objective | Method | Pass Criteria |
|---|---|---|---|
| **Retrieval Accuracy Test** | Verify RAG retrieves correct information for diverse enquiry types. | Run 200 real patient enquiries (pilot study); assess if top-1 document is clinically appropriate. | ≥90% accuracy. |
| **Coverage Test** | Verify knowledge base covers expected enquiry types. | Audit gap analysis; identify enquiry types with no matching source. | <5% of expected enquiries have no source. |
| **Clinical Accuracy Audit** | Verify retrieved documents contain clinically accurate information. | Clinician reviews 50 random retrieved documents for accuracy against current guidance. | 100% accuracy; 0 clinically false or unsafe information. |
| **Escalation Logic Test** | Verify chatbot escalates when no appropriate source found. | Test 50 enquiries outside knowledge base scope; verify 100% escalated. | 100% escalation for out-of-scope queries. |
| **Source Attribution Test** | Verify responses include source attribution. | Audit 100 responses; check if source cited. | 100% of responses include source reference. |

### Pilot Testing (Pre-Deployment)

- **Duration:** 2-week pilot with 100 real patients
- **Monitoring:** 100% of responses reviewed by PALS staff; feedback collected
- **Success Criteria:** 
  - Accuracy feedback: 95%+ of responses rated accurate by PALS staff
  - Escalation appropriateness: 95%+ of escalations appropriate (patient feedback + PALS review)
  - System stability: <1% system errors; retrieval latency <2 seconds

---

## Clinical Safety & Escalation

### Scenarios Requiring Escalation (Despite Retrieved Information)

Certain enquiries must be escalated to human staff even if RAG returns relevant information:

| Scenario | Reason | Action |
|---|---|---|
| **Patient expresses clinical concern** | Information service cannot diagnose; clinician review needed. | Escalate to PALS/clinician regardless of FAQ match. |
| **Enquiry involves personalised medical advice** | Information is generic; personalised advice requires clinician. | Escalate. |
| **Multiple conflicting interpretations** | Ambiguity in enquiry; human judgment needed. | Escalate. |
| **Urgent or emergency-sounding language** | Precautionary escalation for patient safety. | Escalate to clinician immediately. |
| **Safeguarding concern detected** | Abuse, neglect, self-harm, safeguarding risk. | Escalate to safeguarding team. |

---

## Document & Change Control

### Source Document Control

Each approved information source must be maintained in a controlled format:

**Requirements:**
- Version-controlled (Git, SharePoint, or equivalent)
- Approval sign-off (owner, reviewer, date)
- Clear effective date
- Change history / revision log
- Deprecation date (if being retired)
- Author and reviewer contact information

**Example metadata:**

```
Title: Appointment Booking FAQs
Version: 1.2
Effective Date: 2026-09-01
Last Reviewed: 2026-09-11
Next Review: 2026-12-11
Owner: Clinical Scheduling Team
Approved By: Chief Medical Officer
Changes in v1.2:
  - Updated appointment availability window (now 12 weeks vs 8 weeks)
  - Added cancellation fees information
Deprecates: v1.1 (2026-06-15)
```

### Ingestion & Versioning

- Each source version tagged with ingestion date
- RAG system tracks which source version used for each response
- Retrieval logs include source ID and version
- Historical audit trail maintained

---

## Assurance Sign-Off

### Pre-Deployment Assurance Gate

Before deployment, RAG system must be approved by:

| Role | Approval | Criteria |
|---|---|---|
| **Chief Medical Officer** | ✓ Clinical appropriateness | All sources reviewed and clinically approved; escalation logic sound. |
| **Clinical Informatics Lead** | ✓ Technical soundness | Retrieval accuracy ≥90%; escalation logic tested; monitoring in place. |
| **AI Governance Committee** | ✓ Governance adequacy | Information-governance process defined; maintenance schedule realistic; monitoring plan comprehensive. |

### Post-Deployment Assurance

**Ongoing monitoring:**
- Weekly retrieval-quality metrics review
- Monthly clinical review of sample responses
- Quarterly audit of information sources
- Annual comprehensive clinical and technical audit

**Re-assurance trigger:**
- Retrieval precision drops below 85% → Root-cause analysis; recovery plan required
- Patient feedback identifies inaccuracies → Immediate source review and correction
- New regulation/guidance issued → Sources reviewed within 5 business days
- Material system change (model, vector DB, threshold) → Re-validation testing required

---

## Conditions for Deployment

The RAG system can proceed to deployment only if:

1. **Pre-deployment testing completed:** Retrieval accuracy ≥90%; coverage ≥95%; all clinical safety tests passed.
2. **Pilot testing successful:** 95%+ of pilot responses rated accurate by PALS staff; escalations appropriate.
3. **Clinical approval:** Chief Medical Officer approves all sources as clinically appropriate and accurate.
4. **Monitoring in place:** Dashboard live; metrics baseline established; monitoring responsibility assigned.
5. **Change management process formalised:** Information maintenance schedule defined; staff trained; SLA established.
6. **Governance committee approval:** AI Governance Committee approves RAG system design and information governance.

---

## Risks & Mitigations (RAG-Specific)

| Risk | Inherent Risk | Mitigation | Residual Risk |
|---|---|---|---|
| Sources become outdated | Medium-High | Quarterly review schedule + change-notification integration | Low |
| Retrieval quality degrades over time | Medium | Continuous monitoring of retrieval metrics; weekly review | Low |
| New source added without clinical review | Medium | Approval gate: no source ingested without CMO approval | Low |
| Inappropriate source retrieved | Medium | Similarity threshold; escalation for uncertain matches | Low-Medium |
| RAG system misses known source | Medium | Quarterly coverage audit; improvement sprints | Low |

---

## Document Control

| Item | Value |
|---|---|
| Document ID | AI-003-RAG-ASSURANCE-20260911 |
| Version | 1.0 (Draft) |
| Classification | Internal Governance |
| Owner | Clinical Informatics Lead |
| Last Updated | 2026-09-11 |
| Next Review | 2026-12-11 or upon material change |

---

## Appendix: Approved Sources (Initial)

(Detailed source list to be populated with final approved sources before deployment)

- **FAQ-001:** Appointment Booking FAQs (45 items)
- **FAQ-002:** Test-Result Retrieval (30 items)
- **POL-001:** Visiting Hours & Arrangements
- **POL-002:** General Medication Information (Educational)
- **PROC-001:** Complaints & Patient Rights
- **SERV-001:** Service Descriptions & Locations
