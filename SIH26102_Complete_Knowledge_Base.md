# SIH26102 — Complete Working Knowledge Base

> **Purpose:** Master reference containing everything established so far for the MPLADS AI monitoring project.

## 1. Problem Statement

**SIH26102:** Development of an AI-powered system to detect anomalies, fraud, and inefficiencies in MPLAD Scheme implementation.

**Organization:** MoSPI  
**Division:** Data Informatics & Innovation Division (DIID)  
**Category:** Software  
**Theme:** Miscellaneous

### Core interpretation

The project should not be treated as merely an “AI fraud detector” or another dashboard.

The strongest interpretation is:

> **An evidence-driven, AI-powered lifecycle and risk-intelligence layer for MPLADS that continuously checks whether project claims, financial activity, documents, images, timelines and reported progress are consistent with the approved project plan and with each other.**

---

# 2. Existing Ecosystem Understanding

MPLADS is currently supported by the **eSAKSHI** digital ecosystem.

The current workflow should be understood approximately as:

```text
MP Recommendation
        ↓
District / Competent Authority
        ↓
Feasibility / Sanction
        ↓
Implementing Agency
        ↓
Work Execution
        ↓
Progress / Documents / Images
        ↓
Payment Requests
        ↓
PFMS / Government Payment Flow
        ↓
Completion / Closure
```

Important correction:

> The system should not be designed around the assumption that money simply flows from the ministry directly to an individual worker.

The current ecosystem includes Implementing Agencies, vendors, government authorities and PFMS/payment mechanisms.

### Product implication

Do **not** replace eSAKSHI unless required.

Preferred framing:

> **eSAKSHI + AI Trust / Intelligence Layer**

The existing platform records what stakeholders report. The proposed system checks:

> **Does the evidence support what was reported?**

---

# 3. Core Product Philosophy

The goal should not be:

> “Guarantee zero fraud.”

No software can honestly guarantee that.

The goal should be:

### **Fraud-resistant by design + continuously verifiable + difficult to manipulate + easy to investigate.**

Use three major control layers:

```text
PREVENTION
    ↓
DETECTION
    ↓
INVESTIGATION
```

### Prevention

- Role-based access
- Separation of duties
- Approval controls
- Budget locks
- Milestone dependencies
- Mandatory evidence
- Versioned records
- Direct/controlled payment workflow

### Detection

- Rule engine
- Statistical anomaly detection
- ML
- NLP
- Computer vision
- Graph analytics
- Predictive models

### Investigation

- Evidence-linked alerts
- Explainable risk scores
- Complete audit history
- Related documents
- Related payments
- Related projects
- Case management

---

# 4. Proposed End-to-End Lifecycle

```text
PROJECT PROPOSAL
      ↓
ELIGIBILITY / COMPLIANCE CHECK
      ↓
TECHNICAL ESTIMATION
      ↓
PROJECT BLUEPRINT
      ├── Scope
      ├── Budget
      ├── Timeline
      ├── Milestones
      ├── Dependencies
      └── Evidence Requirements
      ↓
ADMINISTRATIVE / TECHNICAL APPROVAL
      ↓
IMPLEMENTING AGENCY ASSIGNMENT
      ↓
EXECUTION
      ↓
MILESTONE-BASED PROGRESS
      ├── Report
      ├── Documents
      ├── Images
      ├── Measurements
      └── Financial Data
      ↓
CONTROL ENGINE
      ├── RBAC
      ├── Budget Controls
      ├── Approval Controls
      └── Immutable Audit Trail
      ↓
AI VERIFICATION
      ├── Financial
      ├── Timeline
      ├── Document
      ├── Image
      ├── NLP
      ├── Graph
      └── Prediction
      ↓
RISK ENGINE
      ↓
EXPLAINABLE ALERT
      ↓
HUMAN / AUTHORIZED REVIEW
      ↓
CASE OUTCOME
      ↓
FEEDBACK
```

---

# 5. Project Blueprint

Every approved project should have a structured digital blueprint.

## Project identity

- Project ID
- MP
- Constituency
- State
- District
- Village / ward
- Exact location
- GPS coordinates
- Work category
- Work description
- Beneficiary information
- Implementing Agency

## Scope

- Exact work
- Components
- Quantity
- Unit
- Specification
- Expected output
- Maintenance responsibility

## Timeline

Do not store only one completion date.

Use:

> **Work Breakdown Structure + Milestones + Dependencies**

Example:

```text
Site Preparation
      ↓
Foundation
      ↓
Structure
   ┌──┴───────┐
   ↓          ↓
Electrical   Plumbing
   └────┬─────┘
        ↓
    Finishing
        ↓
    Inspection
        ↓
    Completion
```

Each milestone should have:

- Planned start
- Planned end
- Actual start
- Actual end
- Dependency
- Responsible actor
- Expected output
- Budget
- Required evidence

