# SIH26102 — Deep-Dive Problem Statement Analysis

> **Problem:** Development of an AI-powered system to detect anomalies, fraud, and inefficiencies in MPLAD Scheme implementation  
> **Organization:** MoSPI — Data Informatics & Innovation Division (DIID)  
> **Category:** Software  
> **Theme:** Miscellaneous  
> **Problem Statement ID:** SIH26102

---

## ⚡ Executive Verdict

| Factor | Rating | Why |
|---|---|---|
| 🔎 Problem importance | ⭐⭐⭐⭐⭐ | Public money + nationwide infrastructure + accountability |
| ⚙️ Hackathon feasibility | ⭐⭐⭐⭐☆ | Very buildable if scope is controlled |
| 📊 Data feasibility | ⭐⭐⭐☆☆ | Public dashboard exists, but granular/clean data is the main challenge |
| 💡 Innovation potential | ⭐⭐⭐⭐⭐ | Huge room beyond the existing dashboard |
| 🤖 AI suitability | ⭐⭐⭐⭐⭐ | Anomaly detection + NLP + graph analytics fit naturally |
| 🌍 Real-world scalability | ⭐⭐⭐⭐⭐ | Could become a monitoring/audit intelligence layer |
| 🏆 Winning potential | ⭐⭐⭐⭐⭐ | Strong if presented as an **explainable risk engine**, not another dashboard |

### Final verdict: 🟢 GREEN LIGHT

**Single biggest reason:** this is not merely a theoretical AI problem. There is an existing government workflow, existing public data, documented historical irregularities, and a clear opportunity to build an **AI-based early-warning layer on top of MPLADS/eSAKSHI**.

The biggest danger is equally clear: **building a pretty dashboard with a random ML model will not be enough.**

---

# 1. 🔎 Pain Points & Core Understanding

## What is the actual problem?

MPLADS involves a chain roughly like:

**MP recommends work → District Authority sanctions → Implementing Agency executes → Funds are released → Work progresses → Payments/expenditure recorded → Asset completed → Documentation/UC/audit**

The PS is essentially asking:

> **Can we automatically identify where something in this chain looks unusual, risky, delayed, inefficient, duplicated, or potentially fraudulent — before it becomes an audit finding?**

That's a much more interesting interpretation than simply "use AI to detect fraud."

## 🧩 Major anomaly classes

### 1. 💰 Financial anomalies

Examples:

- Estimate ₹20 lakh → expenditure ₹29 lakh
- Unusually high expenditure compared with similar works
- Abnormal payment timing
- Large expenditure immediately before project completion
- Unusual fund utilization patterns
- Repeated cost escalation

### 2. ⏱️ Timeline anomalies

Example:

> Similar road projects normally finish in 8 months.

One project:

> 19 months → ₹18 lakh spent → only 50% progress.

That should generate a risk alert.

Historical CAG audits identified delays in sanction and completion, including cases where completion delays reached several years.

### 3. 🔁 Duplicate / suspiciously similar works

Potentially one of the strongest AI opportunities.

| Work | Location | Description | Cost |
|---|---|---|---:|
| A | Village X | Construction of community hall | ₹18L |
| B | Village X | Community hall construction | ₹17.8L |
| C | Village X | Construction of public hall | ₹18.2L |

The system could detect:

> 🚨 **Potential duplicate/similar works**

using:

- NLP similarity
- geospatial proximity
- cost similarity
- implementing agency
- beneficiary/location
- time overlap

### 4. 📜 Compliance anomalies

Convert MPLADS Guidelines into machine-checkable rules.

```text
IF
    work_type = prohibited
THEN
    compliance_risk = HIGH
```

or:

```text
IF
    expenditure > sanctioned_cost
AND
    no approved revision
THEN
    financial_risk = HIGH
```

A government monitoring system should combine:

> **Rules + Statistics + ML + Human Review**

### 5. 🏗️ Implementation inefficiency

Examples:

- Sanctioned but not started
- Started but stalled
- Repeated progress updates without completion
- Funds released but utilization low
- Completed work but documentation missing
- Abnormally slow implementing agency

### 6. 🕸️ Network-level anomalies

Instead of looking at one work independently:

```text
MP
 ↓
District Authority
 ↓
Implementing Agency
 ↓
Contractor / Agency
 ↓
Work
 ↓
Payment
 ↓
Location
```

Build a graph.

Possible pattern:

> One implementing agency is associated with an unusually large number of high-risk projects across multiple districts.

Or:

> Multiple apparently different projects share the same location + agency + description + cost pattern.

Graph-based anomaly detection is useful because relationships between entities can expose patterns that ordinary tabular analysis misses.

---

# 2. 🧠 Root Causes

The problem isn't really caused by a "lack of AI."

The deeper problem is:

### **Scale + fragmented information + manual monitoring + delayed detection**

Thousands of works can generate:

- financial records
- sanctions
- estimates
- progress reports
- completion records
- photographs
- documents
- geographical information
- agency information

A human cannot efficiently inspect every combination.

Historical audits have identified exactly the types of issues this PS mentions:

- delayed works
- incomplete/abandoned works
- irregular contract awards
- inadequate documentation
- incorrect expenditure reporting
- monitoring failures

---

# 3. 👥 Primary Stakeholders

| Stakeholder | What they need |
|---|---|
| 🏛️ MoSPI | National-level monitoring |
| 🏢 State Nodal Authority | State-level risk visibility |
| 🏙️ District Authority | Which works need attention? |
| 👨‍💼 Implementing Agency | Track delays/compliance |
| 🧑‍💼 MP | Constituency-level status |
| 🔍 Auditors | Prioritized audit cases |
| 👨‍👩‍👧 Citizens | Transparency |
| 💰 Government | Better utilization of public funds |

### Important product insight

**The citizen is not necessarily your primary user.**

The primary user should probably be:

> **District Authority / State Nodal Authority / MoSPI monitoring officer**

Citizens can be the secondary transparency layer.

---

# 4. ⚙️ Feasibility of Execution

## Can it be built during SIH?

### **Yes — if scope is controlled.**

Do **not** attempt to build:

> "A replacement for eSAKSHI."

Instead build:

> **An AI-powered Risk & Audit Intelligence Layer for eSAKSHI/MPLADS.**

This is a much stronger framing.

---

# 5. 🏗️ Recommended MVP Architecture

```text
                 MPLADS / eSAKSHI DATA
                         │
             ┌───────────┴───────────┐
             │                       │
       Structured Data          Documents
             │                       │
             ▼                       ▼
      Data Cleaning              OCR / NLP
             │                       │
             └──────────┬────────────┘
                        ▼
                Feature Engineering
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
       Rules       ML Anomaly      Graph Engine
       Engine       Detection       Analysis
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                  RISK ENGINE
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
         Risk Score          Explanation
              │                   │
              └─────────┬─────────┘
                        ▼
                OFFICER DASHBOARD
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
       Alerts        Analytics     Case Review
```

---

# 6. 🎯 Recommended MVP Features

## Feature 1 — 🔴 Risk Score

Every work gets:

> **Risk Score: 0–100**

Example:

**Work #MPL-29482**

> 🔴 **87/100 — HIGH RISK**

Breakdown:

| Signal | Contribution |
|---|---:|
| Cost deviation | +22 |
| Delay | +19 |
| Similar work nearby | +18 |
| Agency anomaly | +15 |
| Documentation gap | +13 |

This is much more useful than simply saying:

> "Our AI predicts fraud."

---

# 7. 🔍 Feature 2 — Explainable AI

This is **critical**.

Never show:

> AI says fraudulent.

Instead:

> 🚨 **Why was this flagged?**

### Example

**Risk: 87/100**

Reasons:

- Estimated cost is **31% above comparable works**
- Completion is **146 days behind expected timeline**
- Another similar work exists **0.8 km away**
- Implementing agency has unusually high concentration of works
- Completion documentation is incomplete

The system should make the evidence visible.

---

# 8. 🔁 Feature 3 — Duplicate Work Detection

Potentially a **demo killer**.

Use:

### NLP

Compare:

> "Construction of community hall at XYZ village"

with:

> "Construction of public community centre at XYZ village"

### + GPS

### + Cost

### + Category

### + Date

Then:

> ⚠️ **78% Similarity — Possible Duplicate**

---

# 9. 🕸️ Feature 4 — Agency Relationship Graph

