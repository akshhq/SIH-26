# MPLADS SENTINEL

## Explainable AI-Powered Risk Intelligence for MPLADS

> **MPLADS Sentinel** is an AI-powered risk-intelligence system that analyses MPLADS implementation data to identify suspicious financial patterns, duplicate records, compliance violations, execution delays, abnormal vendor relationships and other risk indicators, and prioritises them for human investigation.

---

# 1. PROJECT OVERVIEW

## 1.1 Problem

MPLADS generates large volumes of data covering:

- Work recommendations
- Sanctions
- Implementing Agencies (IDA)
- Vendors
- Payments / expenditure
- Work status
- Completion
- Financial years
- MP-wise allocations
- Calamity-related consent

The core problem is not merely storing this information.

The challenge is:

> **How can we automatically identify which projects, payments, vendors or agencies deserve attention first, why they are suspicious, and what evidence supports the alert?**

MPLADS Sentinel creates an analytical intelligence layer over this data.

---

## 1.2 Core Philosophy

The system should **NOT** work as:

```text
DATA
  ↓
AI
  ↓
"FRAUD CONFIRMED"
```

Instead:

```text
DATA
  ↓
DETECTION ENGINE
  ↓
ANOMALY / RISK SIGNAL
  ↓
EXPLANATION
  ↓
RISK SCORE
  ↓
HUMAN VERIFICATION
  ↓
INVESTIGATION
```

An alert is therefore a **risk indicator**, not a declaration of guilt.

---

# 2. ANOMALY, FRAUD RISK & INEFFICIENCY

These three concepts must remain separate.

| Type | Meaning | Example |
|---|---|---|
| **Anomaly** | A record or pattern that is unusual compared with normal behaviour | One work has 52 payments |
| **Fraud Risk** | A combination of indicators that may suggest manipulation or financial/procedural irregularity | Duplicate payment + abnormal vendor concentration |
| **Inefficiency** | Delay, poor execution or operational under-performance without proof of fraud | Work remains incomplete for 18 months |

The system therefore follows:

```text
ANOMALY
   ↓
RISK SIGNAL
   ↓
MULTIPLE CORRELATED SIGNALS
   ↓
HIGH-PRIORITY CASE
   ↓
HUMAN VERIFICATION
```

---

# 3. MPLADS WORK LIFECYCLE

Where data is available, Sentinel reconstructs the lifecycle of an MPLADS work:

```text
MP RECOMMENDATION
        ↓
WORK EXAMINATION
        ↓
ADMINISTRATIVE / FINANCIAL SANCTION
        ↓
IMPLEMENTING AGENCY
        ↓
WORK EXECUTION
        ↓
PAYMENT / EXPENDITURE
        ↓
INSPECTION / VERIFICATION
        ↓
COMPLETION
```

The detection engine analyses suspicious patterns across this entire lifecycle.

---

# 4. DATA FOUNDATION

## 4.1 Multi-Dataset Architecture

The 12 datasets should not be treated as isolated spreadsheets.

They should be connected using common identifiers wherever available:

- Work ID
- MP
- Constituency
- State
- Implementing Agency
- Vendor
- Dates
- Financial Year

Conceptually:

```text
RECOMMENDATION DATA
        ↓
SANCTION DATA
        ↓
WORK DATA
        ↓
PAYMENT / EXPENDITURE DATA
        ↓
COMPLETION DATA
```

Additional analytical sources include:

```text
ALLOCATION DATA
CALAMITY CONSENT DATA
```

This allows Sentinel to reconstruct:

```text
WHO recommended the work?
        ↓
WHEN was it sanctioned?
        ↓
WHO implemented it?
        ↓
WHO received payment?
        ↓
HOW MUCH was paid?
        ↓
HOW MANY payments occurred?
        ↓
WAS the work completed?
        ↓
HOW LONG did it take?
```

---

## 4.2 Unified Analytical Work Model

The system can create a common analytical representation containing fields such as:

```text
Work_ID
State
Constituency
MP
IDA
Vendor
Work_Category
Work_Description
Recommendation_Date
Sanction_Date
Completion_Date
Payment_Date
Sanctioned_Amount
Amount_Disbursed
Payment_Count
Financial_Year
Completion_Status
Image_Status
```

Derived analytical fields can include:

```text
Days_Recommendation_to_Sanction
Days_Sanction_to_Completion
Days_Since_Sanction
Total_Payments
Vendor_Payment_Share
Vendor_Work_Share
Duplicate_Flag
Overpayment_Flag
Completion_SLA_Flag
Compliance_Flag
Vendor_Concentration_Flag
Financial_Status_Mismatch
Risk_Score
Risk_Level
```

