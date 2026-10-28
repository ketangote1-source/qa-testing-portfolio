# Test Cases — Fees Module

**Module:** Fees (Structure → Collection → Receipt → Dues → Reports)
**Application:** InstituteSync College ERP
**Author:** Ketan Gote

| ID | Title | Steps | Test Data | Expected Result | Type |
|----|-------|-------|-----------|-----------------|------|
| TC_FEE_01 | Define fee structure | Create fee heads & amounts for a course | tuition + exam + misc | Fee structure saved & applies to mapped students | Positive |
| TC_FEE_02 | Auto-generate dues on admission | Admit a student mapped to a fee structure | admitted student | Correct total due generated automatically | Integration |
| TC_FEE_03 | Collect full payment | Record full fee payment → generate receipt | full amount | Receipt generated; due becomes 0; status = Paid | Positive |
| TC_FEE_04 | Partial payment | Pay part of the due amount | partial amount | Balance due updated correctly; receipt reflects paid & balance | Functional |
| TC_FEE_05 | Fee calculation accuracy | Sum of all heads vs displayed total | multiple heads | Displayed total = exact sum of heads (no rounding error) | Calculation |
| TC_FEE_06 | Negative / zero amount | Enter 0 or negative payment | `0`, `-500` | Rejected with validation error | Negative |
| TC_FEE_07 | Overpayment | Pay more than the due amount | due+extra | Blocked OR handled as advance per policy (no negative due) | Boundary |
| TC_FEE_08 | Receipt content | Generate receipt | valid payment | Receipt shows correct student, amount, date, receipt no., heads | Functional |
| TC_FEE_09 | Receipt number uniqueness | Generate multiple receipts | several payments | Each receipt number is unique & sequential | Functional |
| TC_FEE_10 | Payment mode | Record Cash / Online / Cheque | each mode | Mode stored & shown on receipt and report | Functional |
| TC_FEE_11 | Concession / discount | Apply a concession to a student | discount value | Due reduces by exact concession; audited | Functional |
| TC_FEE_12 | Dues report accuracy | Open dues/defaulters report | mixed paid/unpaid | Only students with balance appear; amounts correct | Report |
| TC_FEE_13 | Collection report by date range | Filter collection report by dates | date range | Totals match sum of receipts in range | Report |
| TC_FEE_14 | Export report | Export to Excel/PDF | report data | Exported file matches on-screen data | Report |
| TC_FEE_15 | Reprint / duplicate receipt | Reprint an existing receipt | paid record | Duplicate marked clearly; amounts unchanged | Functional |
| TC_FEE_16 | Concurrent payment | Two staff collect for same student simultaneously | same student | No double-count / data corruption | Edge |