---

# 6. Financial Model

Do not represent a project as only:

> Total project = ₹X

Use:

```text
Project Budget
    ↓
Component Budget
    ↓
Activity / Milestone Budget
    ↓
Commitments
    ↓
Payments
    ↓
Verified Expenditure
```

Recommended states:

1. Planned
2. Sanctioned
3. Committed
4. Paid / Disbursed
5. Verified Expenditure

Important principle:

> **Money transferred ≠ money spent ≠ expenditure verified.**

---

# 7. Evidence Architecture

Every important claim should have evidence.

Example:

### Claim

> Foundation completed.

Required evidence could include:

- Progress report
- Photograph
- GPS
- Timestamp
- Measurement
- Responsible person
- Inspection record
- Supporting document

Represent this as:

```text
CLAIM
  ↓
EVIDENCE
  ↓
VERIFICATION
  ↓
TRUST / RISK SIGNAL
```

Everything should be linked to the Project ID and milestone.

---

# 8. Document System

Potential documents:

- Proposal
- Estimate
- Feasibility report
- Technical sanction
- Administrative sanction
- Work order
- Invoice
- Bill
- Utilization certificate
- Progress report
- Inspection report
- Completion certificate
- Other supporting documents

AI should verify:

- Document type
- Required fields
- Project ID
- Dates
- Amounts
- Authority names
- Agency
- Milestone
- Cross-document consistency
- Duplicate documents
- Suspicious alterations

---

# 9. Image Verification

Major problem:

> Work is incomplete or incorrect, but a different / old / unrelated image is submitted and approved.

Potential controls:

## Capture controls

Capture through the application where possible.

Store:

- GPS
- Timestamp
- Project ID
- Milestone ID
- Device information
- Capture metadata

## AI checks

- Wrong asset type
- Reused image
- Near-duplicate image
- Inconsistent progress
- Possible image manipulation
- Image/location mismatch
- Image/project mismatch
- Repeated evidence

## Progress verification

Compare:

```text
Reported Progress
+
Milestone State
+
Previous Images
+
Current Image
+
Financial Utilization
```

Example:

> Reported progress = 80%  
> Financial utilization = 91%  
> Visual stage = approximately 50–60%

→ High-risk inconsistency.

---

# 10. Completion Certificate Verification

A completion certificate should be checked for:

### Structural correctness

- Project ID
- Work description
- Amount
- Completion date
- Authority
- Agency
- Required fields
- Required signatures / approvals

### Cross-document consistency

Compare against:

- Sanction
- Work order
- Expenditure
- Progress reports
- Inspection report
- Images

Example:

```text
Completion certificate:
₹28 lakh

Ledger:
₹32 lakh

→ Financial inconsistency
```

---

# 11. Major Fraud / Irregularity Taxonomy

| Category | Example | Potential Detection |
|---|---|---|
| 💰 Cost inflation | Estimate far above comparable work | Benchmark ML |
| 🧾 False billing | Invoice doesn't match work | Rules + NLP |
| 👻 Ghost work | Asset does not exist | CV + field verification |
| 📉 Under-delivery | 50% physical work but 90% spending | Financial/physical analytics |
| 🔁 Duplicate billing | Same expense submitted twice | Transaction matching |
| 🔁 Duplicate project | Same project submitted multiple times | NLP + GIS |
| 📦 Quantity fraud | Claimed quantity differs from evidence | Structured checks |
| 🧱 Quality substitution | Lower-grade material | Inspection/CV where feasible |
| ⏱️ False progress | Reported progress overstated | Timeline + CV |
| 💸 Payment anomaly | Unusual amount/timing | ML |
| 🏦 Related entities | Accounts/vendors appear linked | Graph |
| 📝 Document manipulation | Altered records | Document AI |
| 🧑‍💼 Unauthorized action | Wrong role approves | RBAC |
| 🔀 Budget diversion | Spending outside approved component | Rules |
| 💰 Unreconciled funds | Paid but not supported | Ledger reconciliation |
| 🏗️ Abandoned work | Work stalls | Timeline model |
| 📍 Location mismatch | Work evidence elsewhere | GPS |
| 📸 Reused photos | Same evidence in multiple projects | Perceptual hashing/CV |
| 🧾 Unsupported certificate | Certificate lacks evidence | Document + evidence graph |
| 🔄 Repeated revisions | Frequent budget/scope changes | Version analytics |

---

# 12. Role-Based Accountability

Model actual responsibilities instead of putting every operational action on the MP.

Possible roles:

| Role | Responsibility |
|---|---|
| MP | Recommend work |
| District / Competent Authority | Administrative oversight and sanction |
| Technical Officer | Technical verification |
| Implementing Agency | Execution |
| Site Engineer / Responsible Officer | Progress and measurements |
| Finance Officer | Financial verification |
| Inspection Officer | Physical verification |
| MoSPI / Central Authority | Monitoring |
| Auditor | Audit / investigation |