---

# 5. DETECTION FRAMEWORK

The entire detection system is divided into major analytical buckets.

```text
MPLADS SENTINEL
│
├── FINANCIAL & PAYMENT INTELLIGENCE
│
├── WORK & RECORD INTEGRITY
│
├── COST & VALUE ANOMALIES
│
├── COMPLIANCE & RULE VIOLATIONS
│
├── TIMELINE & EXECUTION EFFICIENCY
│
├── VENDOR & RELATIONSHIP INTELLIGENCE
│
└── FUND & CROSS-YEAR ANALYSIS
```

---

# 6. FINANCIAL & PAYMENT INTELLIGENCE

This bucket focuses on abnormal payment behaviour, duplicate financial records and possible over-disbursement.

---

## 6.1 Excessive / Split Payment Detector

### Objective

Detect works receiving an unusually large number of separate payments.

### Logic

```text
Group records by Work ID
        ↓
Count payment records
        ↓
Compare with similar works
        ↓
Identify unusually high payment counts
        ↓
Generate risk alert
```

### Example

```text
Work ID = WS123

Payment 1  → ₹20,000
Payment 2  → ₹20,000
Payment 3  → ₹20,000
...
Payment 52 → ₹20,000
```

If comparable works normally have 2–5 payments:

```text
WS123 → 52 payments
```

This becomes a potential payment-structuring anomaly.

### Important

A high payment count alone does **NOT** prove fraud.

Possible legitimate explanations include staged payments or multiple execution milestones.

---

## 6.2 Exact Duplicate Payment Detector

### Objective

Detect potentially duplicated ledger/payment records.

### Primary Matching Key

```text
Work ID
+
Vendor
+
Payment Date
+
Amount
```

### Example

```text
WS123 | ABC Contractors | 12-Jul-26 | ₹50,000
WS123 | ABC Contractors | 12-Jul-26 | ₹50,000
WS123 | ABC Contractors | 12-Jul-26 | ₹50,000
```

Three records have identical payment attributes.

### Interpretation

> **Potential Exact-Duplicate Payment**

### Dataset Observation

The analysed payment data contained suspicious duplicate patterns, including:

| Dataset | Potentially Duplicated Rows |
|---|---:|
| Lok Sabha | **172** |
| Rajya Sabha | **354** |

These should be treated as **records requiring verification**, not automatically as fraudulent payments.

---

## 6.3 Repeated Payment Pattern Detector

Not every duplicate has to be exact.

The detector should evaluate multiple combinations.

### Pattern A — Strongest Duplicate Signal

```text
SAME WORK ID
+
SAME VENDOR
+
SAME AMOUNT
+
SAME DATE
```

→ Very strong duplicate-record signal.

### Pattern B

```text
SAME WORK ID
+
SAME VENDOR
+
SAME AMOUNT
+
DIFFERENT DATES
```

→ Potential repeated / structured payment pattern.

### Pattern C

```text
DIFFERENT WORK IDs
+
SAME VENDOR
+
SAME AMOUNT
+
SAME / NEARBY DATE
```

→ Potential payment-pattern anomaly.

### Pattern D

```text
SAME WORK ID
+
SAME AMOUNT
+
DIFFERENT VENDORS
+
SAME DATE
```

→ Potential financial-record anomaly requiring verification.

The detector should therefore analyse **combinations of fields**, not just one duplicate condition.

---

## 6.4 Cumulative Overpayment Detector

### Objective

Detect cases where cumulative disbursement exceeds the sanctioned amount.

### Formula

```text
Total Disbursed > Sanctioned Amount
```

### Example

```text
Sanctioned Amount = ₹5,00,000

Payment 1 = ₹2,00,000
Payment 2 = ₹2,00,000
Payment 3 = ₹1,50,000

Total Disbursed = ₹5,50,000
```

Therefore:

```text
₹5,50,000 > ₹5,00,000
```

→ Potential over-disbursement.

### Risk

High priority, subject to checking revisions, refunds, corrections or legitimate financial adjustments.

---

# 7. WORK & RECORD INTEGRITY

This bucket detects duplicated works, inconsistent records and suspicious Work ID behaviour.

---

## 7.1 Similar / Duplicate Work Detector

### Objective

Identify different Work IDs that may represent the same or substantially similar work.

### Compare

```text
Work Description
+
MP
+
Constituency
+
State
+
IDA
+
Amount
```

### Example

```text
WS101
Construction of Community Hall at Village X

WS205
Construction of Community Hall at Village X
```

If location, MP, IDA and amount are also similar:

> **Potential Duplicate / Replicated Work**

### Techniques

- Text similarity
- Normalised descriptions
- Token similarity
- Fuzzy matching
- Location comparison
- Financial similarity

---

## 7.2 Work ID Consistency Detector

A Work ID can legitimately appear multiple times.

Therefore:

```text
Repeated Work ID ≠ Fraud
```

The detector should check whether repeated Work ID records contain contradictions.

### Example

```text
WS123 → Community Hall

WS123 → Road Construction
```

Potential data-integrity anomaly.

### Fields to compare

```text
Work Description
MP
State
IDA
Financial Identity
Status
```

---

# 8. COST & VALUE ANOMALY INTELLIGENCE

This bucket identifies works whose financial characteristics are unusual compared with similar works.

---

## 8.1 Cost Outlier Detector

### Objective

Identify unusually high or low work values.

### Example

```text
Similar Works:

₹2.5L
₹2.7L
₹2.8L
₹2.6L
₹8.9L  ← OUTLIER
```

The ₹8.9L work becomes a review candidate.

### Possible Methods

```text
Median comparison
IQR
Percentiles
Z-score
Category-wise statistics
Clustering
```

An outlier is a **risk signal**, not automatic evidence of inflated expenditure.

---

## 8.2 Cost-per-Unit Detector

Applicable where reliable quantity/unit data exists.

### Formula

```text
Total Cost
    ÷
Quantity
    =
Cost per Unit
```

### Example

```text
Road A:
100 metres → ₹5L

Cost per metre = ₹5,000
```

Another similar work:

```text
Road B:
100 metres → ₹12L

Cost per metre = ₹12,000
```

Potential unit-cost anomaly.

---

## 8.3 Cost-per-Day / Execution Velocity Detector

Applicable when reliable execution dates are available.

### Formula

```text
Total Amount
    ÷
Execution Duration
```

### Example

```text
Work Amount = ₹13,00,000
Execution Duration = ~6 weeks
```

Compare this against similar works.

The system can identify unusual combinations such as:

```text
Very High Cost
+
Very Short Execution
```

or:

```text
Very Low Cost
+
Very Long Execution
```

This is an anomaly detector, not direct proof of fraud.

---

# 9. COMPLIANCE & RULE INTELLIGENCE

This bucket is different from statistical anomaly detection.

It asks:

> **Does this record potentially violate an applicable MPLADS rule, limit or procedural requirement?**

---

## 9.1 Non-Permissible Work Detector

### Objective

Use text analysis / NLP to identify descriptions potentially matching prohibited or non-permissible categories.

Potential categories include:

- Religious buildings
- Welcome gates
- Private / residential buildings
- Land purchase
- CSR pooling
- Unauthorised colonies
- Recurring expenditure
- O&M expenditure

### Detection Pipeline

```text
Work Description
        ↓
Text Cleaning
        ↓
Keyword / NLP Classification
        ↓
Applicable Rule Matching
        ↓
Compliance Alert
```

### Example

```text
Work Description:

Construction of private residential building
```

→ Potential non-permissible-work alert.

The applicable guideline/version should be verified before treating the alert as an actual rule violation.

---

## 9.2 Recommendation → Sanction SLA Detector

### Objective

Identify recommendations taking longer than the applicable sanction timeline.

### Formula

```text
Sanction Date
-
Recommendation Date
=
Processing Duration
```

### Example

```text
Recommendation:
01-Jan-2026

Sanction:
20-Mar-2026

Elapsed:
78 days
```

If the applicable SLA is 45 days:

```text
78 > 45
```

→ Potential SLA breach.

### Additional Pattern

Repeated same-day approvals can separately be analysed as a timing anomaly.

Important:

```text
>45 days ≠ Fraud
Same-day approval ≠ Fraud
```

---

## 9.3 Completion SLA Detector

### Objective

Identify works remaining incomplete beyond the applicable completion period.

### Completed Work

```text
Completion Date
-
Sanction Date
```

### Incomplete Work

```text
Current Date
-
Sanction Date
```

### Example

```text
Sanction:
January 2025

Current Status:
Not Completed

Elapsed:
18 months
```

→ Completion SLA risk.

---

## 9.4 Outside-Area Recommendation Cap Detector

### Logic

```text
Identify Outside-Area Works
        ↓
Group by MP + Financial Year
        ↓
Aggregate Applicable Amount
        ↓
Compare with Applicable Cap
        ↓
Generate Alert
```

### Example

```text
Applicable Cap = ₹25L

Detected Amount = ₹32L

→ Potential Cap Breach
```

