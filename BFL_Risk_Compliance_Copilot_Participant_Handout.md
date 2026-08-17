# Microsoft 365 Copilot — Participant Handout
## Risk & Compliance | Bajaj Finance Limited
### Half-Day Workshop | M365 Copilot for Risk & Compliance Teams

---

> **Technizer India** | In partnership with Bajaj Finance Limited
> Prompt Framework: **RTCFT** (Role · Task · Context · Format · Tone)

---

## 📋 SESSION OVERVIEW

| Parameter | Detail |
|---|---|
| Duration | 3.5 Hours (Half-Day) |
| Audience | Risk Analysts · Compliance Officers · Fraud Investigators · Portfolio Managers |
| Dataset | `BFL_Risk_Compliance_Copilot_Dataset.xlsx` |
| Policy Document | `RBI_Policy.pdf` — RBI (NBFC Internal Ombudsman) Directions, 2026 |
| Tools Covered | Copilot Chat · Copilot in Excel · Copilot in Outlook |
| Framework | RTCFT — applied across all 5 use cases |

---

## 🎯 WHAT YOU WILL BE ABLE TO DO AFTER THIS SESSION

1. Write high-quality Copilot prompts using the **RTCFT framework**
2. Use **Copilot in Excel** to analyse loan portfolios and surface DPD trends and risk signals
3. Use **Copilot Chat** to extract compliance obligations from real RBI regulatory documents
4. Use **Copilot Chat** to draft risk reports, gap analyses, and Board-level summaries
5. Use **Copilot in Outlook** to communicate risk findings with the right tone and urgency
6. Identify **your own top 3 use cases** where Copilot can save you time every week

---

## 🏗️ THE RTCFT FRAMEWORK

Every strong Copilot prompt has 5 elements. Together they remove ambiguity and give Copilot exactly what it needs to produce useful output.

| Element | What It Means | Example for Risk & Compliance |
|---|---|---|
| **R** — Role | Who should Copilot act as? | "You are a senior credit risk analyst at Bajaj Finance..." |
| **T** — Task | What specific action should it perform? | "...analyse the DPD bucket distribution and flag NPA accounts..." |
| **C** — Context | What data, background, or constraints apply? | "...Q1 FY26 portfolio data; Gross NPA threshold is 4.5%..." |
| **F** — Format | How should the output be structured? | "...output as a table with a 3-bullet executive summary..." |
| **T** — Tone | What style or register is needed? | "...formal, risk-aware tone suitable for MD review." |

### ❌ Weak Prompt vs ✅ Strong Prompt

| | Example |
|---|---|
| ❌ Weak | `"Summarise the loan data"` |
| ✅ Strong | `"You are a credit risk analyst at BFL. Analyse the attached loan portfolio for Q1 FY26 and identify all accounts in the 91+ DPD bucket. Show total outstanding and provision, and flag any accounts where provision coverage is below 65%. Table format. Formal tone for Credit Risk Committee."` |

---

## 📊 USE CASE 1 — Credit Portfolio Risk Analysis

**Tool:** Copilot in Excel + Copilot Chat
**Dataset Sheet:** `Loan Portfolio Risk`

### The Problem Today
Filtering DPD buckets, calculating provision totals, writing the executive summary — done manually across multiple tools, taking 45–60 minutes per cycle.

### With Copilot
The same analysis takes 4–5 minutes with a well-structured RTCFT prompt.

---

### PROMPT 1A — Portfolio Risk Summary

```
Role: You are a senior credit risk analyst at Bajaj Finance Limited.

Task: Analyse the loan portfolio data from the attached Excel file and prepare
a Portfolio Risk Summary for the Credit Risk Committee.

Context: The dataset covers 28 retail loans across Q1 FY2025-26. Key thresholds
— Gross NPA > 4.5% = breach; SMA accounts > 10% = early warning; Provision
Coverage Ratio should exceed 65%. Flag any loan where DPD is 91 or higher as
requiring immediate action.

Format:
1. Executive Summary (3 bullet points — key findings only)
2. DPD Bucket Distribution Table (Bucket | Count | Outstanding | Provision)
3. Top 3 At-Risk Accounts (Loan ID | DPD | Outstanding | Recommended Action)
4. Risk Committee Recommendations (numbered list, max 5 items)

Tone: Formal, precise, risk-aware. Use specific numbers from the data.
Suitable for MD-level review.
```

