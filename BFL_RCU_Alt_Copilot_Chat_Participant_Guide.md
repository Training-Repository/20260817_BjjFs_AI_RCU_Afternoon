# Copilot Chat for Excel — Participant Exercise Guide
### Formulas & Pivot Tables for Risk Containment Unit (RCU)
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `BFL_RCU_Copilot_Demo.xlsx`
**Mode:** Copilot Chat (no Microsoft 365 Copilot licence required)

---

## Before You Begin

### What You Need
- **Excel** open with `BFL_RCU_Copilot_Demo.xlsx`
- **Copilot Chat** open in a second window — either:
  - `https://copilot.cloud.microsoft` (M365 Copilot Chat, work account), or
  - The **Copilot** button in Microsoft Edge, or
  - The Copilot app in Windows / Teams
- Both windows side by side (**Win + ←** and **Win + →**) — you will be switching constantly

### How This Session Works
Copilot Chat is **not connected to your workbook.** It cannot insert formulas, build pivot tables, or change anything in Excel. It can *write* everything for you — you paste it in.

Every exercise follows the same **two-step rhythm**:

| Step | Where | What You Do |
|------|-------|-------------|
| **1. Ask** | Copilot Chat | Paste the prompt, get the formula or the steps |
| **2. Apply** | Excel | Paste into the cell, press Enter, fill down |

> **Key habit:** Because Chat cannot see your file, **you** must describe the file. That is the entire skill this session teaches — and it is the same skill that makes every other AI tool work well.

**The sheet:** headers are in **row 2**; data runs **row 3 to row 27** (25 cases). Real data occupies columns **A–P**; columns **Q–T are empty** — you will fill these using Copilot Chat.

---

## Step 0 — Set the Context (do this once)

Open Copilot Chat and paste this **first**. Everything after it can be short, because Chat now knows your sheet.

```
I'm working in Excel on an RCU (Risk Containment Unit) case log. You can't
see the file, so here is the layout:

Headers are in row 2. Data runs from row 3 to row 27 (25 case rows).

A  Case ID              (text, e.g. RCU-001)
B  Branch Name          (text)
C  Branch Code          (text)
D  Zone                 (West / Central)
E  Case Type            (Pre-Disbursement Verification, Fraud Investigation,
                         Document Verification, Address Verification,
                         Employment Verification, Reference Check)
F  Applicant Name       (text)
G  Product              (Personal Loan, Home Loan, Business Loan, Gold Loan,
                         Two-Wheeler Loan)
H  Loan Amount (₹)      (number)
I  Case Owner           (text)
J  Case Received Date   (date)
K  Case Closed Date     (date, blank if the case is still open)
L  TAT (Days)           (number, blank if still open)
M  TAT Benchmark (Days) (number)
N  Customer Segment     (Retail, SME, Corporate, HNI)
O  Risk Level           (Low, Medium, High, Critical)
P  Status               (Cleared, Pending, Escalated)
Q to T are empty — I'll be adding calculated columns there.

For the rest of this conversation: when I ask for a formula, give me the
formula for the FIRST data row (row 3), ready to paste and fill down.
Give me the formula on its own line, then a one-line explanation. No long
preamble.
```

> **Trainer note:** This single block is the difference between five sharp answers and five vague ones. Keep it visible on screen — participants will refer back to it.

---

## Exercise 1 — Breach Flag (Column Q)

**What this does:** Flags each case as **"Breach"** or **"On Time"** by comparing actual TAT against the benchmark. Cases still open are flagged **"Pending"**.

### Step 1 — Ask (Copilot Chat)
```
Write a formula for cell Q3 that checks whether a case breached its TAT
benchmark. Compare TAT (column L) against the TAT Benchmark (column M):
- "Breach" if TAT is greater than the Benchmark
- "On Time" otherwise
- "Pending" if TAT is blank (case still open)
Handle the blank check first.
```
**Expected output:**
```excel
=IF(L3="","Pending",IF(L3>M3,"Breach","On Time"))
```

