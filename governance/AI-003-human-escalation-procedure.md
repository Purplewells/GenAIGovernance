---
title: AI-003 Generative AI Patient Service Assistant — Human Escalation Procedure
date: 2026-09-11
lifecycle_stage: Deployment & Operations
scope: Escalation routing, staff response, documentation, and monitoring for patient service assistant chatbot
decision_requested: Whether the escalation procedure is adequate for safe chatbot operation
owner: PALS Manager
approval_authority: Chief Medical Officer & Head of Operations
review_date: 2026-12-11
status: Draft for consultation
---

# AI-003 Generative AI Patient Service Assistant — Human Escalation Procedure

## Purpose

This procedure defines how the patient service assistant chatbot escalates complex, clinical, urgent, or safeguarding-related enquiries to appropriate human staff, and how those staff respond to ensure patient safety and satisfaction.

**Objective:**
- Ensure patient safety by escalating clinical and urgent cases promptly
- Provide clear routing rules so escalations reach the right team
- Establish response SLAs and documentation requirements
- Enable monitoring and continuous improvement of escalation process

---

## Escalation Triggers

### Category A: Immediate Clinical Escalation (to Clinician)

**Trigger Criteria:** Enquiry contains any of the following:

- **Acute symptoms or emergency language:** Chest pain, difficulty breathing, loss of consciousness, severe bleeding, severe allergic reaction, severe injury, thoughts of self-harm or suicide, acute psychiatric crisis
- **Red-flag symptoms:** Any language suggesting urgent medical need (e.g. "emergency," "can't wait," "severe," "urgent")
- **Clinical concern or diagnosis request:** Patient describes symptoms and asks for diagnosis, clinical advice, or interpretation of test results
- **Medication concern:** Patient reports adverse drug reaction, medication error, or asks for medication adjustment advice
- **Safeguarding concern:** Language suggesting abuse, neglect, exploitation, self-harm, neglect of child or vulnerable adult, coercion, trafficking
- **Uncertainty in chatbot:** Retrieval confidence below 70% AND enquiry involves clinical or patient-safety concern (detected by confidence scoring + keyword analysis)

**Routing:** → **Duty Clinician** (within 2 minutes)

**Response:** Clinician assesses urgency and either:
- Provides immediate clinical advice (if within scope and safe to do so)
- Directs patient to NHS 111 or A&E (if emergency)
- Refers to GP (if non-urgent but requires clinical assessment)
- Escalates to safeguarding team (if safeguarding concern)

---

### Category B: Urgent Non-Clinical Escalation (to PALS)

**Trigger Criteria:**

- **Urgent operational issue:** Patient reports urgent problem affecting care (e.g. "I can't get through to my clinic," "appointment system not working," "can't pay my bill and need urgent support")
- **Complex or multi-part enquiry:** Enquiry spans multiple topics or has conflicting information in chatbot responses
- **Patient dissatisfaction or complaint:** Patient expresses frustration with chatbot or prior experience; may be escalating to complaint
- **Accessibility need:** Patient indicates need for alternative format (braille, BSL interpreter, etc.)
- **Uncertain routing:** Enquiry doesn't clearly fit clinical or routine categories; human judgment needed

**Routing:** → **PALS Team** (within 15 minutes)

**Response:** PALS staff:
- Listen to full enquiry and context
- Escalate to clinician if clinical concern emerges
- Escalate to operations/service delivery if service issue
- Assist with accessibility needs
- Document complaint/feedback

---

### Category C: Routine Query with Escalation Needed (to PALS)

**Trigger Criteria:**

- **Chatbot cannot answer:** No matching information found in RAG system; enquiry out of scope
- **Chatbot confidence low:** Retrieval confidence 50–70% (uncertain but not clinical emergency)
- **Patient requests human agent:** Patient explicitly asks to speak with human staff
- **Potential follow-up needed:** Chatbot responds but enquiry may require personalised follow-up (e.g. appointment confirmation)

**Routing:** → **PALS Team** (within 30 minutes)

**Response:** PALS staff:
- Provide human-assisted answer (look up information, personalise response)
- Escalate to clinician if clinical need emerges
- Document response for future knowledge base improvement

