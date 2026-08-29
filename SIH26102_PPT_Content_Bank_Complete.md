# SIH26102 — Complete PPT Content Bank

## Based on the SIH 2026 Idea Presentation Format

> **⚠️ Scope Lock:** Our real MPLADS export has no images and no document content (the "Image" field in Works Completed is a text placeholder, not an image). Every slide-content block below involving Document/Image/GPS verification is marked `[DEFERRED]` and should NOT be presented as working, demoed functionality — use it only for the "roadmap / future scope" slide content, never the "what we built" slide content. Consistent with `MPLADS_Sentinel_Custom_AI_Specification.md` and `SIH26102_Complete_Knowledge_Base.md`.

> **Purpose:** This is the complete internal content bank for the SIH presentation. It is intentionally much larger than the final six-slide PPT. Nothing here is being aggressively compressed; the team can later select the strongest content for the final submission.

The supplied SIH template has six content slides including the title slide: **Title Page, Idea/Proposed Solution, Technical Approach, Feasibility & Viability, Impact & Benefits, and Research & References.** The template also instructs teams to keep the maximum to six slides, use points/diagrams/infographics/pictures, keep explanations precise, use the provided template, and submit the final file as PDF.

---

# SLIDE 1 — TITLE PAGE

## Official information

- **SMART INDIA HACKATHON 2026**
- **Problem Statement ID:** SIH26102 / 26102
- **Problem Statement Title:** Development of an AI-powered system to detect anomalies, fraud, and inefficiencies in MPLAD Scheme implementation regd.
- **Organization:** MoSPI
- **Division:** Data Informatics & Innovation Division (DIID)
- **Theme:** Miscellaneous
- **PS Category:** Software
- **Team ID:** `[TEAM ID]`
- **Team Name:** `[REGISTERED TEAM NAME]`

## Recommended idea title

# MPLADS Sentinel

### AI-Powered Evidence Verification & Risk Intelligence for MPLADS

## Alternative titles

- MPLADS Sentinel
- MPLADS Rakshak
- MPLADS Insight
- MPLADS Risk Intelligence System
- MPLADS AI Trust Layer
- Project Sentinel
- MPLADS Integrity Engine

## Optional subtitle options

> **Verify every claim. Trace every rupee. Prioritize every risk.**

> **From project monitoring to continuous, explainable risk intelligence.**

> **An AI trust layer for the MPLADS project lifecycle.**

## Possible title visual

```text
PLAN → EXECUTE → DOCUMENT → VERIFY → DETECT → INVESTIGATE
```

Or:

```text
₹ FUNDS + 📄 DOCUMENTS + 📸 EVIDENCE + 📊 PROGRESS
                         ↓
                    AI ANALYSIS
                         ↓
                  EXPLAINABLE RISK
```

---

# SLIDE 2 — IDEA TITLE / PROPOSED SOLUTION

## A. Problem understanding

MPLADS generates large volumes of:

- project proposals
- sanctions
- expenditure data
- payment information
- work-progress information
- documents
- certificates
- photographs/evidence
- implementing-agency information
- completion records

The core difficulty is not merely collecting this information.

> **The challenge is determining whether the information being reported is consistent with the approved project, the financial record, the timeline and the available evidence.**

## Examples of possible irregularities

- Cost significantly higher than comparable works
- Expenditure inconsistent with physical progress
- Work completion reported too early
- Stalled or repeatedly delayed projects
- Duplicate or highly similar works
- Duplicate payments
- Reused photographs
- Photographs from the wrong location/project
- Incomplete work represented as completed
- Certificate and expenditure mismatch
- Missing mandatory evidence
- Suspiciously repeated documents
- Unusual vendor/agency concentration
- Repeated budget or scope revisions
- Unauthorized workflow actions

---

# B. Proposed solution

## MPLADS Sentinel

> **An AI-powered verification and risk-intelligence layer for the MPLADS lifecycle that analyzes financial data, timelines, documents, images, locations, relationships and reported progress to identify anomalies and prioritize high-risk cases for investigation.**

The full solution combines:

- deterministic compliance rules ✅ MVP
- statistical anomaly detection ✅ MVP
- machine learning (Isolation Forest, etc.) ✅ MVP
- graph analytics (vendor/agency concentration) ✅ MVP — already validated on real data
- NLP/document intelligence — text similarity ✅ MVP, document OCR/parsing 🔮 deferred
- computer vision 🔮 deferred (no real image data)
- geospatial validation 🔮 deferred (no GPS in real data — only State/Constituency)
- predictive analytics ⭐ bonus, time permitting
- explainable risk scoring

---

# C. Relationship with eSAKSHI

The project should **augment rather than unnecessarily replace** the existing ecosystem.

```text
eSAKSHI / MPLADS DATA
          ↓
   Existing workflow
          ↓
 ┌──────────────────────┐
 │   MPLADS SENTINEL    │
 │                      │
 │ Rules + ML + NLP     │
 │ CV + Graph + Risk    │
 └──────────┬───────────┘
            ↓
    Evidence + Risk
            ↓
       Investigation
```

### Core positioning

> **The existing digital system records and manages project activity. MPLADS Sentinel adds an intelligence layer that continuously asks whether the reported activity is supported by evidence.**

Do not present the existing platform as useless or claim unsupported deficiencies.

---

# D. Core innovation — Evidence-linked monitoring

## Every important claim should have evidence.

Example:

```text
CLAIM
“Foundation completed”
       ↓
EVIDENCE
📸 Image
📍 Location
⏱ Timestamp
📄 Progress report
📐 Measurement
💰 Expenditure
       ↓
AI VERIFICATION
       ↓
CONSISTENT?
   ↙          ↘
 YES           NO
  ↓             ↓
Continue     Risk Alert
```

The system should not simply say:

> “AI found fraud.”

It should say:

> **“This project is high risk because these independent signals conflict, and these are the records/evidence behind the alert.”**

---

# E. Full project lifecycle

```text
PROJECT PROPOSAL
      ↓
ELIGIBILITY / COMPLIANCE
      ↓
PROJECT BLUEPRINT
      ├── Scope
      ├── Budget
      ├── Timeline
      ├── Milestones
      ├── Dependencies
      └── Evidence Requirements
      ↓
APPROVAL / SANCTION
      ↓
IMPLEMENTING AGENCY
      ↓
EXECUTION
      ↓
MILESTONE UPDATE
      ↓
DOCUMENT + IMAGE + FINANCIAL EVIDENCE
      ↓
AI VERIFICATION
      ↓
RISK ENGINE
      ↓
EXPLAINABLE ALERT
      ↓
AUTHORIZED REVIEW
      ↓
CASE OUTCOME / FEEDBACK
```