The applicable rule and cap should be verified against the relevant MPLADS guidelines.

---

## 9.5 Repair & Renovation Cap Detector

### Logic

```text
MP + Financial Year
        ↓
Identify Repair / Renovation Works
        ↓
Aggregate Amount
        ↓
Compare with Applicable Limit
```

### Example

```text
₹18L
+
₹12L
+
₹25L
=
₹55L
```

If the applicable limit is ₹50L:

```text
₹55L > ₹50L
```

→ Potential annual cap breach.

---

## 9.6 Allocation Limit Detector

### Objective

Check aggregate MP-wise recommendation / sanction against the applicable annual entitlement.

### Logic

```text
MP + Financial Year
        ↓
Aggregate Relevant Amount
        ↓
Compare with Annual Allocation
        ↓
Flag Excess
```

### Example

```text
Applicable Allocation = ₹5Cr

Detected Aggregate = ₹5.3Cr

→ Potential Allocation Limit Breach
```

---

## 9.7 Successor-MP / Post-Sanction Change Detector

### Objective

Identify unexpected changes in the MP associated with a work.

### Track

```text
Work ID
+
MP at Recommendation
+
MP at Sanction
+
MP in Later Records
```

### Example

```text
Recommendation → MP A
Sanction        → MP A
Later Record    → MP B
```

→ Potential record irregularity.

Legitimate MP succession or administrative data updates may explain such cases.

---

## 9.8 MP Tenure Detector

### Objective

Check whether recommendations or sanctions fall outside the MP's valid tenure.

### Logic

```text
MP Tenure Window
        ↓
Recommendation Date
        ↓
Sanction Date
        ↓
Validity Check
```

### Example

```text
MP tenure ends:
15-May-2026

Recommendation:
20-Jun-2026
```

→ Potential tenure irregularity.

This detector requires reliable MP tenure information.

---

## 9.9 Calamity-Fund Ceiling Clustering Detector

### Objective

Identify unusual clustering of calamity consent amounts near an applicable ceiling.

### Example

```text
₹98.5L
₹99.0L
₹99.2L
₹99.5L
₹99.8L
```

Repeated concentration near a threshold can be flagged as:

> **Potential Threshold-Clustering Anomaly**

This does not prove manipulation.

---

## 9.10 Coordinated Multi-MP Calamity Timing Detector

### Objective

Identify unusually tight timing clusters across multiple MP calamity consents.

### Example

```text
MP A → 10:02 AM
MP B → 10:05 AM
MP C → 10:08 AM
MP D → 10:11 AM
```

Repeated unusual timing clusters may indicate:

- Independent normal activity
- Coordinated administrative activity
- Potential procedural anomaly

Human verification is required.

---

# 10. TIMELINE & EXECUTION EFFICIENCY

This bucket focuses primarily on **inefficiency**, stalled implementation and mismatches between physical and financial progress.

---

## 10.1 Long-Stalled Work Detector

### Objective

Identify works with unusually long elapsed time and incomplete status.

### Stronger Signal

```text
High Disbursement
+
Not Completed
+
Long Elapsed Duration
```

### Example

```text
₹8L disbursed
+
Work Not Completed
+
18 months elapsed
```

→ High-priority execution case.

---

## 10.2 Financial-vs-Status Mismatch Detector

### Objective

Identify cases where financial progress appears inconsistent with reported physical status.

### Example

```text
Status:
In Progress

Financial Position:
90% of expected amount already disbursed
```

→ Potential financial-status mismatch.

### Strong Pattern

```text
High Disbursement
+
Low / Incomplete Physical Progress
+
Long Duration
```

→ Stronger risk signal.

---

## 10.3 Year-End Activity Concentration Detector

### Objective

Identify unusual concentration of sanctions, payments or expenditure around financial year-end.

### Example

```text
April      → 5%
May        → 6%
June       → 7%
...
February   → 10%
March      → 32%
```

→ Potential year-end activity anomaly.

Year-end activity may naturally increase, so this detector becomes stronger when combined with other signals.

---

# 11. VENDOR & RELATIONSHIP INTELLIGENCE

This is one of the most important analytical layers of MPLADS Sentinel.

Instead of analysing vendors independently, Sentinel analyses relationships between:

```text
MP
│
├── WORK
│     │
│     ├── IDA
│     │
│     └── VENDOR
│
└── PAYMENTS
```

This creates a relationship graph.

---

## 11.1 Vendor Near-Duplicate Detector

### Objective

Identify spelling variations that may represent the same vendor.

### Example

```text
ASSOSIATES
ASSOCIATES
AASSOCIATES
ASSOCIATES PVT LTD
```

