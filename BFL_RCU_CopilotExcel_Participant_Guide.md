# Copilot in Excel — Participant Exercise Guide
### Formulas & Pivot Tables for Risk Containment Unit (RCU)
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `BFL_RCU_Copilot_Demo.xlsx`

---

## Before You Begin

- Use **Copilot agent** to open the agent in the Copilot panel
- Add `BFL_RCU_Copilot_Demo.xlsx` from OneDrive
- Keep the Copilot panel open throughout all exercises
- The file has **25 rows of RCU case data** — one main sheet, no formula columns yet
- Columns Q–T are intentionally blank — you will fill these using Copilot

### Dataset Overview

| Column | Field | Description |
|--------|-------|-------------|
| A | Case ID | Unique case reference (RCU-001 to RCU-025) |
| B | Branch Name | Branch where the case was referred from |
| C | Branch Code | Short branch identifier |
| D | Zone | West / Central |
| E | Case Type | Pre-Disbursement Verification, Fraud Investigation, Document Verification, Address Verification, Employment Verification, Reference Check |
| F | Applicant Name | Name of the loan applicant under review |
| G | Product | Loan product — Personal Loan, Home Loan, Business Loan, Gold Loan, Two-Wheeler Loan |
| H | Loan Amount (₹) | Applied loan amount |
| I | Case Owner | RCU officer handling the case |
| J | Case Received Date | When the case was referred to RCU |
| K | Case Closed Date | When RCU completed its review (blank if still open) |
| L | TAT (Days) | Actual turnaround time in days |
| M | TAT Benchmark (Days) | Standard TAT for that case type |
| N | Customer Segment | Retail, SME, Corporate, HNI |
| O | Risk Level | Low, Medium, High, Critical |
| P | Status | Cleared, Pending, Escalated |
| **Q–T** | *(blank)* | **You will add these using Copilot** |

---

## Exercise 1 — Add a Formula Column: Breach Flag

### What This Does
Flags each case as **"Breach"** or **"On Time"** by comparing actual TAT against the benchmark. Cases still open are flagged **"Pending"**.

### Your Turn
Type into the Copilot panel:

```
In column Q, add a formula that checks whether each case breached
its TAT benchmark. Compare the TAT in column L against the
TAT Benchmark in column M.
- If column L is blank (case still open), return "Pending"
- If TAT (L) is greater than the Benchmark (M), return "Breach"
- Otherwise return "On Time"
Label the column "Breach Flag". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(L3="","Pending",IF(L3>M3,"Breach","On Time"))
```
Copilot will name the column, write the formula, and fill it down to Q27.

---

## Exercise 2 — Add a Formula Column: Risk Score Band

### What This Does
Converts the text **Risk Level** (column O) into a **numeric score band** — useful for sorting, filtering, and prioritisation in reports.

### Your Turn
Type into the Copilot panel:

```
In column R, add a formula that converts the Risk Level in column O
into a numeric score band:
- "Critical" = 4
- "High" = 3
- "Medium" = 2
- "Low" = 1
- Any other value = 0
Label the column "Risk Score Band". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(O3="Critical",4,IF(O3="High",3,IF(O3="Medium",2,IF(O3="Low",1,0))))
```
This numeric column makes it easy to sort cases from highest to lowest risk priority.

---

## Exercise 3 — Add a Formula Column: Pending Days

### What This Does
For cases still **open**, calculates how many days they have been waiting since they were received. Closed cases return 0.

### Your Turn
Type into the Copilot panel:

```
In column S, calculate the number of days each case has been
pending. If the case is already closed (column K has a date),
return 0. If the case is still open, return the number of days
since the case was received (column J) up to today.
Label the column "Pending Days". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(K3<>"",0,TODAY()-DATEVALUE(J3))
```
Cleared and Escalated cases with a closed date show 0. Open Pending cases show the number of days they have been waiting.

---

## Exercise 4 — Add a Formula Column: Resolution Category

### What This Does
Classifies each closed case by **how quickly it was resolved** relative to its TAT benchmark — giving RCU a performance quality label for every case.

### Your Turn
Type into the Copilot panel:

```
In column T, classify each RCU case into a resolution performance
category based on how the actual TAT (column L) compares to the
TAT Benchmark (column M):
- "Fast" if TAT is 50% or less of the Benchmark
- "Within TAT" if TAT is within the Benchmark
- "Moderate Breach" if TAT exceeds Benchmark by up to 50%
- "Critical Breach" if TAT exceeds Benchmark by more than 50%
- "Pending" if TAT is blank
Label the column "Resolution Category". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(L3="","Pending",IF(L3<=M3*0.5,"Fast",IF(L3<=M3,"Within TAT",IF(L3<=M3*1.5,"Moderate Breach","Critical Breach"))))
```

---

## Exercise 5 — Ask Copilot to Explain a Formula

### Your Turn
Copy the formula from cell **T3** and paste it into the Copilot panel:

```
Explain this formula to me in simple terms.
What does each part do?
```

### What Copilot Will Explain
> *"This formula first checks if the TAT in L3 is blank — if so, the case is still Pending. It then checks if the TAT is at most half the benchmark, meaning the RCU team was very Fast. Next it checks if TAT is within the full benchmark — that's Within TAT. If TAT went over the benchmark but not by more than 50%, it's a Moderate Breach. Anything beyond 150% of the benchmark is a Critical Breach. Each IF only runs when the previous condition wasn't true."*

---

## Exercise 6 — Create a Pivot Table: Cases by Case Type and Status

### What This Does
Shows which **types of RCU cases** have the most unresolved or escalated work — helping the team prioritise where to focus.

### Your Turn
Type into the Copilot panel:

```
Create a pivot table that shows the count of cases for each
Case Type, broken down by Status (Cleared, Pending, Escalated).
I want to see which case types have the most unresolved or
escalated work.
```

### What Copilot Will Produce
A new sheet with a Pivot Table:
- **Rows:** Case Type (Pre-Disbursement Verification, Fraud Investigation, Document Verification, Address Verification, Employment Verification, Reference Check)
- **Columns:** Status (Cleared, Pending, Escalated)
- **Values:** Count of Case ID

> **Discussion Point:** Which case type has the highest escalation rate? Why do you think Fraud Investigations take longer than other types?

---

## Exercise 7 — Create a Pivot Table: Average TAT by Case Owner

### What This Does
Shows which **RCU officers** are taking the longest to resolve cases — and which **case types** drive the highest TAT per officer.

### Your Turn
Type into the Copilot panel:

```
Now create a pivot table showing the average TAT in days for each
Case Owner, broken down by Case Type. I want to identify which
RCU officers or case types are taking the longest to close.
```

### What Copilot Will Produce
- **Rows:** Case Owner (Neha Joshi, Rahul Mehta, Priya Desai, Amit Kulkarni, Sunita Rao, Ravi Patil)
- **Columns:** Case Type
- **Values:** Average of TAT (Days)

> **Discussion Point:** Which officer has the highest average TAT on Fraud Investigations? What might explain Priya Desai's TAT on this case type?

---

## Exercise 8 — Bonus: Ask Copilot for Insights

### Your Turn
Type into the Copilot panel:

```
Look at the data in this sheet. Which branches have the most
Critical and High risk cases? Which case owners have the highest
proportion of Escalated cases? Summarise the top risk areas for
the RCU team in 3 bullet points.
```

### What to Expect
Copilot will scan the data and generate a natural-language insight summary — no formula needed. This shows how Copilot moves from **calculation** → **analysis** → **insight** within the same Excel session, which is the RCU team's daily workflow in compressed form.

---

## Quick Reference — Formulas You Built Today

| Column | Label | Formula Logic |
|--------|-------|---------------|
| Q | Breach Flag | Pending if open / Breach if TAT > Benchmark / On Time otherwise |
| R | Risk Score Band | Critical=4, High=3, Medium=2, Low=1 |
| S | Pending Days | 0 if closed / Days since received if still open |
| T | Resolution Category | Fast / Within TAT / Moderate Breach / Critical Breach / Pending |

---

*Bajaj Finance Limited | AI Academy — Risk Containment Unit (RCU) | Microsoft Copilot Training Programme*
*Technizer India*