---

### Category D: Safety-Net Escalation (to PALS Quality Team)

**Trigger Criteria:**

- **Anomalous enquiry:** Unusual language patterns, potential attack, or test case detected by content filters
- **Potential system misuse:** Chatbot used for unintended purpose or apparent testing/attack
- **Quality monitoring:** Routine sample of all responses for quality audit (e.g. 5% of all enquiries logged automatically)

**Routing:** → **PALS Quality Team** (within 24 hours)

**Response:** Quality team:
- Audits enquiry and response
- Flags any issues (inaccurate information, inappropriate response)
- Alerts Clinical Informatics Lead if knowledge base update needed
- Alerts Security if potential attack detected

---

## Escalation Routing Matrix

| Trigger Category | Content Type | Urgency | Route To | SLA | Priority |
|---|---|---|---|---|---|
| **Category A** | Clinical emergency or safeguarding | CRITICAL | Duty Clinician | 2 min | 🔴 CRITICAL |
| **Category A** | Clinical concern (non-emergency) | HIGH | Duty Clinician | 15 min | 🔴 HIGH |
| **Category B** | Urgent operational issue | HIGH | PALS (escalate to ops) | 15 min | 🔴 HIGH |
| **Category B** | Complex/multi-part enquiry | MEDIUM | PALS | 15 min | 🟡 MEDIUM |
| **Category B** | Patient complaint/dissatisfaction | MEDIUM | PALS (log as complaint) | 15 min | 🟡 MEDIUM |
| **Category C** | Routine query, no match found | LOW-MEDIUM | PALS | 30 min | 🟢 LOW |
| **Category C** | Patient requests human | MEDIUM | PALS | 15 min | 🟡 MEDIUM |
| **Category D** | System quality audit (sample) | NONE (audit) | Quality Team | 24 hours | ⚪ AUDIT |
| **Category D** | Potential attack/system misuse | MEDIUM | Quality Team → Security | 24 hours | 🟡 MEDIUM |

---

## Escalation Detection & Routing Logic

### Technical Implementation

**Detection Layer 1: Keyword/Rule-Based**
- Automated scanner checks enquiry text against keyword lists (symptoms, red flags, safeguarding language)
- If match found → Category A (clinical) or Category B (urgent)
- Rule-based detection is deterministic; always triggers for known keywords

**Detection Layer 2: Semantic/LLM Confidence**
- If no keyword match, LLM confidence score evaluated
- Confidence <50% → Category C (escalate due to uncertainty)
- Confidence 50–70% → Additional check: if clinical term present, escalate to PALS; if routine, may answer
- Confidence ≥70% → Answer directly (no escalation)

**Detection Layer 3: Output Filtering**
- Response generated; output filter checks for unexpected content (hallucination, harmful advice, potential security issue)
- If flagged → Escalate to PALS Quality Team (Category D)

**Detection Layer 4: Patient Request**
- If patient explicitly asks for human ("speak to someone," "I want to talk to a person"), flag for Category C escalation

**Detection Layer 5: Monitoring & Feedback**
- PALS/clinical staff can flag responses as requiring knowledge-base update
- Patient feedback indicating incorrect information triggers review

### Escalation Confidence Thresholds

| Threshold | Decision | Action |
|---|---|---|
| **Confidence >80%** | High confidence in answer | Respond directly; log escalation not needed |
| **Confidence 70–80%** | Good confidence | Respond, but flag for monitoring; escalate only if patient unhappy |
| **Confidence 50–70%** | Moderate confidence | Respond with caveats ("I'm not entirely sure..."), offer escalation option |
| **Confidence <50%** | Low confidence | Do not attempt to answer; escalate to PALS with "I'm not sure" message |

---

## Escalation Notification & Routing

### Alert Channels

| Priority | Channel | Who Receives | Notification Time |
|---|---|---|---|
| **CRITICAL (Category A emergency)** | SMS + phone call + in-system alert | Duty Clinician + PALS Manager | Immediate (1 min) |
| **HIGH (Category A/B)** | In-system alert + email | Assigned team (PALS, clinician, ops) | Immediate (2–5 min) |
| **MEDIUM (Category C routine)** | In-system queue | PALS team member | Queued; picked up within SLA |
| **AUDIT (Category D)** | Daily digest email | Quality Team Lead | Daily 9 AM email |

