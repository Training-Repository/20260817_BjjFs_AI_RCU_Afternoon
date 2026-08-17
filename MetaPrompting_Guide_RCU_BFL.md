# Meta-Prompting Guide — Risk Containment Unit (RCU)
**Microsoft Copilot Training | Bajaj Finance Limited**

---

## What Is Meta-Prompting?

Instead of writing a prompt yourself, you ask Copilot to write the prompt for you — by telling it your role, your task, and what you need.

You are essentially saying:

> *"You are a prompt expert. You know how to talk to AI. Write me a prompt I can use for my actual RCU work."*

The output becomes your **reference prompt** — something you refine and reuse across case reviews, fraud reporting, verification workflows, risk escalations, and management communication.

---

## The Core Meta-Prompt Formula

```
Act as a Microsoft Copilot prompt expert.
I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].
Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

## Meta-Prompts for RCU Team — Bajaj Finance

Use these as your starting point. Copy, paste, and run in Copilot Chat. Use the output as your working prompt for your exercises.

---

### 1. Case Review and Prioritisation

```
Act as a Microsoft Copilot prompt expert.
I am an RCU Manager at Bajaj Finance Limited. I am responsible for managing the
end-to-end case pipeline for the Risk Containment Unit across branches in West and
Central zones. I maintain a Case Log in Excel with fields including: Case ID,
Branch Name, Zone, Case Type, Applicant Name, Product, Loan Amount, Case Owner,
Case Received Date, Case Closed Date, TAT (Days), TAT Benchmark (Days), Customer
Segment, Risk Level, Status, Breach Flag, Risk Score Band, Pending Days, and
Resolution Category.

I need to generate a daily case prioritisation dashboard that surfaces all open
Pending and Escalated cases, ranks them by Risk Level (Critical first) and Pending
Days (oldest first), and flags any case where TAT has already breached the benchmark.
I also need a case owner workload summary showing how many open cases each RCU
officer currently holds.

My audience is the RCU Head and Zonal Risk Managers who need a clear, action-oriented
view of what needs to be resolved today.

Write me a detailed, structured Copilot prompt I can use to produce this Case
Prioritisation Dashboard from my attached Excel file. The prompt should specify
format (priority case table: Case ID | Branch | Case Type | Applicant | Risk Level |
TAT Breach | Pending Days | Case Owner — sorted Critical first then by Pending Days
descending + case owner workload summary: Owner | Open Cases | Critical | High |
Oldest Open Case), tone (operational and urgent — for daily RCU team huddle), and
what to surface (Status = Pending or Escalated, Risk Level = Critical or High,
any case with Breach Flag = Breach).
```

---

### 2. Fraud Investigation Reporting

```
Act as a Microsoft Copilot prompt expert.
I am an RCU Fraud Analyst at Bajaj Finance Limited. I investigate suspected fraud
cases referred by branches before loan disbursement and prepare investigation
summaries for the Head of Risk. I maintain a Case Log in Excel where Fraud
Investigation cases are tagged under Case Type = "Fraud Investigation" with
additional fields including Risk Level, Loan Amount, Customer Segment, Status,
TAT (Days), and Resolution Category.

I need to produce a monthly Fraud Investigation Summary covering: total fraud cases
referred, breakdown by Risk Level (Critical, High, Medium), total loan exposure under
fraud review (sum of Loan Amount for open Fraud Investigation cases), escalated cases
requiring immediate RCU Head attention, and resolution performance (average TAT vs
benchmark for closed fraud cases). I also need to draft a 150-word summary paragraph
for the Head of Risk.

My audience is the Head of Risk and the Credit Risk Committee who need a concise,
data-grounded view of fraud case health and exposure for June FY2026-27.

Write me a structured Copilot prompt I can use to produce this Fraud Investigation
Report from my attached Case Log. The prompt should specify format (investigation
summary table: Risk Level | Count | Loan Exposure (₹) | Cleared | Pending |
Escalated | Avg TAT vs Benchmark + escalated cases flag table + 150-word summary
paragraph for Head of Risk), tone (formal, risk-aware, legally defensible —
suitable for Credit Risk Committee), and what to surface (Case Type = Fraud
Investigation, Status = Escalated or Pending, Risk Level = Critical or High,
Breach Flag = Breach).
```

---

### 3. Verification TAT Analysis

```
Act as a Microsoft Copilot prompt expert.
I am an RCU Operations Lead at Bajaj Finance Limited. I monitor turnaround time
performance across all verification case types including Pre-Disbursement Verification,
Document Verification, Address Verification, Employment Verification, and Reference
Checks. I maintain a Case Log in Excel with TAT (Days), TAT Benchmark (Days),
Breach Flag, and Resolution Category fields for each case.

I need to produce a monthly TAT Performance Report identifying which case types
and which case owners are consistently breaching their TAT benchmarks, calculating
average TAT vs benchmark by case type and by owner, and highlighting systemic
patterns — for example, whether a particular zone or case type is driving repeated
breaches. I also need 3 actionable recommendations for reducing TAT on the highest-
breach category.

My audience is the RCU Head and the Branch Operations team who need a data-led
performance view with specific, assignable corrective actions.