Every important action should record:

```text
WHO
WHAT
WHEN
WHERE / SOURCE
OLD VALUE
NEW VALUE
REASON
SUPPORTING EVIDENCE
AUTHORIZATION
```

---

# 13. Versioning / Audit Trail

Never silently overwrite important records.

Example:

```text
Budget v1 = ₹40L
      ↓
Budget v2 = ₹43L
      ↓
Budget v3 = ₹47L
```

Store:

- Who changed it
- When
- Why
- Approval
- Supporting document

This creates an auditable history and enables AI to detect suspicious revision patterns.

---

# 14. Financial-Physical Consistency

One of the strongest detection concepts:

```text
Financial Progress
        +
Physical Progress
        +
Milestone Progress
        +
Evidence
```

Example:

```text
Physical completion
██████████░░░░░ 62%

Financial utilization
███████████████ 88%
```

→ **Financial–Physical Mismatch**

This is a risk signal, not proof of fraud.

---

# 15. Project Digital Twin

Every project can have a live state:

```text
PROJECT #MPL-004821

Budget
₹42,00,000

Financial Progress
78%

Physical Progress
54%

Schedule Variance
+38 days

Documents
19 / 21 verified

Evidence
14 / 17 verified

AI Risk
82 / 100

Current Milestone
Structural Work

Expected Milestone
Finishing
```

This becomes the project's single operational view.

---

# 16. Graph Model

Connect:

```text
MP
 │
Project
 │
District
 │
Agency
 │
Officer
 │
Vendor
 │
Bank / Payment Entity
 │
Invoice
 │
Payment
 │
Document
 │
Evidence
 │
Location
```

Potential graph signals:

- Vendor concentration
- Repeated entities
- Unusual agency relationships
- Same account linked to multiple vendors
- Same document across projects
- Same image across projects
- Suspicious project clusters

---

# 17. Hybrid AI Philosophy

Use the correct technology for the correct task.

### Deterministic rules

When the answer is deterministic.

Example:

> expenditure > sanctioned amount

### ML / statistics

When the pattern is uncertain.

Example:

> This project is unusually expensive compared with similar projects.

### NLP / LLM

When language/document reasoning is involved.

Example:

> Compare a completion certificate with the sanctioned work.

### Computer Vision

When visual evidence matters.

Example:

> Does this image appear consistent with the claimed asset/stage?

### Graph analytics

When relationships matter.

Example:

> Does a vendor show unusual connections across projects?

---

# 18. Risk Engine

Do not use a single black-box model.

Example:

```text
Risk =

25% Financial Anomaly
20% Timeline Anomaly
20% Compliance Risk
15% Duplicate Similarity
10% Agency / Graph Risk
10% Documentation / Evidence Risk
```

Then expose the contribution:

```text
RISK = 84

Financial anomaly       +21
Timeline anomaly        +17
Image inconsistency     +19
Document inconsistency  +12
Duplicate evidence      +15
```

---

# 19. AI Risk Categories

### 🟢 Low

Normal variation.

### 🟡 Medium

One or more unusual signals.

### 🟠 High

Multiple independent anomalies.

### 🔴 Critical

Multiple strong signals and/or evidence inconsistency.

The system should say:

> **Potential irregularity — investigation recommended**

not:

> **Fraud confirmed.**

---

# 20. Real MPLADS Datasets Currently Available

The current uploaded datasets are:

| Dataset | Rows | Main use |
|---|---:|---|
| Works Recommended — Lok Sabha | 7,001 | Recommendation stage |
| Works Recommended — Rajya Sabha | 4,001 | Recommendation stage |
| Works Sanctioned — Lok Sabha | 5,001 | Sanction + status |
| Works Sanctioned — Rajya Sabha | 5,001 | Sanction + status |
| Works Completed — Lok Sabha | 3,001 | Completion |
| Works Completed — Rajya Sabha | 6,001 | Completion |
| Expenditure — Lok Sabha | 8,001 | Expenditure + vendor/payment |
| Expenditure — Rajya Sabha | 7,001 | Expenditure + vendor/payment |
| Allocated Limit — Lok Sabha | 544 | MP allocation |
| Allocated Limit — Rajya Sabha | 232 | MP allocation |
| Calamity Consent — Lok Sabha | 13 | Calamity allocation |
| Calamity Consent — Rajya Sabha | 21 | Calamity allocation |

Total uploaded CSV rows: **approximately 51,816**.

The files are real uploaded MPLADS datasets and should be treated as the baseline data source for the prototype.

---

# 21. Important Dataset Fields

## Recommended / Sanctioned

Common fields include:

- Sr. No.
- Work category
- Work
- State
- IDA
- MP
- Constituency / Elected-Nominated
- Work description
- Recommended date
- Sanction date
- Recommended amount
- Sanction amount
- Work status

## Completed

Common fields include:

- Work category
- Work
- State
- IDA
- Work description
- MP
- Constituency / Elected-Nominated
- Image
- Completion date
- Amount disbursed

## Expenditure

Important fields include:

- State
- Work
- Work ID
- IDA
- MP
- Constituency / Elected-Nominated
- Expenditure date
- Vendor name
- Payment status
- Fund disbursed amount

## Allocation

Includes:

- State
- MP
- Constituency / Elected-Nominated
- Allocated amount

---

# 22. Dataset Limitations

Current public datasets do not obviously expose every internal operational field needed for the complete proposed system.

Potential missing areas:

- Detailed milestone schedule
- BOQ
- Component-level budget
- Individual material quantities
- Full invoices
- Inspection reports
- Completion certificates
- Officer-level action logs
- GPS coordinates
- Stage-by-stage images
- Bank-level transaction details
- Confirmed fraud labels

Therefore use:

### Real data

For the baseline monitoring and analytical prototype.

### Clearly labelled synthetic data

For demonstrating additional transaction/evidence workflows not exposed publicly.

### Future integration

Explain how authorized eSAKSHI/internal systems could provide the missing fields in production.

---

# 23. Dataset Join Strategy

Conceptually:

```text
Recommended
     ↓
Sanctioned
     ↓
Expenditure
     ↓
Completed
```

The datasets contain work identifiers embedded in the `Work` strings and explicit `Work ID` values in expenditure records.

Important:

> The current files appear to represent different slices/subsets of the live ecosystem, so join coverage should be measured after normalization rather than assuming every row will match.

Use normalized work identifiers, dates and other fields.

---

# 24. Proposed Product

## MPLADS Sentinel

### Tagline

> **AI-powered early-warning & audit intelligence for public development works.**

Alternative names:

- MPLADS Rakshak
- MPLADS Insight
- eSAKSHI AI Trust Layer

### Core pitch

> **We built an explainable AI risk engine that continuously analyzes MPLADS works and tells authorities which projects, agencies and districts require attention — and exactly why.**

---

# 25. Strongest Demo

```text
12,482 Works
      ↓
Risk Engine
      ↓
843 anomalies
      ↓
127 high-risk
      ↓
18 critical
```

Open a project:

```text
RISK SCORE: 87

⚠️ 31% cost deviation
⚠️ 146-day delay
⚠️ Similar work 0.8 km away
⚠️ Agency anomaly
⚠️ Documentation gap
```

Then:

> **Why is this high risk?**

The system traces every reason back to evidence.

---

# 26. Strongest Differentiator

## Evidence-Linked Risk Intelligence

Every alert should be traceable:

```text
RISK
 ↓
REASON
 ↓
CLAIM
 ↓
EVIDENCE
 ↓
DOCUMENT / IMAGE / PAYMENT
 ↓
ORIGINAL PROJECT EVENT
```

The system does not say:

> “Trust the AI.”

It says:

> **“Here is the evidence that caused the alert.”**

---

# 27. SIH Scope

## MUST HAVE

- Real MPLADS dataset ingestion
- Data normalization
- Project lifecycle view
- Compliance/rule engine
- Risk scoring
- Cost anomaly
- Timeline anomaly
- Duplicate work detection
- Document consistency
- Image reuse detection
- GPS/location validation concept
- Financial-vs-physical mismatch
- Explainable alerts
- District / agency / work dashboards

## STRONG BONUS

- Agency graph
- GIS heatmap
- Visual progress estimation
- AI Audit Copilot
- Predictive delay
- Document authenticity signals

## FUTURE

- Satellite verification
- Advanced deepfake detection
- Real bank integration
- Nationwide live integration
- Advanced multimodal models

---

# 28. Core Design Principle

> **Every rupee should be traceable to an approved project component, every component should be traceable to a milestone, every milestone should have evidence, and every important action should have an accountable actor and immutable history.**

Then AI asks:

> **“Does reality still match what the system says should be happening?”**

---

# 29. Key Resources

- Official MPLADS/eSAKSHI: https://mplads.gov.in/
- MPLADS dashboard: https://www.mplads.gov.in/mplads/Dashboard/DashBoard.aspx
- MPLADS Guidelines 2023: https://mplads.gov.in/MPLADS/UploadedFiles/MPLADSGuidelines2023_English_.pdf
- CAG MPLADS reports: https://cag.gov.in/
- Graph fraud research: https://arxiv.org/abs/2306.10857
- Procurement fraud ML research: https://arxiv.org/abs/2304.10105
- Explainable anomaly detection research: https://arxiv.org/abs/2607.13469