---

# F. Project Digital Twin

Each work should have one consolidated project state.

Example:

```text
WORK #<Work ID>

Sanctioned Amount     Rs.42 L
Financial Progress    78%  (disbursed / sanctioned — real field)
Status Proxy          "In Progress"  (from Work Status field — real)
Recommend->Sanction   +38 days  (flag if > 45-day guideline SLA)

Documents             [DEFERRED — no real document data]
Evidence              [DEFERRED — no real image/evidence data]

AI Risk               82/100
Status                HIGH RISK
```

## Project object can contain

### Identity

- Project ID
- MP
- Constituency
- State
- District
- Location (State + Constituency only — no GPS in real data)
- Work category
- Work description
- Implementing Agency

*(GPS and beneficiary information are not present in the real export — drop from MVP identity fields.)*

### Scope

- Work components
- Quantity
- Unit
- Specification
- Expected output
- Maintenance responsibility

### Financial

- Recommended amount
- Sanctioned amount
- Component budgets
- Milestone budgets
- Commitments
- Payments/disbursements
- Verified expenditure

### Timeline

- Planned start
- Planned completion
- Milestones
- Dependencies
- Actual start
- Actual completion
- Extensions

### Evidence `[DEFERRED — none of these fields exist in real data]`

- Documents
- Images
- Measurements
- Inspection records
- Certificates
- Metadata

---

# G. Financial intelligence

The system should distinguish:

```text
PLANNED
   ↓
SANCTIONED
   ↓
COMMITTED
   ↓
PAID / DISBURSED
   ↓
VERIFIED EXPENDITURE
```

Important principle:

> **Money transferred, money spent and expenditure verified are not necessarily the same state.**

## Candidate checks

- Sanctioned vs recommended amount
- Sanctioned vs expenditure
- Planned vs actual spending
- Expenditure velocity
- Unusual payment amounts
- Unusual payment timing
- Payment concentration
- Duplicate payment
- Split-payment patterns
- Vendor concentration
- Component overspending
- Financial/physical mismatch
- Unreconciled expenditure

---

# H. Timeline intelligence

Represent the work as milestones rather than only one final date.

Example:

```text
Site Preparation
       ↓
Foundation
       ↓
Structure
       ↓
Electrical / Plumbing
       ↓
Finishing
       ↓
Inspection
       ↓
Completion
```

Each milestone can have:

- planned start
- planned end
- actual start
- actual end
- dependency
- responsible role
- expected output
- budget
- evidence requirement

## Detect

- late start
- milestone slippage
- dependency violation
- stalled work
- repeated extensions
- unrealistic completion date
- predicted deadline miss

---

# I. Document verification `[DEFERRED — no real document data]`

## Candidate documents

- Proposal
- Estimate
- Feasibility report
- Technical sanction
- Administrative sanction
- Work order
- Invoice
- Bill
- Progress report
- Inspection report
- Utilization certificate
- Completion certificate
- Other supporting documents

## AI checks

### Document classification

Identify what type of document has been uploaded.

### OCR / extraction

Extract:

- Project ID
- Work description
- Amount
- Dates
- Authority
- Agency
- Vendor
- Certificate number
- Reference number
- Milestone

### Cross-document consistency

Example:

```text
Sanction       ₹35L
Work Order     ₹37L
Final Bill     ₹41L
Certificate    ₹35L
```

→ **Cross-document inconsistency**

### Duplicate / similarity checks

Detect:

- reused certificates
- repeated reports
- near-identical documents
- suspiciously similar wording
- repeated templates

---

# J. Image verification `[DEFERRED — no real image data]`

## Problems

- Wrong image
- Old image
- Reused image
- Image from another project
- Wrong location
- Incomplete work
- Reported progress inconsistent with image
- Potential manipulation

## Verification pipeline

```text
IMAGE
 ↓
Metadata
 ↓
GPS
 ↓
Timestamp
 ↓
Project Context
 ↓
Image Similarity
 ↓
Visual Classification
 ↓
Previous Evidence
 ↓
Risk Signal
```

## Image checks

### Location

Compare project GPS and image GPS where metadata is available.

Example:

> Image captured 18.7 km from registered project location.

If metadata is unavailable:

> Location verification unavailable.

Do not fabricate certainty.

### Reuse

Use:

- perceptual hashing
- image embeddings
- vector similarity
- nearest-neighbor search

Example:

```text
Project A ── Image X
                │
             99.4%
             similarity
                │
Project B ── Image X
```

### Wrong asset

Compare declared asset against visual evidence.

Example:

> Expected: Community Hall
>
> Visual signal: inconsistent with declared asset type.

### Progress stage

For suitable categories:

```text
Site → Foundation → Structure → Roof → Services → Finishing → Completion
```

Compare reported stage with visually inferred stage.

### Temporal consistency

Compare:

- capture time
- upload time
- previous images
- milestone dates

### Image integrity

Potential signals:

- metadata anomalies
- compression inconsistencies
- editing traces
- suspicious duplicated regions

Present these as **integrity risk**, not definitive proof of manipulation.

---

# K. Duplicate project detection

Compare (real fields only — no GPS in our data):

- Work description
- Category
- State + Constituency (proxy for location, not GPS)
- MP
- Agency
- Amount
- Dates

Pipeline:

```text
Description
    ↓
Embedding
    ↓
Similarity Search
    ↓
Same State + Constituency check
    ↓
Cost Similarity
    ↓
Time Overlap
    ↓
Duplicate Probability
```

Example output:

```text
Possible duplicate

Text similarity        92%
Same constituency      yes
Cost similarity        89%

Overall probability    91%
```

Say "same constituency" out loud in the demo, not "location similarity" — we don't have GPS to back a distance claim.

This should remain a **potential duplicate** signal, not an accusation.

---

# L. Financial–physical mismatch

One of the strongest project-level indicators — and fully buildable on real data using a status proxy instead of visual progress.