Write me a structured Copilot prompt I can use to produce this TAT Performance
Report from my attached Case Log. The prompt should specify format (TAT analysis
table by case type: Case Type | Avg TAT | Benchmark | Breach Count | Breach % |
Worst Case Owner + owner performance table: Owner | Cases | Avg TAT | Breach Count |
Critical Breach Count + 3 corrective action recommendations with suggested owner),
tone (analytical and improvement-focused — for internal RCU performance review),
and what to surface (Breach Flag = Breach, Resolution Category = Critical Breach,
Avg TAT exceeding Benchmark by more than 30%).
```

---

### 4. Risk Escalation Communication

```
Act as a Microsoft Copilot prompt expert.
I am the RCU Zonal Head for West Zone at Bajaj Finance Limited. I manage risk
escalations from RCU officers to the Head of Risk and Branch Heads when a case
meets escalation criteria — typically Risk Level = Critical, Status = Escalated,
or TAT has breached the benchmark on a high-value loan. I maintain a Case Log in
Excel and need to produce structured escalation communications for different audiences.

I need to draft three communication templates from the Case Log data:
(1) An escalation email to the Head of Risk for all Critical-risk Escalated cases,
    summarising case details, loan exposure, and what decision or intervention is needed.
(2) A branch advisory email to Branch Heads whose cases are in the Escalated or
    Critical category, asking for additional documents or information within 24 hours.
(3) A Copilot Chat prompt that I can reuse every week to identify which cases to
    escalate based on standard criteria.

My audience varies — Head of Risk needs a concise executive brief; Branch Heads
need specific, actionable instructions; the reusable prompt is for internal RCU use.

Write me structured Copilot prompts for each of these three communication needs,
drawing from the attached Case Log. Specify: format (escalation email — Subject,
summary table of escalated cases, risk exposure total, decisions required; branch
advisory — specific case IDs, documents needed, 24-hour deadline; reusable
weekly escalation prompt — criteria-based filter and output format), tone (escalation
email: formal and urgent; branch advisory: direct and instructional; reusable prompt:
operational and precise).
```

---

### 5. RCU Monthly MIS Report

```
Act as a Microsoft Copilot prompt expert.
I am the Head of RCU at Bajaj Finance Limited. I prepare monthly MIS (Management
Information System) reports for the Chief Risk Officer (CRO) and Board Risk
Committee. I maintain a Case Log in Excel with fields covering all 25 RCU cases
for June FY2026-27, including Case Type, Risk Level, Loan Amount, TAT performance,
Status, Zone, and Case Owner.

I need to produce the June MIS Report covering: total cases received and closed,
risk exposure breakdown (total loan value under Critical and High risk review),
TAT compliance rate (% of closed cases resolved within benchmark), zone-wise
performance comparison (West vs Central), fraud case summary, and top 3 risk
observations with recommended Board-level actions.

My audience is the CRO and the Board Risk Committee who need a concise, data-led
executive summary — not raw case lists.

Write me a structured Copilot prompt I can use to produce this Monthly RCU MIS
Report from my attached Case Log. The prompt should specify format (executive
summary: 4–5 lines + risk exposure table: Risk Level | Count | Total Loan Value |
% of Portfolio Under Review + TAT compliance scorecard + zone performance comparison
table + fraud summary + 3 Board-level observations and recommendations), tone
(Board-ready, precise, data-grounded — CRO presentation standard, 500 words
maximum), and what to surface (Critical and High risk cases, Escalated status,
TAT compliance rate below 80%, zone performance gaps of more than 15%).
```

---

## Still Confused? Run This.

If the prompt Copilot wrote doesn't feel right — too generic, wrong format, wrong tone — don't rewrite it yourself. Use this follow-up prompt instead:

```
The prompt you wrote is a good start, but I need you to adjust it.
Here is what I want to change:

- [Describe what felt off — e.g., "the format doesn't match what our
  CRO expects in a monthly RCU MIS report"]
- [Describe what's missing — e.g., "it doesn't tell Copilot to flag
  Critical-risk cases where no action has been taken in 48 hours"]
- [Describe the tone issue — e.g., "it sounds too casual for a Board
  Risk Committee presentation"]

Please rewrite the prompt with these corrections.
Keep the same structure (Role / Task / Context / Format / Tone)
but fix the parts I've described.
```

---

## What to Do With the Output

Once Copilot gives you a well-structured prompt:

1. **Read it** — does it reflect your actual RCU role and the work you handle at BFL?
2. **Replace the placeholders** — swap generic text with your real reporting period, zone, case type, or risk threshold.
3. **Run it** — use it on the exercise dataset (`BFL_RCU_Copilot_Demo.xlsx`) provided during training.
4. **Save it** — this is your reusable reference prompt for that RCU task type.

---

## 📋 RCU Team Quick Reference

| Use Case | Dataset Fields Copilot Will Use | Key Output |
|---|---|---|
| Case Review & Prioritisation | Status, Risk Level, Pending Days, Breach Flag, Case Owner | Daily prioritisation dashboard + owner workload |
| Fraud Investigation Reporting | Case Type = Fraud Investigation, Risk Level, Loan Amount, Status, TAT | Monthly fraud summary + Head of Risk paragraph |
| Verification TAT Analysis | TAT (Days), TAT Benchmark, Breach Flag, Resolution Category | TAT performance table + corrective actions |
| Risk Escalation Communication | Status = Escalated, Risk Level = Critical, Loan Amount | Escalation email + branch advisory + reusable prompt |
| Monthly MIS Report | All fields — full case log | CRO/Board-ready MIS report |

---

*Bajaj Finance Limited | AI Academy — Risk Containment Unit (RCU) | Microsoft Copilot Training Programme*
*Technizer India*