### PROMPT 1B — Copilot in Excel (Natural Language)

```
Highlight all loans in the 91-180 DPD and 180+ DPD buckets in red.
Add a new column called "Action Priority" — mark these accounts as "Immediate",
accounts in 61-90 DPD as "Urgent", and all others as "Monitor".
Show me the total outstanding and provision amount for Immediate priority accounts.
```

---

## 🔍 USE CASE 2 — Fraud Pattern Identification

**Tool:** Copilot Chat
**Dataset Sheet:** `Fraud Pattern Detection`

### The Problem Today
Reviewing 200–500 flagged transactions weekly, manually highlighting anomalies, and writing individual STR narratives — time-consuming and inconsistent.

### With Copilot
Copilot filters by anomaly score, identifies fraud typologies, and drafts an STR narrative shell in seconds.

---

### PROMPT 2A — Fraud Pattern Summary

```
Role: You are a fraud risk investigator at a large Indian NBFC.

Task: Review the transaction monitoring data and identify the top fraud risk
patterns for June 2025. Prioritise accounts where Anomaly Score > 0.75 AND
Investigation Status is "Under Investigation" or "Confirmed Fraud".

Context: Dataset contains 25 flagged transactions. Key indicators — geo-mismatch
(Location = "Unknown" or "Foreign IP"), velocity flags (column J ≠ "No Flag"),
high-value transactions (> ₹2,00,000) with suspicious merchants, multiple
attempts within 24 hours.

Format:
- Section 1: Top 5 High-Risk Transactions (TX ID | Customer | Amount |
  Anomaly Score | Pattern Type | Recommended Action)
- Section 2: Pattern Analysis — 3–4 bullets on emerging fraud typologies
- Section 3: STR Draft Template — 150-word FIU-compliant shell for the
  highest-risk transaction

Tone: Investigative, factual, legally defensible. Flag only what the data supports.
```

### PROMPT 2B — Fraud Alert Email (Copilot in Outlook)

```
Role: You are the Head of Fraud Risk at Bajaj Finance.

Task: Draft an urgent internal email to Branch Heads alerting them to a spike
in UPI fraud attempts in June 2025.

Context: 186 UPI fraud attempts this month vs threshold of 100. Three confirmed
fraud cases; 8 under investigation. Dominant patterns: geo-mismatch and
high-velocity transfers.

Format: Email — Subject line, brief opening, 3 key data points as bullets,
specific instructions for branch staff (2–3 action items), escalation contact.

Tone: Urgent but measured. Authoritative without causing panic.
```

---

## 📑 USE CASE 3 — Risk Reporting

**Tool:** Copilot Chat + Copilot in Outlook
**Dataset Sheet:** `Risk Reporting Dashboard`

### The Problem Today
Pulling KPIs from multiple systems, writing dashboard commentary, and drafting the monthly management report — typically a half-day task.

### With Copilot
Copilot reads the dashboard data and produces board-ready commentary with exception-based reporting in minutes.

---

### PROMPT 3A — Monthly Risk Commentary