### Techniques

```text
Lowercase Normalisation
Whitespace Normalisation
Punctuation Removal
Abbreviation Handling
Fuzzy String Matching
Token Similarity
```

Purpose:

> Prevent vendor activity from being artificially fragmented across slightly different names.

---

## 11.2 Vendor Concentration Detector

### Objective

Identify vendors receiving a disproportionately large share of works or payments.

### Calculate

```text
Vendor
   ↓
Number of Works
   ↓
Number of Payments
   ↓
Total Disbursement
   ↓
Portfolio Share
```

### Example

```text
MP A

Vendor X → 65%
Vendor Y → 12%
Vendor Z → 8%
Others  → 15%
```

Vendor X becomes a concentration hotspot.

### Stronger Signal

```text
High Vendor Concentration
+
Repeated Same Vendor
+
Uniform Payment Amounts
+
Multiple Works
```

→ Higher investigation priority.

---

## 11.3 Vendor Payment Uniformity Detector

### Objective

Identify unusually repeated payment amounts associated with the same vendor.

### Example

```text
₹19,990
₹20,000
₹20,000
₹19,995
₹20,000
₹20,005
...
```

A large number of highly similar payments can indicate unusual payment structuring.

### Strong Combination

```text
High Vendor Concentration
        +
Many Small Payments
        +
Highly Uniform Amounts
```

→ Stronger payment-risk signal.

---

## 11.4 Vendor–IDA Role Conflict Detector

### Objective

Identify cases where the same entity appears as both Implementing Agency and Vendor.

### Logic

```text
Implementing Agency
        vs
Vendor
```

### Example

```text
IDA = XYZ
Vendor = XYZ
```

→ Potential role-conflict alert.

This does not automatically establish wrongdoing and should be verified against the relevant administrative structure.

---

## 11.5 MP–Vendor Concentration Detector

### Objective

Identify unusually strong relationships between one MP and one vendor.

### Example

```text
MP A
│
├── Work 1 → Vendor X
├── Work 2 → Vendor X
├── Work 3 → Vendor X
├── Work 4 → Vendor X
└── Work 5 → Vendor X
```

If Vendor X receives an unusually large share of MP A's work:

> **Potential MP–Vendor Concentration**

---

## 11.6 IDA–Vendor Concentration Detector

### Objective

Identify vendors dominating an Implementing Agency's portfolio.

### Logic

```text
IDA
 ↓
Vendor Distribution
 ↓
Number of Works
 ↓
Total Payments
 ↓
Vendor Share
 ↓
Peer Comparison
```

### Example

```text
IDA A

Vendor X → 72%
Vendor Y → 10%
Vendor Z → 8%
Others  → 10%
```

→ Vendor concentration hotspot.

---

# 12. FUND & CROSS-YEAR ANALYSIS

---

## 12.1 Cross-Year Work ID Detector

A Work ID appearing across financial years is not automatically suspicious.

The system should examine:

```text
Recommendation
Sanction
Payment
Completion
Financial Year
```

### Example

```text
FY 2024–25 → WS123
FY 2025–26 → WS123
```

This may be completely legitimate.

The detector looks for unusual lifecycle fragmentation or inconsistent financial movement.

---

## 12.2 Historical / Successor MP Pattern Detector

Track:

```text
Work
 ↓
Original MP
 ↓
Sanction
 ↓
Subsequent MP
```

Unexpected changes are flagged for review.

---

# 13. MULTI-SIGNAL RISK DETECTION

Individual detectors may produce weak signals.

The major strength of Sentinel is combining multiple independent signals.

### Example

```text
WORK WS123
│
├── 52 payments
│
├── Same vendor repeatedly used
│
├── Many payments have identical amounts
│
├── Vendor highly concentrated in MP portfolio
│
├── High cumulative disbursement
│
└── Work remains incomplete
```

Instead of treating these as six unrelated alerts:

```text
Payment Risk
      +
Vendor Risk
      +
Financial Risk
      +
Timeline Risk
      ↓
COMBINED HIGH RISK
```

---

# 14. RISK SCORING & ALERT ENGINE

## 14.1 Risk Categories

A prototype scoring model can combine:

| Risk Category | Example Weight |
|---|---:|
| Financial Risk | 25% |
| Timeline Risk | 20% |
| Compliance Risk | 20% |
| Duplicate / Integrity Risk | 15% |
| Vendor / Relationship Risk | 20% |

These weights should remain configurable and can later be calibrated using validated historical cases.

---

## 14.2 Risk Levels