Example:

```text
              ┌──────── Work A
              │
Agency X ─────┼──────── Work B
              │
              ├──────── Work C
              │
              └──────── Work D
                    │
                    ▼
                District Y
```

Then:

> Agency X has 46 works  
> 11 are high-risk  
> 8 have unusually similar costs  
> 5 are delayed

This is significantly more sophisticated than a standard dashboard.

---

# 10. 🗺️ Feature 5 — Geographic Risk Map

India map → State → District → Constituency.

Color intensity represents:

> **Risk concentration**

Click district:

```text
North Delhi

Total Works: 284
High Risk: 17
Medium Risk: 46
Delayed: 31
Potential Duplicates: 7
Estimated At-Risk Value: ₹4.8 Cr
```

Then drill down to individual works.

---

# 11. 📊 Data Availability

## 🟢 Good news

There is an official MPLADS public dashboard.

The official dashboard exposes information including:

- MP
- constituency
- state
- expenditure
- works
- work status
- sector
- district
- block
- village
- start date
- completion date
- sanctioned/released amounts
- unspent balances

The official MPLADS ecosystem also includes **eSAKSHI**, which handles fund flow and implementation workflows with role-based access for MPs, MoSPI, State Nodal Authorities, District Authorities and Implementing Agencies.

### Key resources