```
Role: You are the Chief Risk Officer of Bajaj Finance Limited.

Task: Write the Monthly Risk Commentary for June 2025 for submission to the
Risk Management Committee (RMC).

Context: Dashboard shows — Gross NPA at 4.10% (threshold 4.5%, status: WATCH),
Collection Efficiency at 96.8% (threshold >96%, barely compliant), SMA-0
accounts at 9.1% (threshold <10%, status: WATCH). All other indicators
(Net NPA, PCR, CAR, Write-off Rate) are within acceptable bands. 4.5% of
portfolio is in the Loss category (180+ DPD) — highest in 3 quarters.

Format:
1. Opening — Key Risk Stance (2 sentences, traffic-light: Green/Amber/Red)
2. KPI Table (Indicator | Status | MoM Change | Commentary)
3. Watch Items — 2 items needing committee attention (1 paragraph each)
4. Forward-Looking Indicators — 2 emerging signals for next 30 days
5. Recommended Actions — numbered list for CRO sign-off

Tone: Board-level. Concise, data-backed. Every statement references a metric.
```

### PROMPT 3B — Exception Report for Zonal Heads

```
Role: You are a Risk Reporting Analyst at Bajaj Finance.

Task: Prepare an exception report highlighting only DPD buckets that have
breached or are approaching threshold — for distribution to Zonal Collection Heads.

Context: Flag buckets where portfolio share > 4% (currently 180+ DPD at 4.5%)
or where roll rates are increasing. Exclude Standard (0 DPD) accounts.

Format: One section per flagged bucket — Bucket | Outstanding (₹ Cr) |
% of Portfolio | Threshold | Action Recommended. End with a summary action
table for field teams.

Tone: Operational, direct, action-oriented. Simple language — no finance jargon.
```

---

## 📋 USE CASE 4 — Policy and Compliance Review

**Tool:** Copilot Chat (with PDF upload)
**Dataset Sheet:** `Policy Compliance Tracker`
**Policy Document:** `RBI_Policy.pdf` — RBI (NBFC Internal Ombudsman) Directions, 2026

### The Problem Today
Reading a 18-page RBI circular, extracting every obligation, mapping it to an internal owner, flagging deadlines, and updating the tracker — typically 2–3 hours of careful manual work.

### With Copilot
Upload the PDF directly to Copilot Chat. With the right RTCFT prompt, Copilot extracts all obligations in a structured table in under 60 seconds.

---

### About the RBI Document

**Document:** Reserve Bank of India (Non-Banking Financial Companies — Internal Ombudsman) Directions, 2026
**Reference:** RBI/CEPD/2025-26/384 | Issued: January 14, 2026 | Pages: 18

**Applies to BFL?** Yes — BFL is a Non-Deposit taking NBFC with assets above ₹5,000 crore with public customer interface. Fully applicable.

**Three clauses with hard deadline — June 30, 2026:**

| Clause | What BFL Must Do |
|---|---|
| 7(2) | Board to determine IO / Dy. IO headcount annually based on complaint volume |
| 14(2) | Deploy fully automated Complaint Management System with IO access |
| 14(4) | CMS must use exactly 3 categories: Fully Resolved / Partially Resolved / Wholly Rejected |

---

### PROMPT 4A — Obligation Extraction from RBI Direction

```
Role: You are a Senior Compliance Officer at Bajaj Finance Limited.

Task: Read the attached RBI Direction (Non-Banking Financial Companies —
Internal Ombudsman Directions, 2026) and extract ALL compliance obligations
that are mandatory for BFL.

Context: BFL is a Non-Deposit taking NBFC (NBFC-ND) with asset size exceeding
₹5,000 crore with a public customer interface — these Directions are fully
applicable to BFL. The Direction was issued on January 14, 2026. Three provisions
have a hard compliance deadline of June 30, 2026: Clauses 7(2), 14(2), and 14(4).
Ignore clauses applicable only to excluded categories (HFC, CIC, IDF-NBFC,
NBFC-IFC, NOFHC, Primary Dealers, MGC).

Format: Structured table —
- Clause Reference
- Area (e.g., IO Appointment / CMS / Board Oversight)
- Obligation Description (precise, actionable)
- Responsible Owner at BFL
- Compliance Timeline
- Priority: HIGH / MEDIUM

After the table, add a section: "IMMEDIATE ACTIONS — June 30, 2026 Deadline"
listing only the three deadline items with specific steps.

Tone: Formal regulatory language. Precise and actionable. Suitable for MD review.
```