| Score | Risk Level | Meaning | Action |
|---:|---|---|---|
| 0–24 | Low | Normal / weak signal | Monitor |
| 25–49 | Medium | Unusual pattern | Review if needed |
| 50–74 | High | Multiple meaningful signals | Priority review |
| 75–100 | Critical | Strong multi-signal case | Investigation priority |

The thresholds should be configurable rather than permanently hard-coded.

---

# 15. EXPLAINABLE ALERT SYSTEM

Every alert should answer five questions:

```text
WHAT?
↓
Which work/payment/vendor is suspicious?

WHY?
↓
Which detector triggered?

HOW?
↓
What calculation or pattern caused the alert?

EVIDENCE?
↓
Which original records support the alert?

NEXT STEP?
↓
What should an authorised officer verify?
```

---

## Example Alert

```text
🔴 HIGH RISK — PAYMENT STRUCTURING

Work ID:
WS123

Payment Count:
52

Comparable Work Median:
4 payments

Detected Signals:
• 52 payment records detected
• 47 payments have identical/similar amounts
• Same vendor repeatedly used
• Vendor has high concentration within MP portfolio
• Work remains incomplete

Risk Categories:
Payment Risk
Vendor Risk
Timeline Risk

Recommended Verification:
• Review payment ledger
• Verify sanctioned amount
• Check payment approvals
• Check work progress
• Verify supporting financial records
```

---

# 16. DETECTOR OUTPUT SCHEMA

Every detector should produce a standardised output.

```text
Alert_ID
Work_ID
Detector_ID
Detector_Name
Risk_Category
Risk_Level
Risk_Score
Trigger_Condition
Observed_Value
Expected_Value
Evidence_Records
Explanation
Recommended_Verification
```

### Example

```text
Alert_ID:
ALT-0001

Work_ID:
WS123

Detector_ID:
PAY-002

Detector_Name:
Exact Duplicate Payment

Risk_Category:
Payment & Financial

Risk_Level:
HIGH

Observed:
Same Work ID + Vendor + Date + Amount repeated 3 times

Expected:
Unique payment record

Explanation:
Three ledger records share identical payment attributes.

Recommended Verification:
Verify payment voucher and transaction reference.
```

---

# 17. DETECTOR REGISTRY

## 17.1 Financial / Payment

| ID | Detector |
|---|---|
| PAY-001 | Excessive / Split Payment |
| PAY-002 | Exact Duplicate Payment |
| PAY-003 | Repeated Payment Pattern |
| PAY-004 | Cumulative Overpayment |

---

## 17.2 Work / Record Integrity

| ID | Detector |
|---|---|
| WORK-001 | Similar / Duplicate Work |
| WORK-002 | Work ID Consistency |

---

## 17.3 Cost

| ID | Detector |
|---|---|
| COST-001 | Cost Outlier |
| COST-002 | Cost-per-Unit |
| COST-003 | Cost-per-Day / Execution Velocity |

---

## 17.4 Compliance

| ID | Detector |
|---|---|
| COMP-001 | Non-Permissible Work |
| COMP-002 | Recommendation-Sanction SLA |
| COMP-003 | Completion SLA |
| COMP-004 | Outside-Area Cap |
| COMP-005 | Repair / Renovation Cap |
| COMP-006 | Allocation Limit |
| COMP-007 | Successor-MP Change |
| COMP-008 | MP Tenure |
| COMP-009 | Calamity Amount Clustering |
| COMP-010 | Multi-MP Timing |

---

## 17.5 Timeline / Efficiency

| ID | Detector |
|---|---|
| TIME-001 | Long-Stalled Work |
| TIME-002 | Financial-Status Mismatch |
| TIME-003 | Year-End Activity Concentration |

---

## 17.6 Vendor / Relationship

| ID | Detector |
|---|---|
| VEND-001 | Vendor Near-Duplicate |
| VEND-002 | Vendor Concentration |
| VEND-003 | Payment Uniformity |
| VEND-004 | Vendor-IDA Role Conflict |
| VEND-005 | MP-Vendor Concentration |
| VEND-006 | IDA-Vendor Concentration |

---

## 17.7 Fund / Cross-Year

| ID | Detector |
|---|---|
| FUND-001 | Cross-Year Work ID |
| FUND-002 | Historical / Successor MP Pattern |

---

# 18. END-TO-END INVESTIGATION WORKFLOW