### Escalation Queue Management

**System maintains escalation queues:**

1. **CRITICAL Queue** (Duty Clinician) — 0 items maximum; must be responded to immediately
2. **HIGH Queue** (Clinician/PALS) — Monitored continuously; target <5 items waiting
3. **MEDIUM Queue** (PALS Routine) — Standard queue; items picked up in order within 30-min SLA
4. **AUDIT Queue** (Quality Team) — Daily batch review; no real-time urgency

**Queue monitoring dashboard:**
- Queue depth (items waiting)
- Average wait time per queue
- SLA compliance rate
- Oldest item in queue (flag if exceeds SLA)
- Escalation volume (trend analysis)

---

## Response Protocols

### Duty Clinician Response (Category A)

**Upon receiving escalation alert:**

1. **Acknowledge receipt** — Click "acknowledge" in alert to confirm; timestamp recorded
2. **Review enquiry** — Read full patient enquiry, symptoms, context
3. **Initial triage** — Determine urgency (emergency vs high vs routine)
4. **Respond:**
   - **Emergency (e.g., chest pain):** Direct to 999/A&E immediately; send message: "This sounds urgent. Please call 999 or go to your nearest A&E now."
   - **Clinical concern (non-emergency):** Provide advice if safe and within scope; OR direct to GP or NHS 111; OR escalate to safeguarding
   - **Safeguarding concern:** Alert safeguarding team immediately; do not continue chatbot conversation; provide patient with safeguarding helpline number
5. **Document** — Record clinical assessment, advice given, referral made, in patient record
6. **Close escalation** — Mark as resolved in system; log time-to-response

**Response SLA:** 2 minutes for CRITICAL; 15 minutes for HIGH

**Quality check:** Random sample of clinician responses audited quarterly for clinical safety and appropriateness

---

### PALS Team Response (Category B/C)

**Upon receiving escalation alert:**

1. **Acknowledge receipt** — Click "acknowledge"; timestamp recorded
2. **Review enquiry & context** — Full patient message, prior responses, category assigned
3. **Assess:**
   - Does this require clinical input? (If yes → escalate to clinician; do not delay)
   - Is this a complaint/feedback? (If yes → log as formal complaint)
   - Is this an access need? (If yes → facilitate accommodation)
   - Can PALS answer directly? (If yes → provide response)
4. **Respond:**
   - If routine enquiry: Look up information (booking system, policy, etc.); provide personalised response
   - If complex: Acknowledge; explain further information needed; offer call-back within X hours
   - If complaint: Log formally; provide complaint-process explanation; assign to complaints team
   - If access need: Acknowledge; facilitate accommodation (alternative format, interpreter, etc.)
5. **Document** — Record PALS response in system; document any actions taken or referrals made
6. **Follow-up** — If response requires action (e.g., clinician referral, accessibility accommodation), track to completion
7. **Close escalation** — Mark resolved; log time-to-response

**Response SLA:** 15 minutes for HIGH; 30 minutes for MEDIUM

**Quality check:** 10% random sample of PALS responses audited monthly for accuracy and tone; monthly team huddle to review challenging escalations

---

### Quality Team Review (Category D)

**Daily process (morning handover):**

1. **Review overnight escalations** — Pull Category D escalations from overnight (potential attacks, system errors)
2. **Audit sample** — Review 5% random sample of all enquiry-response pairs for quality
3. **Assess for:**
   - Hallucination or inaccurate information in response
   - Inappropriate tone or unclear messaging
   - Gaps in knowledge base (frequently escalated topics)
   - System performance issues (slow response, errors)
   - Security incidents (attack attempts, data anomalies)
4. **Action:**
   - If knowledge-base gap identified → Alert Clinical Informatics Lead; prepare content for addition
   - If security incident → Alert Security Lead; initiate incident response
   - If escalation trend (e.g., 10%+ escalation rate for specific topic) → Alert Clinical Informatics Lead; plan content improvement