### PROMPT 4B — Gap Analysis Against Existing Tracker

```
Role: You are the Head of Compliance at Bajaj Finance Limited.

Task: Compare the obligations in this attached RBI Direction with BFL's current
Policy Compliance Tracker and identify compliance gaps requiring immediate action.

Context: The Policy Compliance Tracker shows the Ombudsman Scheme row with
status "WATCH" — TAT breach noted in 3 cases, last updated April 2025. The new
RBI Direction (January 2026) introduces four requirements not yet in the tracker:
(a) Fully automated CMS with auto-escalation by June 30, 2026
(b) Mandatory 3-category CMS classification system by June 30, 2026
(c) Annual Board determination of IO/Dy.IO headcount by June 30, 2026
(d) New 23-point quarterly reporting format to RBI CEPD

Format:
1. Gap Analysis Table — Requirement | Current BFL Status | Gap (Yes/No) |
   Remediation Action | Owner | Target Date
2. Executive Summary — 3 bullet points for MD review
3. Tracker Update Recommendations — rows to be added or updated

Tone: Compliance advisory. Direct about gaps, solution-focused, no ambiguity.
```

### PROMPT 4C — Board Note Drafting

```
Role: You are the Company Secretary of Bajaj Finance Limited.

Task: Draft a Board Note for the next Board meeting seeking approval for BFL's
implementation plan for the RBI Internal Ombudsman Directions, 2026.

Context: The Direction (RBI/CEPD/2025-26/384) was issued January 14, 2026,
effective immediately. BFL already has an Internal Ombudsman from the 2023
Direction. Three provisions require Board action by June 30, 2026:
(1) Board determination of IO/Dy.IO headcount [Cl. 7(2)]
(2) Deployment of fully automated CMS with IO access [Cl. 14(2)]
(3) Implementation of 3-category complaint classification [Cl. 14(4)]
Additional ongoing obligations: 30-day complaint TAT, quarterly RBI CEPD
reporting, IO appointment notification within 5 working days.
Estimated CMS upgrade cost: ₹45–60 lakhs (to be confirmed by IT team).

Format: Formal Board Note —
1. Reference and Date
2. Subject
3. Regulatory Background (2 paragraphs)
4. Key Obligations Table (Clause | Requirement | Deadline | Owner)
5. Proposed Implementation Plan (milestone table with dates)
6. Budget Approval Sought
7. Recommendations (numbered, for Board resolution)

Tone: Formal board communication. Precise about obligations and deadlines.
```

### PROMPT 4D — Quarterly Compliance Status Report

```
Role: You are the Head of Compliance at Bajaj Finance Limited.

Task: Generate a Quarterly Compliance Status Report for Q1 FY2025-26 based
on the Policy Compliance Tracker data and the attached RBI Direction.

Context: The tracker covers 10 regulatory requirements including RBI KYC norms,
SARFAESI, PMLA/AML, DPDP Act, and IRAC norms. Current status — 7 COMPLIANT,
2 WATCH (Fair Practices Code, Ombudsman TAT), 1 AT RISK (DPDP Act consent
framework). The RBI Internal Ombudsman Directions 2026 require new rows to be
added to the tracker with June 30, 2026 deadlines.

Format:
1. Compliance Health Dashboard — traffic-light table
   (Policy | Regulatory Body | Status | Key Action)
2. At-Risk and Watch Items — root cause and remediation plan for each
3. New Obligations from RBI IO Directions 2026 — rows to add to tracker
4. Upcoming Review Calendar — next 30 days, policies due and owners
5. Board Certification Statement — 2-paragraph certification for MD signature

Tone: Formal regulatory language. Precise about deadlines and owners.
Board-appropriate.
```

---

## ⚠️ USE CASE 5 — Risk Monitoring & Early Warning Signals