### Step 2 — Apply (Excel)
1. Click **Q2** → type `Breach Flag` → Enter
2. Click **Q3** → paste the formula → Enter
3. Select **Q3**, double-click the fill handle (bottom-right corner) to fill down to **Q27** *(or select Q3:Q27 and press **Ctrl + D**)*

> **Try this:** Ask Copilot Chat — *"What happens if I don't check for the blank first?"* It will explain that a blank cell counts as 0, so every open case would wrongly read "On Time". This is the single most common formula bug in real RCU trackers.

---

## Exercise 2 — Risk Score Band (Column R)

**What this does:** Converts the text **Risk Level** (column O) into a **numeric score band** — useful for sorting, filtering, and prioritisation in reports.

### Step 1 — Ask (Copilot Chat)
```
Write a formula for cell R3 that converts the Risk Level in column O into a
numeric score band:
- "Critical" = 4
- "High" = 3
- "Medium" = 2
- "Low" = 1
- any other value = 0
```
**Expected output:**
```excel
=IF(O3="Critical",4,IF(O3="High",3,IF(O3="Medium",2,IF(O3="Low",1,0))))
```

### Step 2 — Apply (Excel)
1. **R2** → `Risk Score Band`
2. **R3** → paste → Enter → fill down to **R27**

> **Try this:** Ask Chat — *"What does this return if the Risk Level cell is blank or misspelt?"* It will point out the final `0` catch-all — so a stray "Hgh" silently scores 0 and quietly drops down any risk-sorted report. Worth knowing before you sort on it.

> **Bonus prompt:** *"Rewrite this using IFS, and again using SWITCH."* Three ways to write the same mapping — compare which reads cleanest for a text-to-number lookup.

---

## Exercise 3 — Pending Days (Column S)

**What this does:** For cases still **open**, calculates how many days they have been waiting since they were received. Closed cases return 0.

### Step 1 — Ask (Copilot Chat)
```
Write a formula for cell S3 that shows how many days a case has been
pending. If the case has closed (column K has a date), return 0. If it is
still open, return the number of days from Case Received Date (column J) to
today.
```
**Expected output:**
```excel
=IF(K3<>"",0,TODAY()-J3)
```

### Step 2 — Apply (Excel)
1. **S2** → `Pending Days`
2. **S3** → paste → Enter → fill down to **S27**

> **This one breaks — on purpose.** In this training file the dates in column J are stored as **text**, so the formula above returns **#VALUE!**. That's the lesson. Go back to Chat and ask:
> ```
> My Case Received Date in column J is stored as text, not a real date.
> Rewrite the S3 formula to handle that.
> ```
> You'll get `=IF(K3<>"",0,TODAY()-DATEVALUE(J3))`. Paste it, fill down — now cleared/escalated cases with a closed date show 0 and open cases show a real day count. If a result shows as a **date** instead of a number, select **S3:S27 → Home → Number Format → Number**.

---

## Exercise 4 — Resolution Category (Column T)

**What this does:** Classifies each closed case by **how quickly it was resolved** relative to its TAT benchmark — giving RCU a performance quality label for every case.

### Step 1 — Ask (Copilot Chat)
```
Write a formula for cell T3 that classifies each RCU case by how the actual
TAT (column L) compares to the TAT Benchmark (column M):
- "Fast" if TAT is 50% or less of the Benchmark
- "Within TAT" if it is within the Benchmark
- "Moderate Breach" if it exceeds the Benchmark by up to 50%
- "Critical Breach" if it exceeds the Benchmark by more than 50%
- "Pending" if TAT is blank
```
**Expected output:**
```excel
=IF(L3="","Pending",IF(L3<=M3*0.5,"Fast",IF(L3<=M3,"Within TAT",IF(L3<=M3*1.5,"Moderate Breach","Critical Breach"))))
```