5. **Communicate** — Morning team meeting reviews overnight findings; prioritises actions
6. **Document** — Quality review log maintained; trends tracked

---

## Staffing & Training Requirements

### Duty Clinician Role

**Staffing:** 
- Minimum 1 Duty Clinician on-call during chatbot operating hours (8 AM–8 PM initially)
- Clinician must be qualified to assess patient enquiries (registered medical or nursing professional)

**Responsibilities:**
- Monitor clinical escalation queue
- Respond to clinical escalations within SLA (2–15 min depending on priority)
- Escalate to 999/A&E as needed
- Refer to safeguarding team if concerns
- Document clinical assessment

**Training required:**
- Orientation to chatbot system and escalation procedure (2 hours)
- Clinical governance and escalation decision-making (in-service training, annually)
- Safeguarding awareness (mandatory annual training)
- System troubleshooting (who to call if technical issue)

---

### PALS Team Role

**Staffing:**
- Minimum 2–3 PALS staff members during operating hours
- Rotating on-call for after-hours urgent escalations (if system operates 24/7)

**Responsibilities:**
- Monitor PALS escalation queue
- Respond to enquiries within SLA (15–30 min)
- Escalate to clinician when clinical need emerges
- Log complaints and feedback
- Handle accessibility requests
- Document responses and actions

**Training required:**
- Chatbot system overview and escalation procedure (2 hours)
- Escalation decision-making and how to recognise clinical concerns (2 hours)
- Complaint-handling procedure and documentation (in-service)
- Patient communication and empathy (standard PALS training)
- System troubleshooting and who to contact

---

### Quality Team Role

**Staffing:**
- 1 Quality Lead (PALS or Clinical Governance)
- Shared responsibilities across PALS team for daily audit samples

**Responsibilities:**
- Daily review of Category D escalations and audit samples
- Trend analysis (escalation rates, knowledge-base gaps, performance issues)
- Escalate findings to Clinical Informatics Lead and Security Lead
- Monthly reporting to PALS Manager and AI Governance Committee
- Planning knowledge-base improvements and staff training needs

**Training required:**
- Chatbot system and RAG knowledge base (2 hours)
- Quality audit methodology (in-service)
- Clinical accuracy review (with clinical input)
- Security incident identification (with IT security)

---

## Documentation & Record-Keeping

### Escalation Log Entry

Every escalation must be documented with:

```
Escalation ID: [Auto-generated]
Timestamp: [Date/time escalation triggered]
Patient ID/NHS Number: [De-identified if required]
Escalation Category: [A/B/C/D]
Trigger: [Keyword/reason escalation triggered]
Original Enquiry: [Patient's message]
Initial Chatbot Response: [What chatbot was about to send, if any]
Escalation Route: [Clinician/PALS/Quality Team]
Assigned To: [Staff member name/role]
Response Time: [Minutes to respond]
Response Content: [Staff member's response to patient]
Outcome: [Resolved / Referred to clinic / Complaint logged / etc.]
Follow-up Actions: [Any actions required; owner; due date]
Resolved Date: [When escalation closed]
Quality Audit: [Passed/Failed; notes if any issues identified]
```

### Escalation Review (Monthly)

**PALS Manager** produces monthly report:
- Total escalations by category (A/B/C/D)
- Escalation rate (escalations as % of total enquiries)
- Average response time per category
- SLA compliance rate (% of escalations responded to within SLA)
- Trends (increasing/decreasing escalation volume, shifting patterns)
- Key findings (frequent topics, recurring issues, staff concerns)
- Recommended actions (knowledge-base improvements, process changes, training needs)

**Report recipients:** PALS Manager, Chief Medical Officer, AI Governance Committee

---

## Monitoring & Quality Assurance

### KPIs (Key Performance Indicators)