**Tool:** Copilot Chat
**Dataset Sheet:** `Risk Monitoring Signals`

### The Problem Today
Checking 12–15 risk indicators weekly, writing narratives for each HIGH/MEDIUM signal, preparing the weekly risk brief for the CRO — a 2–3 hour manual task.

### With Copilot
Copilot scans all EWS signals, produces a prioritised CRO brief, and generates escalation memos for HIGH alerts automatically.

---

### PROMPT 5A — Early Warning Signal Brief for CRO

```
Role: You are the Risk Monitoring Head at Bajaj Finance.

Task: Prepare the Weekly Early Warning Signal (EWS) Brief for the CRO, covering
all HIGH and MEDIUM alerts from Q1 FY26 monitoring.

Context: The EWS dashboard covers 12 signals across Credit, Fraud, Liquidity,
Market, Operational, Cyber, Regulatory, and Reputation risk categories.
HIGH alerts (3): SMA-0 roll rate (12.4% vs 10% threshold), UPI fraud spike
(186 vs 100 threshold), Rural collection efficiency decline (93.1% vs 95%).
MEDIUM alerts: Restructured loan SMA migration, Repo rate NIM sensitivity,
Pending RBI audit observations, ALM gap.

Format:
1. Executive Flash (5 lines max) — overall risk posture this week
2. HIGH Alerts — Signal | Current Level | Threshold | Root Cause |
   Recommended Action | Owner | Deadline
3. MEDIUM Alerts — condensed table format
4. Watch for Next Week — 2 signals showing deteriorating trend

Tone: Crisp, intelligence-brief style. Every HIGH alert must have a specific
recommended action, owner, and deadline. No generic statements.
```

### PROMPT 5B — Escalation Email for Cyber Risk Alert

```
Role: You are the CISO of Bajaj Finance Limited.

Task: Draft an escalation email to the MD and CRO regarding a HIGH-rated
cyber risk alert — a spike in phishing attempts on customer-facing portals.

Context: EWS-008 shows 340 phishing attempts in June 2025 (threshold: <200).
Two attempts nearly succeeded (detected at login stage). Actions initiated:
2FA enforcement approved; staff phishing simulation scheduled next week.
Risk if breach occurs: data of ~50,000 customers exposed, triggering DPDP
Act regulatory action and reputational damage.

Format: Escalation email — Subject, situation summary (3 lines), risk impact
(bullets), actions taken (bullets), decision required from MD/CRO (2 specific
asks), proposed review meeting request.

Tone: Urgent, factual, solution-focused. Serious without causing alarm.
```

---

## 🎮 HANDS-ON LABS

### Lab 1 — Portfolio Triage (15 minutes)

1. Open `BFL_Risk_Compliance_Copilot_Dataset.xlsx` → `Loan Portfolio Risk` sheet
2. Open Copilot in Excel and type:

```
Identify all accounts with DPD > 60 days and Risk Rating C or D.
Show me the total outstanding amount for these accounts and calculate
what % of the total portfolio they represent.
Highlight these rows in red.
```

3. Then open Copilot Chat, attach the file, and run **Prompt 1A**
4. What did Copilot surface that you might have missed manually?

---

### Lab 2 — Build Your Own RTCFT Prompt (20 minutes)

Pick one scenario and write a full RTCFT prompt. Run it in Copilot Chat and share your output with the group.

| Card | Your Scenario |
|---|---|
| A | Present the fraud monitoring summary to your Zonal Head tomorrow |
| B | A new RBI circular on KYC has arrived — summarise its implications for your team |
| C | Collection efficiency in your zone has dropped — write a field action plan |
| D | Update the Board Compliance Certificate for Q1 |
| E | The CRO wants a 5-minute verbal brief — prepare talking points from EWS data |

**Your RTCFT Prompt:**

| Element | Your Draft |
|---|---|
| **Role** | |
| **Task** | |
| **Context** | |
| **Format** | |
| **Tone** | |