```text
Financial Progress (disbursed / sanctioned, real field)
████████████████ 88%

Status Proxy ("Completed"=100%, "In Progress"=50%, else 0%)
██████████       50%
```

Gap:

> **38 percentage points** (label as a status proxy, not verified physical inspection)

Possible interpretation:

> **High-risk inconsistency requiring review.**

Not:

> “Fraud confirmed.”

---

# M. Graph intelligence

## Entities (real-data MVP)

```text
MP
WORK
STATE / CONSTITUENCY
AGENCY (IDA)
VENDOR
PAYMENT
```

`[DEFERRED to Phase 2]`: OFFICER, DOCUMENT, IMAGE, LOCATION (GPS) — none exist in real data.

## Relationships

```text
MP → recommends → Work
Work → assigned_to → Agency
Agency → uses → Vendor
Vendor → receives → Payment
Work → located_in → State/Constituency
```

## Detect — already validated on real data

- **Vendor concentration**: "Ajay Kumar Singh" — 119 payments from a single MP, ~10x the 99th-percentile vendor across the whole Lok Sabha expenditure dataset. Lead the demo with this.
- Agency concentration by state/constituency
- Suspicious work-description clusters (NLP similarity)

---

# N. Risk engine

All MVP signals feed one risk model. (Document Risk and Image Risk removed — deferred, see Scope Lock.)

```text
Financial Risk     25%
      +
Timeline Risk      20%
      +
Compliance Risk    20%
      +
Duplicate Risk     15%
      +
Graph Risk         20%
      ↓
TOTAL RISK (0-100)
```

Example, using the real vendor-concentration case:

```text
Financial (payment structuring)              +24
Graph (vendor concentration, 10x 99th pctile) +20
Compliance (below Rs.2.5L threshold)          +18
Timeline anomaly                               +9
Duplicate similarity                           +8
                                               ───
Risk Score                                    79/100
```

## Risk bands

🟢 Low — normal variation

🟡 Medium — one or more unusual signals

🟠 High — multiple independent risk signals

🔴 Critical — strong multi-source inconsistency / investigation priority

### Governance rule

> **Risk score is an investigation-prioritization signal, not a fraud verdict.**

---

# O. Explainability

## Judge-facing question

> **Why was this vendor/work flagged?**

Example, using the real vendor-concentration finding:

```text
RISK SCORE: 79/100

119 payments from one MP (10x 99th percentile vendor)
Payment amounts unusually uniform (~Rs.19,992 each)
Multiple works below Rs.2.5L minimum threshold
```

Drill-down:

```text
Risk
 ↓
Reason
 ↓
Claim
 ↓
Evidence (real data record)
 ↓
Payment / Work / Vendor
 ↓
Original expenditure row
```

`[Phase 2]`: once Document/Image Intelligence ships, the drill-down extends to Document / Image evidence too — not yet.

This is one of the most important differentiators.

---

# P. Investigation workflow

The AI should prioritize; authorized humans should decide.

```text
ALL PROJECTS
     ↓
AI SCREENING
     ↓
RISK-RANKED QUEUE
     ↓
HIGH-RISK CASE
     ↓
EVIDENCE REVIEW
     ↓
AUTHORIZED DECISION
     ↓
CASE OUTCOME
     ↓
FEEDBACK TO SYSTEM
```

Possible case states:

- New
- Under Review
- Evidence Requested
- Escalated
- Cleared
- Confirmed Irregularity
- Closed

Use actual official terminology if later confirmed from the target workflow.

---

# Q. Innovation and uniqueness — full candidate list

## 1. Evidence-linked AI

Every alert can be traced to evidence.

## 2. Multimodal verification `[Phase 2 target — MVP uses Structured Data + Timeline + Payments only]`

```text
Structured Data + Timeline + Payments  (MVP, real data)
        +
Documents + Images + GPS  (Phase 2, once available)
```

## 3. Lifecycle intelligence

Recommendation → Sanction → Execution → Payment → Completion.

## 4. Hybrid AI

Rules + ML + NLP + CV + Graph Analytics.

## 5. Risk-based investigation

Focus attention on the most suspicious cases.

## 6. Existing-system augmentation

AI trust layer instead of unnecessary workflow replacement.

## 7. Digital project twin

One consolidated view of project state.

## 8. Continuous verification

Risk can change as new evidence arrives.

## 9. Predictive monitoring

Identify projects likely to delay or overrun.

## 10. Explainable alerts

Evidence, not black-box scores.

---

# R. Candidate visual concepts for Slide 2

### Visual 1 — Lifecycle

```text
Recommendation → Sanction → Execution → Evidence → AI → Risk
```

### Visual 2 — Trust layer

```text
eSAKSHI
   ↓
AI TRUST LAYER
   ↓
Evidence Verification
   ↓
Risk Intelligence
```

### Visual 3 — Evidence chain

```text
CLAIM → EVIDENCE → AI → RISK → INVESTIGATION
```

### Visual 4 — Digital twin

One project card with budget, timeline, evidence and risk.

---

# SLIDE 3 — TECHNICAL APPROACH

## A. High-level architecture

```text
               MPLADS / eSAKSHI
                       │
                       ↓
                DATA INGESTION
                       │
                       ↓
               DATA NORMALIZATION
                       │
                       ↓
               PROJECT DATA MODEL
                       │
         ┌─────────────┼─────────────┐
         ↓             ↓             ↓
      STRUCTURED    DOCUMENTS      IMAGES
         │             │             │
         ↓             ↓             ↓
      FEATURES      OCR/NLP         VISION
         │             │             │
         └─────────────┼─────────────┘
                       ↓
                  GRAPH LAYER
                       ↓
                  RISK ENGINE
                       ↓
              EXPLANATION ENGINE
                       ↓
                 OFFICER UI
                       ↓
               CASE MANAGEMENT
```

---

# B. Candidate technology stack

## Frontend

- React
- Next.js
- TypeScript
- Tailwind CSS
- MapLibre / Leaflet
- Recharts / Chart.js

## Backend

- Python
- FastAPI
- Optional Node.js services

## Database

- PostgreSQL
- PostGIS
- Redis where required

## Vector search

- pgvector
- FAISS
- OpenSearch / Elasticsearch where useful

## Graph

- NetworkX for prototype
- Neo4j for a richer production architecture

## ML

- scikit-learn
- XGBoost / LightGBM
- PyTorch where required