### Step 2 — Apply (Excel)
1. **T2** → `Resolution Category`
2. **T3** → paste → Enter → fill down to **T27**

> **Bonus prompt:** *"Rewrite this using IFS instead of nested IFs."* Compare the two — which one would you rather hand a colleague to maintain?

---

## Exercise 5 — Ask Copilot Chat to Explain a Formula

### Your Turn
Copy the formula from cell **T3** in Excel and paste it into Copilot Chat with:
```
Explain this formula to me in simple terms. What does each part do, and in
what order does it evaluate?

=IF(L3="","Pending",IF(L3<=M3*0.5,"Fast",IF(L3<=M3,"Within TAT",IF(L3<=M3*1.5,"Moderate Breach","Critical Breach"))))
```
### What Copilot Chat Will Explain
> *"It reads the TAT in L3 top down. Blank → still Pending. At most half the benchmark → Fast. Within the full benchmark → Within TAT. Over benchmark but not by more than 50% → Moderate Breach. Beyond 150% of benchmark → Critical Breach. Each IF only runs when the one before it was false, so the tightest band is tested first."*

> **This works on any formula.** Take the ugliest formula from your own live tracker, paste it in, and ask the same question. This is the single highest-value habit from the whole session.

---

## Exercise 6 — Pivot Table: Cases by Case Type and Status

**What this does:** Shows which **types of RCU cases** have the most unresolved or escalated work — helping the team prioritise where to focus.

Copilot Chat **cannot build the pivot for you.** It will give you the click-path — you build it. Two minutes, and you will never need to look it up again.

### Step 1 — Ask (Copilot Chat)
```
Give me step-by-step instructions to build a PivotTable in Excel from the
range A2:T27 on this sheet, showing the count of cases for each Case Type,
broken down by Status. I want to see which case types have the most
unresolved or escalated work. Tell me exactly which field goes into which
area.
```
### Step 2 — Apply (Excel)
1. Click any cell inside your data
2. **Insert → PivotTable → From Table/Range** → confirm the range → **New Worksheet** → OK
3. Drag fields into the areas:
   - **Rows:** Case Type
   - **Columns:** Status
   - **Values:** Case ID *(defaults to Count — correct here)*

### No-Pivot Alternative
```
Instead of a PivotTable, give me a COUNTIFS formula that counts cases for a
given Case Type and Status, so I can build a small summary grid manually.
```
`=COUNTIFS($E$3:$E$27,$V3,$P$3:$P$27,W$2)` — Case Types down the side, Statuses across the top.

> **Discussion Point:** Which case type has the highest escalation rate? Why do you think Fraud Investigations take longer than other types?

---

## Exercise 7 — Pivot Table: Average TAT by Case Owner

**What this does:** Shows which **RCU officers** are taking the longest to resolve cases — and which **case types** drive the highest TAT per officer.

### Step 1 — Ask (Copilot Chat)
```
Now give me the steps for a second PivotTable showing the average TAT in
days for each Case Owner, broken down by Case Type. Include how to change
the value field from Sum to Average, and how to round the displayed numbers
to one decimal place.
```
### Step 2 — Apply (Excel)
1. **Insert → PivotTable** again → New Worksheet
2. **Rows:** Case Owner | **Columns:** Case Type | **Values:** TAT (Days)
3. Click the value field → **Value Field Settings → Average**
4. Same dialog → **Number Format → Number → 1 decimal place**

### No-Pivot Alternative
```
Give me an AVERAGEIFS formula for the average TAT for a given Case Owner and
Case Type.
```
`=AVERAGEIFS($L$3:$L$27,$I$3:$I$27,$V3,$E$3:$E$27,W$2)` — a quick grid without a pivot.

> **Discussion Point:** Which officer has the highest average TAT on Fraud Investigations? What might explain Priya Desai's TAT on this case type?

---

## Exercise 8 — Bonus: Get Insights from Copilot Chat

Chat cannot read your workbook — so **you bring the data to Chat.**