---

### Lab 3 — Before & After Email (10 minutes)

**Scenario:** Email your manager about 3 accounts that have crossed into NPA (91+ DPD) this month.

**Step 1:** Write the email yourself — 3 minutes, no Copilot.

**Step 2:** Run this in Copilot in Outlook:

```
Role: Risk Analyst at Bajaj Finance.
Task: Draft an internal email to my manager about 3 accounts crossing into
NPA (91+ DPD) status this month.
Context: Accounts — BFL20250009 (₹98,500 outstanding, 91 DPD),
BFL20250014 (₹1,85,000, 91 DPD), BFL20250021 (₹2,50,000, 180+ DPD).
SARFAESI notices being prepared for the 180+ DPD account. Provisioning
updated per IRAC norms.
Format: Short email — Subject, 2-line context, 3-bullet account summary,
next steps.
Tone: Factual, professional, no urgency exaggeration.
```

**Reflection:** How is the Copilot version different in structure, completeness, and tone?

---

## 💡 PROMPT CHEAT SHEET

Keep this as your desk reference after the session.

**Portfolio Risk Analysis**
> *"You are a credit risk analyst. Analyse the attached loan data. Identify accounts where DPD > 60 and outstanding > ₹1 lakh. Table sorted by risk priority. Formal tone for CRC."*

**Fraud Pattern Detection**
> *"You are a fraud investigator. From the transaction data, list all transactions with Anomaly Score > 0.75 and non-standard locations. Draft a 100-word FIU-compliant STR shell for the top case."*

**RBI Policy — Obligation Extraction**
> *"You are Head of Compliance at BFL. Read the attached RBI Direction and extract all obligations for BFL (NBFC-ND, assets ≥ ₹5,000 Cr). Table: Clause | Obligation | Owner | Deadline | Priority. Flag June 30, 2026 items separately."*

**Compliance Gap Analysis**
> *"You are Head of Compliance. Compare this RBI Direction against BFL's tracker. Table: Requirement | Current Status | Gap | Remediation | Owner | Target Date. End with 3-bullet MD summary."*

**Monthly Risk Commentary**
> *"You are CRO. Write the monthly risk commentary for RMC based on the attached dashboard. Gross NPA threshold 4.5%. Include KPI table, 2 watch items, forward-looking signals, and recommended actions. Board-level tone."*

**EWS Brief for CRO**
> *"You are Risk Monitoring Head. Write a weekly EWS brief covering only HIGH and MEDIUM alerts. Each HIGH alert: current level | threshold | root cause | action | owner | deadline. Intelligence-brief style."*

**Escalation Email**
> *"You are CISO. Draft an escalation email to MD and CRO about a cyber risk spike. Include: situation (3 lines), risk impact (bullets), actions taken (bullets), 2 specific decisions required. Urgent but measured."*

---

## 🚫 COMMON PROMPT MISTAKES — AND HOW TO FIX THEM

| Weak Prompt | Why It Fails | Fix It |
|---|---|---|
| `"Summarise the data"` | Too vague — Copilot doesn't know what matters | Add Role + specify which KPIs, which thresholds |
| `"Write a risk report"` | No structure — output is a free-form essay | Add Format with numbered sections |
| `"Be professional"` | Too generic — every output will feel the same | Specify the audience: "Board-level" / "field team" / "regulator" |
| `"Check compliance"` | No context on which regulation or threshold | Name the regulation, state the threshold and deadline |
| Copy Copilot output directly | Risk of errors if file wasn't attached or data was misread | Always verify numbers against the source file |

---

## 📝 MY ACTION PLAN

After this session, I will use Copilot for these 3 tasks in my daily work:

| # | Task | Tool I Will Use | Time I Expect to Save |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

---

*Technizer India | In partnership with Bajaj Finance Limited*
*Framework: RTCFT | Version 2.0 | June 2026*
*For participant use — not for external distribution*
