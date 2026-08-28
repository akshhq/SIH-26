# 🛡️ MPLADS Sentinel (रक्षक)
### *Explainable AI Evidence Verification & Risk Intelligence Layer for MPLADS / eSAKSHI*

[![Smart India Hackathon 2026](https://img.shields.io/badge/SIH-2026-orange.svg)](https://sih.gov.in)
[![Problem Statement ID](https://img.shields.io/badge/PS%20ID-SIH26102-blue.svg)](https://sih.gov.in/sih2026PS)
[![Ministry](https://img.shields.io/badge/Ministry-MoSPI%20(DIID)-green.svg)](https://www.mospi.gov.in)
[![Category](https://img.shields.io/badge/Category-Software%20%7C%20Miscellaneous-purple.svg)](https://sih.gov.in)

---

## 🏛️ What We Are Building

**MPLADS Sentinel** is an AI-powered **evidence and risk-intelligence layer** for the MPLADS/eSAKSHI ecosystem.

> **eSAKSHI records and manages project activity; MPLADS Sentinel continuously checks whether reported project, financial, documentary, visual and progress information is internally consistent and supported by evidence.**

The system is designed to detect and prioritize:

- 💰 financial anomalies and unusual expenditure
- ⏱️ delayed, stalled or unrealistic projects
- 📄 document and certificate inconsistencies
- 📸 reused, wrong or incomplete visual evidence
- 🔁 duplicate / near-duplicate works
- 🧩 suspicious relationships and concentration patterns
- 📜 guideline / compliance violations
- 🔎 multi-signal cases requiring investigation

**Important:** Sentinel produces **risk and investigation-priority signals, not accusations or automated findings of guilt.**

---

## 🎯 Core Strategic Positioning

```text
                    MPLADS / eSAKSHI
                           │
                           ▼
                  SYSTEM OF RECORD
                           │
                           ▼
                  ┌─────────────────┐
                  │ MPLADS SENTINEL │
                  │                 │
                  │ Rules           │
                  │ Financial ML    │
                  │ NLP / Docs      │
                  │ Computer Vision │
                  │ Graph Analytics  │
                  │ Prediction       │
                  │ XAI + RAG        │
                  └────────┬────────┘
                           ▼
                  Evidence + Risk
                           ▼
                 Investigation Queue
                           ▼
                 Authorized Human Review
```

---

# 📚 Final Four Source-of-Truth Documents

| # | File | Role |
|---:|---|---|
| 1 | `SIH26102_Complete_Knowledge_Base.md` | Complete project knowledge base and strategic reference. |
| 2 | `MPLADS_Sentinel_Curated_Project_Definition.md` | The definitive explanation of what we are actually building and the intended product scope. |
| 3 | `SIH26102_PPT_Content_Bank_Complete.md` | Comprehensive content bank for the official six-slide SIH presentation; deliberately not compressed. |
| 4 | `MPLADS_Sentinel_Custom_AI_Specification.md` | Complete specification of the custom AI modules, techniques, inputs, outputs and priorities. |

### Supporting assets

- `SIH26102_MPLADS_Deep_Dive_Analysis.md`
- `SIH26102_PPT_Content_Blueprint.md`
- Official MPLADS CSV datasets
- `Official_MPLADS_Guidelines_2023.pdf`
- `CAG_Compliance_Audit_Case_Study.pdf`
- `SIH_Sample_6_Slide_PPT_Chakravyuh.pdf`
- `index.html`

---

# 🔄 End-to-End Product Lifecycle

```text
1. PROJECT PROPOSAL
        ↓
2. ELIGIBILITY / COMPLIANCE
        ↓
3. PROJECT BLUEPRINT
   ├── Scope
   ├── Budget
   ├── Timeline
   ├── Milestones
   ├── Dependencies
   └── Evidence Requirements
        ↓
4. APPROVAL / SANCTION
        ↓
5. IMPLEMENTING AGENCY
        ↓
6. EXECUTION
        ↓
7. MILESTONE UPDATE
        ↓
8. DOCUMENT + IMAGE + FINANCIAL EVIDENCE
        ↓
9. CONTROL ENGINE
        ↓
10. AI VERIFICATION
        ↓
11. COMPOSITE RISK
        ↓
12. EXPLAINABLE ALERT / EVIDENCE CARD
        ↓
13. AUTHORIZED INVESTIGATION
        ↓
14. OUTCOME + FEEDBACK
```

---

# 🧠 Hybrid AI Architecture

```text
                         MPLADS AI
                            │
          ┌─────────────────┼─────────────────┐
          ▼                 ▼                 ▼
     Financial AI      Document AI       Computer Vision
          │                 │                 │
          └─────────────────┼─────────────────┘
                            ▼
                       NLP / Duplicate
                            │
                            ▼
                        Graph AI
                            │
                            ▼
                     Predictive AI
                            │
                            ▼
                       Risk Engine
                            │
                            ▼
                    Explanation + RAG
```

## Custom AI modules

1. Proposal Intelligence
2. Compliance Intelligence
3. Cost Anomaly Detection
4. Timeline Intelligence
5. Duplicate Project Detection
6. Document Intelligence
7. Image / Visual Evidence Verification
8. Financial Anomaly Detection
9. Evidence Cross-Checking
10. Graph / Relationship Intelligence
11. Predictive Risk
12. AI Audit Copilot

---

# 🧩 Five Core Risk Pillars for the SIH MVP

| Pillar | Function | Candidate methods |
|---|---|---|
| 1️⃣ NLP | Duplicate / split-work similarity | Sentence-BERT, cosine similarity, edit distance |
| 2️⃣ Statistical / ML | Cost and progress anomalies | MAD, Robust Z-score, Isolation Forest, LOF |
| 3️⃣ Graph | Agency / vendor concentration and relationships | NetworkX, HHI, graph features |
| 4️⃣ Rules | Statutory and workflow compliance | 2023 Guidelines + deterministic rules |
| 5️⃣ XAI + RAG | Explain and ground alerts | SHAP / attribution + FAISS + local LLM |

```text
Multiple independent signals
             ↓
       Risk aggregation
             ↓
       Composite Risk 0–100
             ↓
       Evidence Card
             ↓
     Investigation priority
```

---

# 📊 Data Strategy

## Real prototype data

The project is grounded in available MPLADS datasets covering:

- Recommended works — Lok Sabha / Rajya Sabha
- Sanctioned works — Lok Sabha / Rajya Sabha
- Completed works — Lok Sabha / Rajya Sabha
- Expenditure — Lok Sabha / Rajya Sabha
- MP allocation limits — Lok Sabha / Rajya Sabha
- Calamity consent — Lok Sabha / Rajya Sabha

The current repository also contains an official allocation dataset representing **544 Lok Sabha constituencies and ₹8,306.21 crore**.

## Data gap strategy

Some high-value evidence fields may not be publicly available:

- detailed milestone events
- full invoices / bills
- complete inspection history
- stage-specific photographs
- GPS evidence
- verified fraud labels

Therefore:

```text
REAL PUBLIC DATA
       +
AUTHORIZED FUTURE DATA
       +
CLEARLY LABELLED SYNTHETIC TEST DATA
```

Synthetic records should be used for controlled validation, not presented as real government cases.

---

# 🕵️ Irregularity / Fraud-Signal Coverage

Sentinel can create signals for:

- cost inflation
- unusual expenditure
- duplicate payments
- duplicate / overlapping works
- work-splitting patterns
- stalled execution
- financial-vs-physical mismatch
- false or reused images
- wrong-location evidence
- incomplete work represented as complete
- document inconsistency
- certificate inconsistency
- missing evidence
- repeated revisions
- unusual agency/vendor concentration
- prohibited work categories
- allocation/compliance deviations
- suspicious workflow actions

> **An anomaly is a reason to investigate, not proof of fraud.**

---

# 🔎 Explainable Evidence Card

Every high-risk case should answer:

```text
WHY WAS THIS FLAGGED?
        ↓
WHAT SIGNAL TRIGGERED?
        ↓
WHAT RECORD SUPPORTS IT?
        ↓
WHAT DOCUMENT / IMAGE SUPPORTS IT?
        ↓
WHAT GUIDELINE / RULE IS RELEVANT?
        ↓
WHAT SHOULD THE OFFICER CHECK NEXT?
```

Example:

```text
PROJECT: MPL-004821

Risk: 87 / 100
Priority: HIGH

Signals
├── Cost deviation
├── Timeline delay
├── Financial / physical disparity
├── Document inconsistency
└── Duplicate-evidence similarity

Evidence
├── Source record
├── Source document
├── Source image
└── Relevant rule / guideline

Action
└── Create investigation case
```

---

# 🖥️ Prototype Modules

### Live AI Auditor Console

- risk-ranked work table
- filters
- primary risk signal
- composite score
- evidence-card access

### Interactive 6-Slide Pitch

- six official SIH slides
- presentation navigation

### AI Risk Sandbox

- live risk-score simulation
- pillar-level inputs
- composite score visualization

### 12-Stage Financial / Administrative Flow

- recommendation
- examination
- feasibility
- sanction
- agency
- execution
- monitoring
- payment controls
- CNA transfer
- inspection
- completion
- handover

### Repository / Dataset Explorer

- Markdown viewer
- CSV explorer
- official document access
- research / guide navigation

### Audit Copilot

Natural-language questions grounded in official documents and structured project data.

---

# 🛠️ Candidate Technology Stack

### Frontend

React / Next.js • TypeScript • Tailwind CSS • Recharts • Leaflet / Mapbox

### Backend

Python • FastAPI • Uvicorn • Pydantic

### Data

PostgreSQL / SQLite • pandas • NumPy

### AI / ML

scikit-learn • sentence-transformers • NetworkX • OpenCV • OCR • FAISS • SHAP • Ollama

---

# 🔐 Governance

The architecture should include:

- RBAC
- separation of duties
- maker-checker-approver controls
- mandatory evidence
- audit logs
- record/version history
- model/version logging
- controlled evidence access
- encryption where appropriate

### Core rule

> **The AI recommends where to look. Authorized humans make official decisions.**

---

# 🚀 SIH MVP

The strongest realistic MVP is:

```text
REAL MPLADS DATA
      ↓
NORMALIZATION
      ↓
5-PILLAR RISK ENGINE
      ↓
PROJECT RISK RANKING
      ↓
EXPLAINABLE EVIDENCE CARD
      ↓
AUDITOR DASHBOARD
      ↓
INVESTIGATION BRIEF
```

The demo should prove this loop convincingly rather than superficially implementing every possible AI feature.

---

# 🧪 Validation

Because reliable fraud labels may be unavailable:

- use unsupervised anomaly detection
- validate deterministic rules against documented rules
- test duplicate matching with controlled examples
- create synthetic attack scenarios
- measure ranking quality
- measure false-positive behavior
- evaluate explanation traceability

Avoid unsupported claims such as “98% fraud accuracy” or “zero fraud.”

---

# 🏆 Presentation Strategy

The final SIH presentation is constrained to six slides:

1. Title
2. Idea / Proposed Solution
3. Technical Approach
4. Feasibility & Viability
5. Impact & Benefits
6. Research & References

The separate PPT content bank intentionally contains far more content so the team can select the strongest material later.

---

# 🎯 Final Positioning

> ## **MPLADS Sentinel is not another dashboard.**
>
> **It is an evidence-linked AI trust and risk layer for the MPLADS lifecycle — designed to continuously screen project, financial, documentary, visual and relationship data and bring the highest-risk cases to authorized investigators.**

---

*Developed for Smart India Hackathon 2026 | SIH26102 | Ministry of Statistics and Programme Implementation (MoSPI)*