### Step 1 — Copy from Excel
Select **A2:T27** (headers plus all 25 rows) and press **Ctrl + C**.

### Step 2 — Ask (Copilot Chat)
Paste the data directly into the chat box, then add underneath:
```
Above is my full RCU case log, tab-separated, headers in the first row.
Which branches have the most Critical and High risk cases? Which case owners
have the highest proportion of Escalated cases? Summarise the top risk areas
for the RCU team in 3 bullet points, and name the specific cases driving
each risk.
```
### What to Expect
Chat reads the pasted table and generates a natural-language insight summary — no formula involved. This is the shift from **calculation → analysis → insight**, the RCU team's daily workflow in compressed form.

> ### ⚠️ Data Handling — Read This
> This is a **synthetic training dataset**, safe to paste. RCU works with real applicant data every day — that is not.
> - Only paste into **Copilot Chat signed in with your BFL work account** (look for the green "Protected" / enterprise data-protection indicator)
> - Never paste applicant PII — **Applicant Names, PAN, loan amounts, contact details** — or anything under CAS / compliance restriction
> - **De-identify first** — replace Applicant Names with Applicant-1, Applicant-2, drop the Loan Amount column, and paste only the fields the question actually needs
>
> Pasting the *shape* of a problem is almost always enough. Pasting the *whole* problem rarely is. For a fraud-and-verification function, that discipline is not optional.

---

## What Changes When You Get a Copilot Licence

Keep this session's habits — they transfer. The licence removes the copy-paste, not the thinking.

| | **Copilot Chat** *(today)* | **Copilot in Excel** *(licensed)* |
|---|---|---|
| Sees your workbook | ✗ — you describe it | ✓ — reads it directly |
| Writes formulas | ✓ | ✓ |
| **Inserts** formulas into cells | ✗ — you paste | ✓ automatic |
| Builds PivotTables | ✗ — gives you the steps | ✓ builds them |
| Analyses your data | ✓ — if you paste it in | ✓ — reads the sheet |
| Formats, charts, highlights | ✗ | ✓ |
| Explains any formula | ✓ | ✓ |

**The transferable skill:** describing your data clearly, stating the rule precisely, and checking the answer against a known number. Participants who build that habit here get more out of the licensed tool later than those who skip straight to it.

---

## Quick Reference — Formulas You Built Today

| Column | Label | Formula Logic |
|--------|-------|---------------|
| Q | Breach Flag | Pending if open / Breach if TAT > Benchmark / On Time otherwise |
| R | Risk Score Band | Critical=4, High=3, Medium=2, Low=1 |
| S | Pending Days | 0 if closed / Days since received if still open |
| T | Resolution Category | Fast / Within TAT / Moderate Breach / Critical Breach / Pending |

---

## Quick Reference — Prompt Patterns

| You want | Say this |
|---|---|
| A formula | *"Write a formula for cell **X3** that…, ready to fill down to row 27"* |
| It to handle blanks | *"…if the TAT in column L is blank, return 'Pending'. Check the blank first."* |
| A text-to-number map | *"…map Critical to 4, High to 3, Medium to 2, Low to 1, anything else 0, from column O."* |
| A simpler version | *"Rewrite this using IFS."* / *"Try it with SWITCH."* |
| To understand it | *"Explain this formula in simple terms, part by part."* |
| To fix a date error | *"This returns #VALUE!. My date in column J is text, not a real date. Fix it."* |
| A pivot | *"Give me step-by-step instructions to build a PivotTable that… Tell me which field goes in which area."* |
| A count / average without a pivot | *"Give me a COUNTIFS (or AVERAGEIFS) formula for … so I can build a summary grid."* |
| Analysis on pasted data | *[paste the data]* + *"Above is my table, headers in the first row. Which…?"* |

---

*Bajaj Finance Limited | AI Academy — Risk Containment Unit (RCU) | Microsoft Copilot Training Programme*
*Technizer India*