- [Official MPLADS/eSAKSHI portal](https://mplads.gov.in/)
- [MPLADS public dashboard](https://www.mplads.gov.in/mplads/Dashboard/DashBoard.aspx)
- [MPLADS Guidelines 2023](https://mplads.gov.in/MPLADS/UploadedFiles/MPLADSGuidelines2023_English_.pdf)

---

# 12. 🚨 The Data Problem

The public dashboard does **not** expose every internal field.

Do not assume you will have:

- detailed payment transactions
- contractor information
- complete BOQs
- measurement books
- every document
- every internal administrative record
- reliable historical labels saying "fraud = yes"

### Design implication

Support different data confidence levels.

---

# 13. 🧪 Data Strategy

Use a **3-layer data model**.

### Layer A — Real public data

Use:

- MPLADS dashboard
- publicly available work information
- official annual reports
- publicly available documentation

### Layer B — Derived features

Generate:

- cost deviation
- delay days
- work density
- duplicate probability
- agency concentration
- expenditure velocity
- geographic clustering

### Layer C — Synthetic transaction data

For fields not publicly available:

```text
payment_id
payment_amount
payment_date
agency_id
invoice_id
BOQ_amount
actual_amount
progress_percentage
```

Generate realistic synthetic data.

### Important

**Never pretend synthetic data is government data.**

During the demo say:

> "The prototype demonstrates the detection pipeline using public MPLADS records supplemented with clearly labelled synthetic transaction records for fields not publicly exposed."

---

# 14. 🧠 Recommended AI Architecture

Don't use one gigantic model.

Use a **hybrid intelligence engine**.

## Layer 1 — Rules

Highly reliable.

```text
IF actual_cost > sanctioned_cost
AND approved_revision = FALSE
→ HIGH RISK
```

## Layer 2 — Statistical anomaly detection

Examples:

- Isolation Forest
- Local Outlier Factor
- Robust Z-score
- clustering

Useful for:

> "This work is unusually expensive compared with similar works."

## Layer 3 — NLP

For:

- duplicate descriptions
- document analysis
- classification
- guideline matching

## Layer 4 — Graph analytics

For:

- agency-work relationships
- repeated entities
- geographic relationships
- suspicious clusters

## Layer 5 — Explainability

Use:

- SHAP where applicable
- feature contribution
- rule explanations
- nearest comparable works

---

# 15. 💡 Competitor / Existing Solution Analysis

## 🥇 eSAKSHI

The government's existing eSAKSHI platform already handles:

- work recommendations
- sanctions
- fund flow
- implementation tracking
- stakeholder workflows
- photographs
- documentation
- monitoring

The public dashboard also provides drill-down information on works, expenditure and other MPLADS information.

### Therefore:

❌ Don't pitch:

> "We created a better MPLADS dashboard."

### Pitch:

> **"We built an AI-powered intelligence and early-warning layer that continuously analyzes MPLADS data and identifies which works require human attention."**

That is the critical distinction.

---

# 16. 🏛️ Existing Government Ecosystem

There is already an ecosystem around:

- eSAKSHI
- MPLADS MIS
- fund-flow systems
- work monitoring
- audit mechanisms
- CAG audits

Your product therefore becomes:

### **Detection + Prioritization + Explanation**

rather than:

### **Data Entry + Monitoring**

---

# 17. 📚 Research Inspiration

## Paper 1 — Graph-based fraud detection

**Pattern Mining for Anomaly Detection in Graphs: Application to Fraud in Public Procurement**

Useful inspiration for:

> **Agency ↔ Work ↔ District ↔ Payment ↔ Location**

graph analysis.

[Research paper — arXiv](https://arxiv.org/abs/2306.10857)

---

## Paper 2 — ML procurement fraud detection

**Automatic Procurement Fraud Detection with Machine Learning**

Useful for:

- feature engineering
- anomaly detection
- suspicious procurement pattern detection

[Research paper — arXiv](https://arxiv.org/abs/2304.10105)

---

## Paper 3 — Explainable anomaly detection

Recent work on explainable anomaly detection combines anomaly scoring with feature-level explanations for audit users.

Useful principle:

> **"Why was this flagged?" matters as much as the score.**

[Research paper — arXiv](https://arxiv.org/abs/2607.13469)

---

# 18. 💡 Innovation Opportunities

## 🚨 Innovation #1 — MPLADS Risk Intelligence Engine

Not:

> Dashboard

But:

> **AI Audit Copilot**

Officer logs in.

The system says:

### "Here are the 10 cases you should investigate today."

---

# 19. 🧑‍💼 Innovation #2 — AI Audit Copilot

Officer asks:

> "Show me high-risk works in North Delhi where expenditure exceeds 80% but progress is below 50%."

System returns:

> 7 works found.

Or:

> "Why is Work #3289 high risk?"

AI responds based on structured evidence:

> "Risk score 82 because expenditure is 24% above comparable works, completion is 112 days late, and a similar project exists 1.1 km away."

This is a much better use of GenAI than asking an LLM to analyze the entire database.

---

# 20. 📷 Innovation #3 — Computer Vision

The current eSAKSHI ecosystem supports photographs of completed assets, creating a possible future computer-vision layer.

Potential checks:

- Expected asset type vs uploaded image
- Progress-photo consistency
- Repeated/near-duplicate photos
- Unexpected visual changes
- Possible mismatch between reported stage and photo

Example:

> ⚠️ **Possible inconsistent progress evidence**

### Recommendation

Don't make computer vision the core MVP.

Make it **Phase 2**.

---

# 21. 🛰️ Innovation #4 — GIS + Satellite Verification

Potential future feature:

```text
Project location
      ↓
Satellite imagery
      ↓
Temporal comparison
      ↓
Physical development signal
```

For certain infrastructure types, satellite imagery could help validate whether physical change appears consistent with reported progress.

Again:

**great future feature, bad thing to make your MVP depend on.**

---

# 22. 🧩 Clarity of the Problem Statement

The PS asks for:

### Input

Data relating to:

- sanctions
- expenditure
- estimates
- work progress
- payments
- asset creation

### Processing

AI/ML detects:

- anomalies
- fraud indicators
- inefficiencies
- delays
- cost overruns
- duplicate works
- deviations from norms

### Output

- risk alerts
- predictive insights
- dashboards
- compliance monitoring
- early warnings
- decision support

### The solution should visibly contain

```text
DATA
 ↓
ANALYSIS
 ↓
RISK DETECTION
 ↓
EXPLANATION
 ↓
ALERT
 ↓
ACTION
```

If any of these six steps is missing, the product feels incomplete.

---

# 23. ⚠️ Major Misinterpretations to Avoid

### ❌ "We detect corruption."

Too strong.

Use:

> **"potential irregularity / anomaly / fraud risk."**

Final determination remains with authorized officials.

### ❌ "AI decides which officer is guilty."

Absolutely not.

The system should prioritize **cases**, not accuse people.

### ❌ "Our model is 98% accurate."

Unless you have genuinely labelled ground truth, this claim is meaningless.

### ❌ "Blockchain will solve it."

Probably unnecessary.

### ❌ "AI chatbot = innovation."

A chatbot should be an interface over structured evidence, not the core intelligence.

---

# 24. 🎯 Evaluator Perspective

An evaluator will likely ask:

1. Does this actually solve MPLADS monitoring?
2. Is the AI meaningful?
3. Where did the data come from?
4. Can an officer actually use this?
5. Can this integrate with existing government infrastructure?
6. How do you prevent false accusations?
7. Can it scale?
8. Why can't MoSPI just use normal dashboards?

Your presentation should answer these **before they ask.**

---

# 25. 🏆 What Will Impress Judges Most?

| Component | Importance |
|---|---:|
| 🎯 Correct problem understanding | ⭐⭐⭐⭐⭐ |
| 🔎 Explainable risk detection | ⭐⭐⭐⭐⭐ |
| 📊 Realistic data pipeline | ⭐⭐⭐⭐⭐ |
| 🧠 Hybrid AI architecture | ⭐⭐⭐⭐⭐ |
| 🏛️ Integration with eSAKSHI | ⭐⭐⭐⭐⭐ |
| 🕸️ Graph/network detection | ⭐⭐⭐⭐☆ |
| 🗺️ GIS | ⭐⭐⭐⭐☆ |
| 🎨 UI | ⭐⭐⭐☆☆ |
| ⛓️ Blockchain | ⭐☆☆☆☆ |
| 🤖 Random GenAI chatbot | ⭐☆☆☆☆ |

---

# 26. 🚩 Red Flags

## 🔴 Red Flag #1

> "We trained an ML model on synthetic data and achieved 95% accuracy."

Judge:

> "How do you know your labels are correct?"

### Better approach

Be explicit that synthetic labels demonstrate the pipeline, not real-world fraud accuracy.

---

## 🔴 Red Flag #2

A dashboard with:

- pie chart
- bar chart
- India map
- chatbot

…and no meaningful intelligence.

---

## 🔴 Red Flag #3

Calling every anomaly "fraud."

A legitimate project can naturally have:

- higher cost
- longer timeline
- unusual geography
- unusual project type

**Anomaly ≠ fraud.**

---

## 🔴 Red Flag #4

Ignoring eSAKSHI.

The government already has a digital system.

Your product should augment it.

---

# 27. 👥 Team Fit

For a 6-person team:

| Role | People | Responsibility |
|---|---:|---|
| 🧠 ML/Data | 2 | anomaly detection, features, models |
| ⚙️ Backend | 1 | APIs, risk engine, database |
| 💻 Frontend | 1 | dashboard + GIS |
| 🗺️ Data/GIS/Integration | 1 | data pipeline, geo, graph |
| 🎨 Product + Presentation | 1 | UX, pitch, demo, documentation |

If someone can cover two areas, even better.

---

# 28. 🛠️ Suggested Tech Stack

### Frontend

- Next.js
- Tailwind CSS
- shadcn/ui

### Backend

- FastAPI

### Database

- PostgreSQL
- PostGIS

### ML

- Python
- Pandas
- NumPy
- scikit-learn
- NetworkX
- XGBoost if needed

### NLP

- sentence-transformers
- FAISS/vector database if necessary

### Visualization

- Mapbox / Leaflet
- Recharts / ECharts

### Explainability

- SHAP
- Custom reason engine

### Optional

- Neo4j for graph visualization

---

# 29. 🧭 Research → Ideation → Build Strategy

## Phase 1 — Understand MPLADS

Read:

1. **MPLADS Guidelines 2023**
2. eSAKSHI documentation
3. MPLADS dashboard
4. CAG reports
5. Annual reports

## Phase 2 — Build an anomaly catalogue

Create a table:

| Anomaly | Detectable? | Data needed | Technique |
|---|---|---|---|
| Cost overrun | ✅ | estimate + expenditure | statistical/rules |
| Delay | ✅ | dates | rules |
| Duplicate work | ✅ | description + GPS | NLP + GIS |
| Agency concentration | ✅ | agency + work | graph |
| Prohibited work | ✅ | work type | rule engine |
| Payment anomaly | ⚠️ | transactions | ML |
| Fake physical progress | ⚠️ | photos | CV |

This determines:

- architecture
- ML strategy
- dataset design
- pitch
- realistic MVP scope

---

# 30. 🤖 AI-Buildability Split — 20/80

This PS is an excellent example of where AI can accelerate coding but cannot replace system thinking.

## 🟢 The 20% AI can build quickly

AI can rapidly generate:

- FastAPI endpoints
- database models
- dashboard components
- charts
- data preprocessing
- Isolation Forest implementation
- NLP similarity
- embeddings
- basic risk scoring
- map components
- UI components
- synthetic datasets
- API integration boilerplate

---

# 31. 🔴 The 80% AI Cannot Decide for You

Your team still needs to determine:

- What actually constitutes suspicious behavior?
- Which anomalies matter?
- What thresholds are reasonable?
- How do you distinguish anomaly from fraud?
- Which data should influence risk?
- How should risk be explained?
- What action should an officer take?
- How do you prevent political/administrative bias?
- How does this integrate with eSAKSHI?
- What happens when data is missing?
- How do you validate the model without ground-truth fraud labels?

That's the real engineering challenge.

---

# 32. ⚠️ Biggest AI Risk

If your team blindly asks AI:

> "Build an AI fraud detection system."

you'll probably end up with:

```text
CSV
 ↓
Random Forest
 ↓
Risk Score
 ↓
Dashboard
```

That is **not** enough.

The correct architecture is:

```text
MPLADS GUIDELINES
       +
HISTORICAL AUDIT FINDINGS
       +
DOMAIN RULES
       +
STATISTICAL ANOMALIES
       +
ML
       +
GRAPH ANALYSIS
       +
HUMAN REVIEW
```

---

# 33. 🎤 Judge Q&A Stress Test

## Q1. "Where did you get your fraud labels from?"

### Strong answer

> "We are not claiming supervised fraud classification because publicly available MPLADS data does not provide reliable fraud labels. Our prototype uses a hybrid risk engine: deterministic compliance rules, statistical anomaly detection, similarity detection and graph-based signals. Synthetic labelled cases are used only to demonstrate the pipeline, while real public MPLADS data validates the feature-generation and monitoring workflow."

### Likely follow-up

> "So how will this work in production?"

**Answer:**

> "Historical CAG findings, departmental audit outcomes and confirmed investigation results can eventually provide feedback labels. The system would progressively move from unsupervised risk detection toward supervised learning using validated cases."

---

## Q2. "Why do we need your system when eSAKSHI already exists?"

### Strong answer

> "eSAKSHI is the system of record and workflow platform. We are not replacing it. Our system acts as an intelligence layer on top of that ecosystem. eSAKSHI tells an officer what has happened; our system prioritizes what deserves attention and explains why."

Conceptually:

```text
eSAKSHI
   ↓
DATA
   ↓
YOUR RISK ENGINE
   ↓
"Investigate these 10 works first."
```

---

## Q3. "How do you know an anomaly is actually fraud?"

### Strong answer

> "We don't claim that it is. An anomaly is an investigation signal, not a verdict. The platform labels cases as low, medium or high risk based on explainable evidence and routes them for human verification."

---

## Q4. "What if your AI produces too many false positives?"

### Strong answer

> "We don't rely on a single model. Risk is composed from multiple independent signals, and high-risk alerts require stronger evidence. We also expose the individual factors contributing to the score so officers can adjust thresholds and provide feedback."

### Likely follow-up

> "What happens to officer workload?"

**Answer:**

> "The objective is not to flag everything. It's to reduce thousands of works to a manageable investigation queue — for example, the top 1–5% requiring attention."

---

## Q5. "What if the data is incomplete?"

### Strong answer

> "Missingness itself becomes a signal where appropriate, but we never fabricate government records. The system distinguishes between observed, derived and unavailable fields. During prototyping we use clearly labelled synthetic records for unavailable transaction-level fields, while the production architecture accepts those fields through authorized eSAKSHI integrations."

---

# 34. 💥 One Structural Change a Judge Could Demand

Imagine a judge says:

> **"Instead of showing risk at work level, show me which implementing agencies are creating abnormal patterns across districts."**

Could you change it live?

### If architecture is designed correctly: **YES.**

Use:

```text
Raw Data
   ↓
Feature Layer
   ↓
Risk Engine
   ↓
Entity-level aggregation
   ↓
Dashboard
```

Then aggregate the same risk signals by:

- Work
- Agency
- District
- Constituency
- State
- Sector

This is why the dashboard should not be hard-coded around individual projects.

---

# 35. 🧠 Winning Product Concept

## **MPLADS Sentinel**

### *AI-powered early-warning & audit intelligence for public development works*

Alternative names:

### **MPLADS Rakshak**
> *From monitoring projects to detecting risk.*

### **MPLADS Insight**
> *AI-driven risk intelligence for transparent implementation.*

---

# 36. 🔥 Core Product Pitch

Don't pitch:

> "We made an AI dashboard."

Pitch:

> ### **"We built an explainable AI risk engine that continuously analyzes MPLADS works and tells authorities which projects, agencies and districts require attention — and exactly why."**

That sentence is the product.

---

# 37. 🏆 Killer Demo Flow

### Step 1 — Show the scale

> **12,482 works analyzed**

### Step 2 — AI scans everything

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

### Step 3 — Click Critical

> **18 Critical Cases**

### Step 4 — Open one

```text
COMMUNITY HALL — XYZ

Risk Score
████████████████░░ 87

⚠️ 31% cost deviation
⚠️ 146-day delay
⚠️ Similar work 0.8 km away
⚠️ Agency anomaly
⚠️ Documentation gap
```

### Step 5 — Show graph

```text
             Work A
                │
                │
Agency X ───────┼──── Work B
                │
                ├──── Work C
                │
                └──── Work D
```

> **Agency X: 11 high-risk works across 3 districts**

### Step 6 — Ask AI

> **"Why is this case high-risk?"**

AI returns an evidence-based explanation.

### Step 7 — Officer action

```text
AI Detection
      ↓
Officer Review
      ↓
Field Verification
      ↓
Confirmed / Cleared
      ↓
Feedback
      ↓
Model Improvement
```

---

# 38. ♻️ Feedback Loop — Secret Weapon

Most hackathon teams stop at:

> AI detects anomaly.

You should go:

```text
AI flags case
      ↓
Human investigates
      ↓
Case marked:
Confirmed / False Positive
      ↓
Feedback stored
      ↓
Model recalibrated
```

That turns the project from:

> **ML demo**

into:

> **Operational intelligence system.**

---

# 39. 📈 Scalability

### Level 1

One district

↓

### Level 2

State

↓

### Level 3

All MPLADS works

↓

### Level 4

Other government schemes

Potential future applications:

- PMAY
- rural infrastructure
- municipal projects
- public procurement
- welfare expenditure

The underlying concept becomes:

> **AI-powered Government Expenditure Risk Intelligence**

---

# 40. 🌍 Real-World Impact

### 💰 Economic

Potentially identifies:

- unnecessary expenditure
- cost anomalies
- stalled projects
- inefficient fund utilization

### 🏛️ Governance

- faster audits
- prioritized investigations
- better monitoring
- improved accountability

### 👥 Social

Faster completion of:

- roads
- schools
- community facilities
- sanitation infrastructure
- public amenities

### 🔍 Transparency

Citizens could eventually see:

> "This project is delayed."

without necessarily exposing sensitive internal investigation details.

---

# 41. 🧨 Strong CAG Narrative

This PS is unusually strong because historical audit evidence already demonstrates the existence of the exact classes of problems the AI is supposed to detect.

CAG has documented:

- delayed completion
- abandoned works
- irregular awarding of contracts
- documentation weaknesses
- improper utilization reporting
- monitoring failures

A powerful presentation narrative is:

> **"Historical audits identify problems after the fact. Our system attempts to identify risk before the next audit."**

This is a strong problem-solution story.

---

# 42. 🧱 What NOT to Build

Avoid spending hackathon time on:

- ❌ Full eSAKSHI replacement
- ❌ Complex blockchain network
- ❌ Cryptocurrency/token system
- ❌ Generic ChatGPT chatbot
- ❌ Facial recognition
- ❌ Overly complex deep learning
- ❌ Mobile app + website + admin app + citizen app simultaneously
- ❌ 30 different ML models
- ❌ Fake 99% accuracy claims

Instead:

### **One excellent risk engine + one excellent dashboard + one excellent demo.**

---

# 43. 🏁 Recommended MVP Scope

## Must Have 🔥

- [ ] MPLADS dataset ingestion
- [ ] Data normalization
- [ ] Guideline-based rule engine
- [ ] Risk scoring
- [ ] Cost anomaly detection
- [ ] Delay detection
- [ ] Duplicate work detection
- [ ] Explainable alerts
- [ ] District/agency/work dashboards
- [ ] Investigation workflow

## Strong Bonus ⭐

- [ ] Agency graph
- [ ] GIS heatmap
- [ ] NLP document analysis
- [ ] AI Audit Copilot

## Stretch 🚀

- [ ] Image verification
- [ ] Satellite imagery
- [ ] Predictive completion
- [ ] Feedback-based model learning
- [ ] eSAKSHI API integration

---

# 44. 🧮 Suggested Risk Formula

Don't make the risk score a black box.

A defensible MVP formula:

```text
Risk Score =
    25% Financial Anomaly
  + 20% Timeline Anomaly
  + 20% Compliance Risk
  + 15% Duplicate Similarity
  + 10% Agency Network Risk
  + 10% Documentation Risk
```

Normalize to:

> **0–100**

Expose the components.

Later, these weights can be learned or calibrated using validated historical outcomes.

---

# 45. 🧠 Best Technical Differentiator

If you want one feature that makes judges think:

> "These guys actually thought about it."

Choose:

# **Hybrid Explainable Risk Graph**

Combine:

```text
RULES
 +
ANOMALY ML
 +
NLP
 +
GIS
 +
GRAPH
```

into a single risk score.

Example:

> **Agency X → 72% risk**

because:

- unusually high number of works
- abnormal cost distribution
- repeated project descriptions
- geographic clustering
- unusually high delays

Then visualize the connections.

That is much harder to dismiss as a simple dashboard.

---

# 46. 🏆 Final Evaluation

| Dimension | Score |
|---|---:|
| Problem significance | **10/10** |
| Government relevance | **10/10** |
| Data availability | **7/10** |
| AI suitability | **9/10** |
| MVP feasibility | **9/10** |
| Innovation potential | **9/10** |
| Scalability | **10/10** |
| Demo potential | **10/10** |
| Judge Q&A difficulty | **8/10** |
| Risk of weak implementation | **High** |

# 🟢 GREEN LIGHT

### Single biggest reason

**The problem has a rare combination of real government infrastructure + publicly visible data + documented historical irregularities + strong AI applicability + a clear gap between "monitoring" and "intelligent risk detection."**

But there is one condition:

> ### **Do NOT build "another MPLADS dashboard." Build an "AI-powered early-warning and audit intelligence layer."**

That distinction could be the difference between an ordinary SIH project and a **serious winning contender**.

---

# 🔗 Key Resources

- [Official MPLADS/eSAKSHI portal](https://mplads.gov.in/) — understand the government workflow.
- [MPLADS public dashboard](https://www.mplads.gov.in/mplads/Dashboard/DashBoard.aspx) — inspect publicly exposed data.
- [MPLADS Guidelines 2023](https://mplads.gov.in/MPLADS/UploadedFiles/MPLADSGuidelines2023_English_.pdf) — derive compliance rules.
- [CAG MPLADS Audit Reports](https://cag.gov.in/en/audit-report/details/2341) — mine real historical irregularity patterns.
- [Graph-based fraud detection research](https://arxiv.org/abs/2306.10857) — inspiration for agency/work relationship graphs.
- [ML-based procurement fraud research](https://arxiv.org/abs/2304.10105) — feature engineering and anomaly detection.
- [Explainable anomaly detection research](https://arxiv.org/abs/2607.13469) — evidence and explainability.

---

# 🚀 Immediate Next Step

Before writing code, build a **MPLADS Anomaly Taxonomy** from:

1. 2023 MPLADS Guidelines
2. CAG audit findings
3. Fields actually available through the public dashboard/eSAKSHI ecosystem

For every anomaly, classify:

**Detectable with real data / requires synthetic data / future scope**

This should become the foundation for the team's:

- architecture
- ML strategy
- dataset
- MVP
- presentation
- judge Q&A