```text
                 MPLADS DATA
                      ↓
               DATA INGESTION
                      ↓
              DATA NORMALISATION
                      ↓
             CROSS-DATASET LINKING
                      ↓
               DETECTOR ENGINE
                      ↓
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
    FINANCIAL     COMPLIANCE     TIMELINE
        ↓             ↓             ↓
        └─────────────┼─────────────┘
                      ↓
              VENDOR / GRAPH
                 ANALYSIS
                      ↓
                 NLP ANALYSIS
                      ↓
                 RISK ENGINE
                      ↓
            EXPLANATION ENGINE
                      ↓
              OFFICER DASHBOARD
                      ↓
               CASE CREATION
                      ↓
             HUMAN VERIFICATION
                      ↓
                INVESTIGATION
```

---

# 19. TECHNICAL ARCHITECTURE

```text
              MPLADS / eSAKSHI DATA
                         ↓
                  DATA INGESTION
                         ↓
                  DATA CLEANING
                         ↓
                 DATA NORMALISATION
                         ↓
                  UNIFIED DATA MODEL
                         ↓
       ┌─────────────────┼─────────────────┐
       ↓                 ↓                 ↓
     RULES              ML                NLP
       ↓                 ↓                 ↓
 Compliance           Financial        Work Similarity
 SLA Checks           Outliers         Vendor Matching
 Fund Limits          Payment          Description NLP
                     Patterns
       └─────────────────┼─────────────────┘
                         ↓
                  GRAPH ANALYSIS
                         ↓
                MP ↔ WORK ↔ VENDOR
                         ↓
                    IDA ↔ VENDOR
                         ↓
                    RISK ENGINE
                         ↓
               EXPLANATION ENGINE
                         ↓
                  OFFICER DASHBOARD
                         ↓
                   CASE MANAGEMENT
```

---

# 20. DATA PROCESSING PIPELINE

```text
RAW CSV / EXCEL
      ↓
Load Data
      ↓
Column Standardisation
      ↓
Date Parsing
      ↓
Amount Parsing
      ↓
Work ID Normalisation
      ↓
Vendor Name Normalisation
      ↓
MP Name Normalisation
      ↓
IDA Name Normalisation
      ↓
Duplicate Checking
      ↓
Cross-Dataset Joining
      ↓
Detector Engine
      ↓
Risk Engine
      ↓
Dashboard / Alerts
```

---

# 21. PHASE 1 — BUILDABLE FROM CURRENT DATASETS

The strongest MVP should focus on detectors that can be implemented using the currently available structured datasets.

## Financial

```text
Exact Duplicate Payment
Excessive Payment Count
Repeated Payment Patterns
Cumulative Overpayment
```

## Work Integrity

```text
Similar / Duplicate Work
Work ID Consistency
```

## Cost

```text
Cost Outliers
Cost-per-Unit
Cost-per-Day
```

## Compliance

```text
Non-Permissible Work NLP
Recommendation-Sanction SLA
Completion SLA
Allocation Limit
Repair / Renovation Limit
Outside-Area Limit
Cross-Year Analysis
```

## Timeline

```text
Stalled Works
Financial-Status Mismatch
Year-End Concentration
```

## Vendor Intelligence

```text
Vendor Near-Duplicates
Vendor Concentration
Payment Uniformity
Vendor-IDA Relationship
MP-Vendor Concentration
IDA-Vendor Concentration
```

---

# 22. PHASE 2 — ADDITIONAL EVIDENCE REQUIRED

Some advanced fraud detectors cannot be reliably implemented from structured datasets alone.

---

## 22.1 Image Reuse Detection

Requires actual image files.

```text
IMAGE FILES
    ↓
IMAGE HASHING
    ↓
PERCEPTUAL SIMILARITY
    ↓
DUPLICATE IMAGE DETECTION
```

Filename similarity alone cannot prove image reuse.

---

## 22.2 Fake / Non-Existent Vendor Detection

Requires external verification such as:

```text
GSTIN
PAN
Vendor Registration
MCA / Business Registry
Official Vendor Database
```

---

## 22.3 Bid-Rigging / Vendor Cartel Detection

Requires:

```text
Tender Records
Quotation Records
Bidder Information
Bid Amounts
Tender Dates
Award Information
```

---

## 22.4 SC/ST Quota Compliance

Requires:

```text
Work Location
+
Area / Constituency Classification
+
SC/ST Classification
```

---

## 22.5 Utilization Certificate Delay

Requires:

```text
UC Submission Date
+
UC Approval Date
```

---

## 22.6 Certifying-Officer Irregularity

Requires:

```text
Certifying Officer
+
Designation
+
Authority
+
Payment Certification Record
```

---

## 22.7 Land Ownership / Donation Fraud

Requires:

```text
Land Records
+
Ownership Records
+
Donation Records
+
Property Records
```

---

## 22.8 Ownership-Based Conflict of Interest