## NLP

- sentence-transformers
- Hugging Face
- OCR
- LLM API or suitable local model

## Computer Vision

- OpenCV
- image embeddings
- perceptual hashing
- visual classifiers

## Deployment

- Docker
- cloud/private cloud
- on-premise option for sensitive deployments

---

# C. AI module architecture

```text
                      AI LAYER (MVP - real data)
                         │
       ┌─────────────────┼─────────────────┐
       ↓                 ↓                 ↓
 Financial AI      Compliance AI      Duplicate AI (NLP)
       │                 │                 │
       └─────────────────┼─────────────────┘
                         ↓
                     Graph AI
                         ↓
                  Predictive AI ⭐ bonus
                         ↓
                    Risk Engine
                         ↓
                 Explanation AI

  [Phase 2, not wired in]: Document AI ─┐
  [Phase 2, not wired in]: Vision AI   ─┴→ would feed into Risk Engine once real data exists
```

---

# D. Financial AI

## Inputs

- recommended amount
- sanctioned amount
- expenditure
- disbursement
- payment date
- vendor
- agency
- category
- historical comparable works

## Candidate models

- robust Z-score
- Isolation Forest
- Local Outlier Factor
- clustering
- XGBoost if labelled outcomes become available

## Outputs

- cost anomaly
- expenditure anomaly
- payment anomaly
- vendor concentration
- financial/physical mismatch

---

# E. NLP / duplicate AI

```text
Text
 ↓
Cleaning
 ↓
Embedding
 ↓
Vector Search
 ↓
Similarity
 ↓
Context Checks
```

Use for:

- duplicate projects
- similar projects
- repeated descriptions
- document similarity
- repeated certificates

---

# F. Document AI `[DEFERRED — no real document data]`

```text
PDF / Image
     ↓
OCR
     ↓
Document Classification
     ↓
Field Extraction
     ↓
Normalization
     ↓
Cross-document Validation
```

Potential output:

> **Completion certificate amount differs from verified expenditure.**

---

# G. Computer Vision `[DEFERRED — no real image data]`

## Image verification pipeline

```text
Submitted Image
      ↓
Metadata
      ↓
GPS / Timestamp
      ↓
Image Embedding
      ↓
Similarity Search
      ↓
Visual Classification
      ↓
Milestone Context
      ↓
Risk Signal
```

Candidate checks:

- image reuse
- visual similarity
- wrong asset
- stage mismatch
- location mismatch
- temporal inconsistency
- integrity signals

---

# H. Timeline AI

Inputs:

- planned dates
- actual dates
- milestones
- dependencies
- work status
- expenditure

Outputs:

- current delay
- predicted delay
- deadline-miss probability
- stalled-work risk

---

# I. Graph AI

## Nodes (real-data MVP)

- MP
- work
- state / constituency
- agency
- vendor
- payment

`[DEFERRED]`: officer, document, image, location (GPS)

## Edges

- recommends
- assigned_to
- paid_to
- located_in
- similar_to (text-based, not GPS)

## Signals

- unusually central vendors
- repeated entities
- suspicious clusters
- shared evidence
- unusual cross-district relationships

---

# J. Rule engine

Rules are essential where the answer is deterministic.

Examples:

```text
IF expenditure > sanctioned amount
→ financial compliance alert

IF mandatory evidence missing
→ evidence alert

IF user role cannot approve
→ access/workflow alert

IF completion submitted before required milestone
→ workflow inconsistency

IF image distance > configured threshold
→ location alert
```

---

# K. Risk aggregation

```text
Financial Risk    25%
      +
Timeline Risk     20%
      +
Compliance Risk   20%
      +
Duplicate Risk    15%
      +
Graph Risk        20%
      ↓
Weighted Risk Score (0-100)
```

(Document Risk and Image Risk removed — deferred, see Scope Lock at top of file.) Weights should be configurable.

---

# L. Explainability architecture

```text
Alert
 ↓
Trigger
 ↓
Rule / Model / Feature
 ↓
Evidence
 ↓
Source Record
```

Record:

- model version
- rule version
- timestamp
- input snapshot
- score
- reasons
- confidence/uncertainty where meaningful

---

# M. End-to-end technical flow

```text
DATA
 ↓
VALIDATION
 ↓
NORMALIZATION
 ↓
ENTITY RESOLUTION
 ↓
FEATURE ENGINEERING
 ↓
RULE ENGINE
 ↓
ML / NLP / CV
 ↓
GRAPH ANALYSIS
 ↓
RISK AGGREGATION
 ↓
EXPLANATION
 ↓
DASHBOARD
 ↓
INVESTIGATION CASE
```

---

# N. Current real datasets

The current prototype data includes:

1. Works Recommended — Lok Sabha
2. Works Recommended — Rajya Sabha
3. Works Sanctioned — Lok Sabha
4. Works Sanctioned — Rajya Sabha
5. Works Completed — Lok Sabha
6. Works Completed — Rajya Sabha
7. Expenditure — Lok Sabha
8. Expenditure — Rajya Sabha
9. Allocated Limit — Lok Sabha
10. Allocated Limit — Rajya Sabha
11. Calamity Consent — Lok Sabha
12. Calamity Consent — Rajya Sabha

Verified total rows after cleaning (stripping the "Grand Total" footer row every raw file contains):