| KPI | Target | Monitoring | Action if Missed |
|---|---|---|---|
| **SLA Compliance (CRITICAL)** | 100% response within 2 min | Real-time dashboard | Page on-call clinician; escalate if repeated failure |
| **SLA Compliance (HIGH)** | 95% response within 15 min | Daily | Review staffing; add on-call support if capacity issue |
| **SLA Compliance (MEDIUM)** | 90% response within 30 min | Daily | Review PALS queue management; add resources if needed |
| **Escalation Rate** | <10% of enquiries | Weekly | If >10%, investigate causes; improve knowledge base or prompt logic |
| **Clinician Response Quality** | 100% clinically appropriate | Monthly audit (10% sample) | Provide feedback; additional training if needed |
| **PALS Response Quality** | 95%+ accuracy | Monthly audit (10% sample) | Feedback; retraining; knowledge-base improvement |
| **Patient Satisfaction (Escalated Cases)** | 80%+ rate escalation as helpful | Quarterly survey | Review escalation logic; improve staff response training |
| **Safeguarding Escalation Accuracy** | 100% safeguarding concerns escalated appropriately | Monthly review | Alert safeguarding lead; staff retraining if concerns missed |

### Audit & Review Cadence

| Activity | Frequency | Owner | Purpose |
|---|---|---|---|
| **Real-time SLA Monitoring** | Continuous | PALS Manager | Alerts if SLA breached; immediate intervention |
| **Daily Stand-up** | Daily | PALS + Clinician | Review overnight escalations; emerging patterns |
| **Weekly Metrics Review** | Weekly | PALS Manager + Quality Lead | Trend analysis; identify issues early |
| **Monthly Quality Audit** | Monthly | Quality Lead | 10% sample audit of responses; identify improvements |
| **Monthly Escalation Review** | Monthly | PALS Manager + Chief Medical Officer | Escalation trends; knowledge-base gaps; staff concerns |
| **Quarterly Staff Huddle** | Quarterly | PALS Manager + Clinician Lead | Case reviews; lessons learned; training needs |
| **Annual Procedure Review** | Annually | PALS Manager + AI Governance Committee | Assess escalation procedure effectiveness; update as needed |

---

## Exceptions & Edge Cases

### What if Clinician Not Available?

- **During hours (8 AM–8 PM):** Escalation routed to next available clinician in team (pool of 3–5 clinicians)
- **After hours:** If 24/7 operation planned, on-call clinician paged; if not 24/7, escalation queued and routed to duty clinician first thing next morning (escalation time-stamped; SLA may differ for after-hours)

### What if PALS Queue Backlog Exceeds SLA?

- **Monitoring:** Dashboard alerts if queue depth exceeds 5 items for >15 minutes
- **Escalation:** PALS Manager notified; decision to add resources or temporarily pause chatbot intake
- **Communication:** If necessary, chatbot messages patients: "High demand for assistance. Your enquiry is queued. Expected response time [X] minutes."

### What if Patient Escalates Complaint During Escalation?

- Escalation continues but complaint logged separately
- PALS staff provide both assistance (answer enquiry) and complaint support (formal logging, complaint-process explanation)

### What if Escalation Reveals Technical Issue?

- PALS staff escalate to IT Support; document technical issue
- Patient receives: "I've encountered a system issue. Our team will investigate and get back to you within 24 hours."

---

## Conditions for Operational Readiness

The escalation procedure can be activated only when:

1. **Staff trained:** Clinician, PALS, and Quality Team staff trained and competent; training records maintained.
2. **System tested:** Escalation routing tested end-to-end; SLA timers verified; alerts working.
3. **Staffing confirmed:** Minimum staffing levels (1 clinician, 2–3 PALS) confirmed and scheduled.
4. **Dashboard live:** Real-time escalation dashboard operational; alerts configured; staff can access.
5. **Procedures documented:** Staff have access to procedure; troubleshooting guide available; phone numbers posted.
6. **On-call arrangements formalised:** On-call clinician rota published; pager/phone system tested.

---

## Document Control

| Item | Value |
|---|---|
| Document ID | AI-003-ESCALATION-PROCEDURE-20260911 |
| Version | 1.0 (Draft) |
| Classification | Internal Operations |
| Owner | PALS Manager |
| Last Updated | 2026-09-11 |
| Next Review | 2026-12-11 or upon operational change |