Requires:

```text
Vendor Ownership
+
Directors
+
Beneficial Ownership
+
MP / Official Relationship Data
```

---

## 22.9 Benami / Proxy Beneficiary Detection

Requires:

```text
Ground Verification
+
Ownership Records
+
Field Evidence
+
Administrative / RTI Records
```

---

# 23. PHASE ARCHITECTURE

```text
                    MPLADS SENTINEL
                          │
              ┌───────────┴───────────┐
              │                       │
           PHASE 1                 PHASE 2
       CURRENT DATASETS       ADDITIONAL EVIDENCE
              │                       │
              ↓                       ↓
       Financial Rules             Images
       Payment Patterns            GPS
       Timeline Analysis            Ownership
       Compliance NLP               Tender Data
       Vendor Graph                Registry Data
       Duplicate Detection          Field Evidence
              │                       │
              └───────────┬───────────┘
                          ↓
                  FULL EVIDENCE ENGINE
```

---

# 24. EXAMPLE END-TO-END CASE

Suppose Sentinel receives:

```text
Work ID:
WS123

Vendor:
Vendor X

Payments:
52

Repeated Amount:
₹20,000

Status:
Incomplete

Elapsed Duration:
18 months

Vendor Share of MP Portfolio:
65%
```

Detectors produce:

```text
PAY-001
Excessive Payment Count
        ↓
PAY-003
Repeated Payment Pattern
        ↓
VEND-002
Vendor Concentration
        ↓
VEND-003
Payment Uniformity
        ↓
TIME-001
Long-Stalled Work
        ↓
TIME-002
Financial-Status Mismatch
```

The risk engine combines these signals:

```text
Payment Risk
      +
Vendor Risk
      +
Timeline Risk
      +
Financial Risk
      ↓
HIGH / CRITICAL PRIORITY
```

The dashboard should then explain exactly why the case was prioritised.

---

# 25. WHAT SENTINEL SHOULD NOT DO

The system should never:

```text
❌ Declare a person guilty
❌ Automatically accuse a vendor
❌ Replace government investigation
❌ Treat every anomaly as fraud
❌ Treat every duplicate-looking record as fraudulent
❌ Infer corruption without evidence
❌ Claim image reuse without image files
❌ Claim a vendor is fake without verification
```

Instead:

```text
DETECT
   ↓
EXPLAIN
   ↓
PRIORITISE
   ↓
VERIFY
   ↓
INVESTIGATE
```

---

# 26. CORE PRODUCT DIFFERENTIATORS

## 26.1 Explainable Risk

Every alert explains:

```text
What was detected?
Why was it detected?
Which records triggered it?
What should be verified?
```

---

## 26.2 Hybrid Intelligence

```text
Rule-Based Detection
        +
Statistical / ML Detection
        +
NLP
        +
Graph Analysis
```

---

## 26.3 Full Lifecycle Analysis

```text
Recommendation
      ↓
Sanction
      ↓
Execution
      ↓
Payment
      ↓
Completion
```

---

## 26.4 Vendor Relationship Intelligence

Instead of simply counting vendors:

```text
MP ↔ Vendor
MP ↔ Work
Work ↔ Vendor
IDA ↔ Vendor
Vendor ↔ Payment
```

are analysed as a relationship network.

---

## 26.5 Human-in-the-Loop

```text
AI
 ↓
Detect
 ↓
Explain
 ↓
Prioritise
 ↓
Officer
 ↓
Verify
 ↓
Investigate
```

---

# 27. FINAL PRODUCT VISION

MPLADS Sentinel should ultimately answer one question:

> **Which MPLADS projects, payments, vendors or agencies should be investigated first, why are they risky, and what evidence supports the alert?**

---

# ONE-LINE PROJECT PITCH

> **MPLADS Sentinel converts raw MPLADS implementation data into explainable risk intelligence by detecting financial anomalies, compliance violations, suspicious payment and vendor patterns, duplicate works and execution delays — helping authorised officials investigate the right cases first.**

---

# STRONGEST SIH PITCH

> **We are not building a system that says who committed fraud. We are building a system that tells the authorised officer which transaction or project deserves attention first — and exactly why.**

---

# FINAL SYSTEM PHILOSOPHY

```text
DATA
  ↓
PATTERN
  ↓
ANOMALY
  ↓
CORRELATED RISK
  ↓
EXPLAINABLE ALERT
  ↓
HUMAN VERIFICATION
  ↓
ACTION
```

> **MPLADS Sentinel is therefore not merely a fraud detector. It is an explainable risk-intelligence and investigation-prioritisation system for MPLADS implementation.**