> **45,806 real rows** (corrects the earlier "~51.8k" estimate, which wasn't computed from the actual cleaned data)

| Dataset | LS + RS |
|---|---:|
| Works Recommended | 7,000 + 4,000 = 11,000 |
| Works Sanctioned | 5,000 + 5,000 = 10,000 |
| Works Completed | 3,000 + 6,000 = 9,000 |
| Expenditure | 8,000 + 7,000 = 15,000 |
| Allocated Limit | 543 + 231 = 774 |
| Calamity Consent | 12 + 20 = 32 |

Use the cleaned, merged files (`/data/MPLADS_*.csv`) as the baseline for prototype analysis — not the raw uploads, which still contain the footer row and comma-formatted amount strings.

---

# O. Data fusion

Conceptual lifecycle:

```text
RECOMMENDED
     ↓
SANCTIONED
     ↓
EXPENDITURE
     ↓
COMPLETED
```

Additional relationships:

```text
MP ALLOCATION
     ↓
FUND UTILIZATION
```

```text
PROJECT
   ↓
VENDOR
   ↓
PAYMENT
```

Important implementation note:

> Do not assume that every row across every dataset matches perfectly. Normalize identifiers and measure actual join coverage.

---

# P. Prototype screens

Candidate screens — ✅ = real-data MVP, 🔮 = Phase 2 (needs document/image data):

1. ✅ National/state dashboard
2. ✅ District/agency risk leaderboard
3. ✅ Work digital twin (financial + timeline + risk, no document/evidence panel)
4. ✅ Financial analytics
5. ✅ Timeline view
6. ✅ Vendor/agency graph view
7. ✅ Risk explanation (real-signal based)
8. ✅ Investigation case
9. ⭐ AI Audit Copilot (bonus, structured-data queries only)
10. 🔮 Document viewer
11. 🔮 Image verification
12. 🔮 Duplicate evidence viewer (image-based)

---

# Q. Demo flow

## Demo case (real, already validated — lead with this)

> Vendor "Ajay Kumar Singh" — 119 works, one MP (Babu Singh Kushwaha), Uttar Pradesh

## AI finds

```text
Vendor concentration     ⚠️  10x the 99th-percentile vendor
Payment uniformity       ⚠️  ~Rs.19,992 each, minimal variance
Threshold circumvention  ⚠️  many works near the Rs.2.5L minimum
```

## Risk

> **79 / 100 — HIGH**

## Why?

```text
119 payments vs. 99th-percentile vendor's 12 payments
Std dev of just Rs.808 on a Rs.19,566 average payment
Total Rs.23.3L funneled in small, uniform tranches
```

## Evidence drill-down

Show:

- the actual expenditure rows (real CSV data, not mocked)
- the vendor-concentration chart across all Lok Sabha vendors
- the MP's other works, for context

## Final action

> **Create Investigation Case**

`[Phase 2]`: once Document/Image Intelligence ships, extend the drill-down to certificates and site photos for this same case — not available today.

---

# R. AI Audit Copilot

Optional but powerful.

Example queries:

> Show high-risk projects where spending exceeds 80% but physical progress is below 50%.

> Why is Project X high risk?

> Which vendors appear most frequently in high-risk projects?

> Show possible duplicate projects.

> What evidence is missing from this project?

The LLM should query structured data/evidence rather than invent facts.

---

# S. Security architecture

Candidate controls:

- RBAC
- least privilege
- maker-checker-approver
- separation of duties
- immutable/append-only audit events where appropriate
- version history
- evidence access control
- encryption
- secure storage
- model/rule version logging

Important message:

> **AI is the intelligence layer, not the security layer.**

---

# T. Technical innovation candidates

### Multimodal AI

Text + image + structured data.

### Graph AI

Cross-project relationship analysis.

### Explainable AI

Evidence-backed risk.

### Geospatial intelligence

Project/evidence location consistency.

### Digital twin

Single live project state.

### Predictive analytics

Delay/cost risk prediction.

### RAG / AI Copilot

Natural-language investigation interface.

---

# SLIDE 4 — FEASIBILITY AND VIABILITY

# A. Why the idea is feasible

## Data feasibility

The prototype already has real MPLADS datasets covering:

- recommended works
- sanctioned works
- completed works
- expenditure
- MP allocations
- calamity allocations

## Technical feasibility

The core components can be prototyped with available technologies:

- Python
- SQL
- ML
- NLP
- OCR
- Computer Vision
- GIS
- graph analytics
- web frameworks

## Product feasibility

The MVP does not require a production government integration to demonstrate the intelligence layer.

---

# B. MVP — what must actually work

## Data

- Load real MPLADS data
- Normalize fields
- Create project-level records
- Establish measurable joins

## Detection

At minimum:

1. Cost anomaly
2. Financial/physical mismatch
3. Timeline anomaly
4. Duplicate work similarity
5. Image reuse detection if usable image data is available
6. Document consistency where documents are available
7. Explainable risk scoring

## Product

- Dashboard
- Project page
- Risk queue
- Evidence view
- Investigation case

---

# C. Data availability challenge

Some production-level fields may not be available in public data.

Potential gaps:

- detailed milestone schedules
- BOQ
- component-level budgets
- full invoices
- inspection reports
- completion certificates
- officer-level action logs
- GPS
- stage-specific photographs
- bank-level transaction information
- reliable fraud labels

## Mitigation

```text
REAL PUBLIC DATA
       +
CLEARLY LABELLED SYNTHETIC DATA
       +
FUTURE AUTHORIZED INTEGRATION
```

Do not disguise synthetic data as official data.

---

# D. Fraud-label challenge

A conventional supervised fraud classifier may not have enough reliable labels.

## Approach

Use:

- deterministic rules
- unsupervised anomaly detection
- similarity detection
- graph analytics
- semi-supervised methods where possible
- controlled synthetic attacks
- historical audit findings where relevant
- ranking evaluation

Do not claim unsupported accuracy.

---

# E. False positives

An unusual project is not necessarily fraudulent.

## Mitigation

- Multiple independent signals
- Evidence-linked alerts
- Confidence/uncertainty
- Configurable thresholds
- Human review
- Risk terminology instead of guilt terminology

---

# F. Image verification challenge `[Currently: fully deferred, not a "which categories" question]`

The real challenge isn't category suitability — it's that **no image data exists in the current public MPLADS export at all** (verified: the "Image" field in Works Completed is a text placeholder, not an image, link, or file).

## For SIH

Don't build this module. State it plainly as a roadmap item: *"the current eSAKSHI export doesn't expose image content — this is Phase 2 once that data is opened up."*

## Phase 2, once real image data exists

- metadata / GPS / timestamp checks
- image similarity (perceptual hashing, embeddings)
- controlled visual classification, starting with categories where the expected asset is clear and stages are visually distinguishable
- stronger multimodal models, satellite imagery, field verification integrations (further out)

---

# G. Government integration challenge

Direct live eSAKSHI/PFMS integration cannot be assumed during SIH.

## Prototype

```text
CSV / Mock API
      ↓
Production-style schema
      ↓
Risk engine
```

## Production

```text
Authorized government API / integration
      ↓
Secure integration layer
      ↓
Same risk engine
```

The core architecture therefore survives the transition from prototype to production.

---

# H. Scalability

National-scale deployment may involve substantially larger data volumes.

Candidate approach:

- PostgreSQL indexing
- PostGIS
- asynchronous processing
- batch inference
- vector indexing
- caching
- model serving
- event-driven ingestion

---

# I. Security/privacy

Potential sensitive information requires:

- RBAC
- encryption
- access control
- audit logging
- least privilege
- secure deployment
- private/on-premise deployment where required

---

# J. LLM hallucination challenge

Do not allow an LLM to invent an official finding.

Preferred:

```text
Structured Record
      ↓
Evidence Retrieval
      ↓
LLM Explanation
```

Not:

```text
LLM Guess
      ↓
Official Decision
```

---

# K. Data quality

Potential issues:

- missing values
- inconsistent names
- spelling variation
- duplicate rows
- incomplete joins
- inconsistent dates
- inconsistent amounts

Pipeline:

```text
RAW DATA
 ↓
CLEANING
 ↓
ENTITY RESOLUTION
 ↓
VALIDATION
 ↓
CANONICAL DATA
```

---

# L. Synthetic attack generator

A strong development and demo mechanism:

```text
REAL WORK RECORD
     ↓
ATTACK GENERATOR (structured-data only)
     ├── Inflate cost vs. category median
     ├── Change recommend->sanction date gap
     ├── Alter amount below Rs.2.5L threshold (splitting)
     ├── Delay completion beyond 1-year norm
     ├── Duplicate work description in same constituency
     └── Artificial vendor-payment concentration
     ↓
AI DETECTOR
     ↓
DETECTION RESULT
```

("Duplicate image," "duplicate document," "location mismatch" attacks removed — deferred along with the modules they'd test.) This allows the team to demonstrate that the system can detect controlled anomalies without falsely claiming real-world fraud labels.

---

# M. Feasibility matrix

| Component | SIH MVP | Production |
|---|---|---|
| MPLADS dataset ingestion (real, 45,806 rows) | ✅ | ✅ |
| Risk engine | ✅ | ✅ |
| Financial anomaly | ✅ | ✅ |
| Compliance rule engine | ✅ | ✅ |
| Duplicate detection (text-based, no GPS) | ✅ | ✅ |
| Vendor/agency graph (HHI) | ✅ — already validated on real data | Advanced |
| Document AI | 🔮 Deferred — no real document data available | ✅ (once data available) |
| Image similarity | 🔮 Deferred — no real image data available | ✅ (once data available) |
| GPS verification | 🔮 Deferred — no coordinates in real data | ✅ (once data available) |
| Visual stage detection | 🔮 Deferred | Advanced |
| Live eSAKSHI integration | Simulated | Authorized integration |
| PFMS integration | Simulated | Authorized integration |
| National scale | Demonstration | Future |

---

# N. Long-term viability

## Phase 1 — SIH

- Real data ingestion
- Core anomaly detection
- Dashboard
- Evidence-linked risk

## Phase 2

- Authorized data integration
- Advanced CV
- Graph analytics
- Predictive models

## Phase 3

- Real-time monitoring
- Field evidence integration
- Advanced investigation tools

## Phase 4

- Other government schemes

Potential long-term category:

> **Government Expenditure & Project Risk Intelligence Platform**

---

# O. Important “do not claim” list

Do not claim:

- 100% fraud prevention
- zero fraud
- 100% image authenticity
- perfect fraud classification
- live government integration unless actually implemented
- access to restricted government data unless actually provided
- exact financial savings without measurement
- fraud labels if they do not exist

Better language:

> **risk detection**

> **potential irregularity**

> **investigation prioritization**

> **evidence inconsistency**

---

# P. Feasibility message options

### Option 1

> **The core intelligence can be demonstrated today using real MPLADS data; additional internal evidence sources can be integrated later without redesigning the risk engine.**

### Option 2

> **We separate what is already available from what requires future integration, making the prototype both honest and production-oriented.**

### Option 3

> **The MVP proves the intelligence layer first; government-system integration is an integration problem, not a redesign problem.**

---

# SLIDE 5 — IMPACT AND BENEFITS

# A. Primary beneficiaries

## MoSPI / Central Authority

- national risk visibility
- district comparisons
- trend analysis
- high-risk project prioritization
- early-warning signals

## State Nodal Authorities

- state-level risk monitoring
- agency comparison
- constituency/project monitoring
- exception-based review

## District Authorities

- investigation queue
- evidence-linked alerts
- project-level drill-down
- faster review

## MPs

- project visibility
- milestone status
- exception alerts
- implementation transparency

## Auditors

- risk-ranked cases
- evidence packages
- historical audit trail

## Citizens

Potential future benefits:

- greater transparency
- better project delivery
- stronger public accountability

---

# B. Administrative impact

### Traditional model

```text
Thousands of works
      ↓
Manual review
      ↓
Limited attention
      ↓
Delayed identification
```

### Proposed model

```text
Thousands of works
      ↓
AI screening
      ↓
Risk-ranked queue
      ↓
Targeted investigation
```

Core benefit:

> **Reduce the search space for officials.**

---

# C. Economic impact

Potential benefits:

- detect cost anomalies earlier
- reduce waste
- identify duplicate expenditure
- improve fund utilization
- identify inefficient projects
- reduce manual monitoring burden

Avoid unsupported monetary claims.

---

# D. Social impact

Potential benefits:

- faster completion of public works
- improved community assets
- stronger accountability
- earlier detection of stalled works
- improved public confidence

---

# E. Governance impact

```text
PERIODIC MONITORING
        ↓
CONTINUOUS RISK MONITORING
```

```text
STATIC REPORTS
        ↓
DYNAMIC PROJECT RISK
```

```text
EVIDENCE STORED
        ↓
EVIDENCE VERIFIED
```

```text
REVIEW EVERYTHING
        ↓
INVESTIGATE HIGH-RISK CASES FIRST
```

---

# F. Transparency impact

Every alert can show:

```text
WHY FLAGGED?
      ↓
WHICH SIGNAL?
      ↓
WHICH RECORD?
      ↓
WHICH DOCUMENT?
      ↓
WHICH IMAGE?
      ↓
WHICH PAYMENT?
```

This creates an evidence trail.

---

# G. Early warning

The system can potentially flag problems at different stages.

### Proposal stage

> Estimate unusually high.

### Sanction stage

> Potential duplicate work.

### Execution stage

> Spending is ahead of physical progress.

### Evidence submission

> Image/location inconsistency.

### Completion stage

> Certificate conflicts with financial record.

---

# H. Scalability

```text
PROJECT
   ↓
DISTRICT
   ↓
STATE
   ↓
NATIONAL MPLADS
   ↓
OTHER GOVERNMENT SCHEMES
```

The reusable pattern is:

> **Project + Money + Evidence + Timeline + Accountability**

Potential future domains:

- infrastructure schemes
- public procurement
- municipal works
- development projects
- welfare implementation

---

# I. Environmental impact

Environmental impact depends on the project category.

Potential indirect benefits:

- reduced unnecessary rework
- improved resource utilization
- better planning
- reduced wastage
- faster identification of stalled infrastructure

Do not overstate this area if the selected MPLADS projects do not demonstrate a direct environmental impact.

---

# J. Citizen transparency layer

Possible future public view:

```text
PROJECT
 ↓
LOCATION
 ↓
APPROVED SCOPE
 ↓
STATUS
 ↓
PROGRESS
 ↓
COMPLETION
```

Sensitive investigation/risk details should remain restricted to authorized personnel.

---

# K. Impact metrics to track

These are **candidate metrics**, not claims of achieved performance.

## Coverage

- works analyzed
- states/districts covered
- amount analyzed
- projects with complete evidence

## Detection

- anomalies detected
- high-risk cases
- critical cases
- duplicate candidates
- document inconsistencies
- image reuse candidates

## Operations

- average detection time
- review time saved
- evidence verification rate
- alert resolution rate

## Investigation

- alerts converted into cases
- cases resolved
- false-positive rate
- investigator feedback

---

# L. Before vs after

| Traditional monitoring | MPLADS Sentinel |
|---|---|
| Manual review | AI screening |
| Static reports | Dynamic risk |
| Isolated records | Cross-source reasoning |
| Evidence stored | Evidence analyzed |
| Equal attention | Risk-based prioritization |
| Late detection | Early warning |
| Black-box suspicion | Explainable alerts |

---

# M. Strong impact statements

### Option 1

> **Instead of asking officials to manually find anomalies across thousands of works, MPLADS Sentinel continuously screens the ecosystem and brings the highest-risk, evidence-backed cases to the top of the investigation queue.**

### Option 2

> **The impact is not replacing auditors; it is giving them a continuously prioritized map of where their attention is most valuable.**

### Option 3

> **The system shifts monitoring from periodic, record-based review toward continuous, evidence-driven risk intelligence.**

---

# SLIDE 6 — RESEARCH AND REFERENCES

# A. Official references

## MPLADS official portal

https://mplads.gov.in/

Potential use:

- scheme context
- official information
- public project ecosystem

## MPLADS dashboard

https://www.mplads.gov.in/mplads/Dashboard/DashBoard.aspx

Potential use:

- public project/status information
- expenditure context

## MoSPI

https://mospi.gov.in/

Potential use:

- ministry context
- official publications

## eSAKSHI / MPLADS dashboard

https://mplads.mospi.gov.in/digigov/dashboard.html

Potential use:

- existing digital workflow context
- integration positioning

---

# B. Official guidelines

## MPLADS Guidelines 2023

https://mplads.gov.in/MPLADS/UploadedFiles/MPLADSGuidelines2023_English_.pdf

Potential use:

- eligibility
- permissible works
- implementation rules
- financial/process controls
- compliance engine

---

# C. Audit / governance reference

## Comptroller and Auditor General of India

https://cag.gov.in/

Potential use:

- audit findings
- public expenditure monitoring
- implementation issues
- accountability

Use exact CAG reports when making a specific claim.

---

# D. Research areas

The final reference slide can include research from:

1. Financial anomaly detection
2. Government/public procurement fraud detection
3. Graph-based fraud detection
4. NLP similarity / duplicate detection
5. Image retrieval and duplicate detection
6. Image manipulation detection
7. Geospatial anomaly detection
8. Explainable AI
9. Multimodal document/image reasoning
10. Predictive project-delay modelling

---

# E. Candidate research links

## Graph-based fraud/anomaly detection

https://arxiv.org/abs/2306.10857

Use for:

> graph-based anomaly/fraud detection methodology.

## Procurement / ML fraud research

https://arxiv.org/abs/2304.10105

Use for:

> machine-learning approaches related to procurement/fraud detection.

## Explainable anomaly detection

https://arxiv.org/abs/2607.13469

Use for:

> explainability in anomaly detection.

**Important:** Verify paper metadata and exact relevance before final submission.

---

# F. Dataset references

Current prototype datasets:

### Recommended

- Works Recommended — Lok Sabha
- Works Recommended — Rajya Sabha

### Sanctioned

- Works Sanctioned — Lok Sabha
- Works Sanctioned — Rajya Sabha

### Completed

- Works Completed — Lok Sabha
- Works Completed — Rajya Sabha

### Expenditure

- Expenditure — Lok Sabha
- Expenditure — Rajya Sabha

### Allocation

- Allocated Limit — Lok Sabha
- Allocated Limit — Rajya Sabha

### Calamity

- Calamity Consent — Lok Sabha
- Calamity Consent — Rajya Sabha

---

# G. Research-to-feature mapping

| Reference / research area | Project feature |
|---|---|
| MPLADS Guidelines | Compliance engine |
| eSAKSHI | Workflow/data integration |
| MPLADS datasets | Project analytics |
| CAG reports | Risk scenarios |
| Anomaly detection | Financial risk |
| NLP similarity | Duplicate project detection |
| Image retrieval | Reused evidence detection |
| Computer vision | Visual progress/evidence checks |
| Graph fraud research | Network risk |
| Explainable AI | Evidence-linked alerts |
| Predictive modelling | Delay/overrun prediction |

---

# H. Reference-slide organization options

Instead of listing URLs randomly, group them:

```text
OFFICIAL
├── MPLADS
├── MoSPI
├── eSAKSHI
└── MPLADS Guidelines

DATA
├── Recommended
├── Sanctioned
├── Expenditure
└── Completed

RESEARCH
├── Fraud Detection
├── Anomaly Detection
├── Graph AI
├── Computer Vision
└── Explainable AI
```

---

# I. Strong research statement

> **The solution combines official MPLADS information and guidelines with established research areas in anomaly detection, NLP similarity, computer vision, graph analytics, geospatial analysis and explainable AI.**

---

# OPTIONAL CONTENT BANK — THREAT / FRAUD MATRIX

This can be used mainly on Slide 2 or Slide 3 if space permits.

| Threat / irregularity | Candidate prevention | Candidate detection |
|---|---|---|
| Cost inflation | Budget controls | Benchmark anomaly |
| False billing | Structured workflow | Document + financial AI |
| Ghost work | Mandatory evidence | CV / location / inspection |
| Under-delivery | Milestone controls | Financial vs physical |
| Duplicate project | Project ID / GIS | NLP + GIS |
| Duplicate payment | Transaction controls | Matching/anomaly detection |
| Reused image | Evidence binding | Image similarity |
| Wrong image | Capture controls | CV + metadata |
| Location mismatch | GPS capture | Geospatial validation |
| False progress | Milestone evidence | CV + timeline |
| Document manipulation | Versioning | Document AI |
| Unsupported certificate | Required evidence | Evidence graph |
| Budget diversion | Component controls | Rule engine |
| Stalled work | Milestone dependency | Timeline model |
| Vendor concentration | Monitoring | Graph analytics |
| Repeated revisions | Approval workflow | Revision anomaly |
| Missing evidence | Mandatory fields | Compliance engine |
| Unauthorized approval | RBAC | Access/workflow logs |

---

# OPTIONAL CONTENT BANK — “WHAT IF SOMEONE TRIES TO CHEAT?”

```text
CHEAT ATTEMPT
      ↓
──────────────────────────────
Inflate cost
      → Cost AI
──────────────────────────────
Reuse image
      → Image similarity
──────────────────────────────
Fake progress
      → CV + milestone AI
──────────────────────────────
Duplicate work
      → NLP + GIS
──────────────────────────────
Duplicate payment
      → Financial checks
──────────────────────────────
Alter certificate
      → Document AI
──────────────────────────────
Change project details
      → Version history
──────────────────────────────
Wrong location
      → GPS validation
──────────────────────────────
Hide relationship
      → Graph analytics
──────────────────────────────
      ↓
EXPLAINABLE RISK ALERT
```

---

# OPTIONAL CONTENT BANK — “WHAT DOES OUR CUSTOM AI ACTUALLY DO?”

```text
AI #1 — Proposal intelligence
AI #2 — Compliance intelligence
AI #3 — Cost anomaly detection
AI #4 — Timeline prediction
AI #5 — Duplicate project detection
AI #6 — Document understanding
AI #7 — Document similarity
AI #8 — Image verification
AI #9 — Financial anomaly detection
AI #10 — Financial/physical consistency
AI #11 — Graph intelligence
AI #12 — Risk aggregation
AI #13 — Explanation engine
AI #14 — Predictive risk
AI #15 — AI Audit Copilot
```

---

# OPTIONAL CONTENT BANK — AI 20/80 SPLIT

## AI-assisted development can accelerate the 20%

- frontend scaffolding
- APIs
- database models
- preprocessing
- ML pipelines
- OCR integration
- vector search
- image similarity
- dashboards
- synthetic data generation

## Team still owns the 80%

- domain rules
- fraud taxonomy
- risk definitions
- thresholds
- evidence requirements
- architecture
- model validation
- false-positive handling
- data governance
- security
- production decisions

---

# OPTIONAL CONTENT BANK — MODEL VALIDATION

Because trustworthy fraud labels may be unavailable:

## Do not say

> “Our model has 98% fraud detection accuracy.”

unless it has actually been measured against a valid labelled test set.

## Instead evaluate

### Rule correctness

Known rule violations detected correctly.

### Synthetic attack detection

Can controlled anomalies be detected?

### Ranking quality

Do high-risk cases appear near the top?

### False-positive rate

How many flagged cases are actually normal?

### Explanation quality

Can every alert be traced to evidence?

---

# OPTIONAL CONTENT BANK — SYNTHETIC ATTACK BENCHMARK

```text
REAL PROJECTS
      ↓
CONTROLLED ATTACK GENERATOR
      ├──  Cost inflation
      ├──  Duplicate image
      ├──  Date manipulation
      ├──  Payment anomaly
      ├──  False progress
      ├──  Duplicate document
      └──  Location mismatch
      ↓
AI DETECTOR
      ↓
MEASURED RESULT
```

Only publish detection percentages after actually running the benchmark.

---

# OPTIONAL CONTENT BANK — SECURITY / GOVERNANCE

The project should include:

- Role-Based Access Control
- Maker-checker-approver workflow
- Separation of duties
- Least privilege
- Version history
- Audit logs
- Evidence binding
- Model/rule versioning
- Secure storage
- Encryption
- Human review

### Important statement

> **AI identifies and prioritizes risk; authorized officials determine the final outcome.**

---

# OPTIONAL CONTENT BANK — FINAL STORY

If the final six slides need a single narrative:

```text
SLIDE 1
WHAT IS IT?
        ↓
SLIDE 2
WHAT PROBLEM DOES IT SOLVE?
        ↓
SLIDE 3
HOW DOES IT WORK?
        ↓
SLIDE 4
CAN IT ACTUALLY BE BUILT?
        ↓
SLIDE 5
WHY DOES IT MATTER?
        ↓
SLIDE 6
WHY SHOULD WE BELIEVE IT?
```

---

# FINAL ONE-LINER OPTIONS

### Technical

> **An explainable multimodal AI system for continuous MPLADS risk detection and evidence verification.**

### Impact

> **From monitoring every project manually to investigating the projects that matter most.**

### eSAKSHI positioning

> **An AI trust layer that transforms MPLADS workflow data into actionable risk intelligence.**

### Evidence

> **Every claim. Every rupee. Every milestone. Evidence-backed.**

### Recommended

> **MPLADS Sentinel: Verify the claim. Trace the evidence. Prioritize the risk.**

---

# FINAL PRESENTATION PRINCIPLE

The evaluator should leave the presentation remembering:

> ## **“This is not another dashboard. It is an evidence-linked AI trust and risk layer for the MPLADS lifecycle.”**

The system should not claim:

> “AI proves fraud.”

It should demonstrate:

> **“AI found an inconsistency, here are the independent signals, here is the underlying evidence, and here is why this case should be investigated first.”**
