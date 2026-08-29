# MPLADS Sentinel — Custom AI Specification

> **Purpose:** Complete specification of what the custom AI system should do, which AI technique should be used, what inputs it needs, what outputs it produces, and what is realistically achievable for SIH.

---

## ⚠️ Scope Lock — read this before anything else

We checked the real eSAKSHI/MPLADS export we're actually building on (12 CSVs, ~52k rows: Works Recommended/Sanctioned/Completed, Expenditure, Allocated Limits, Calamity Consent). It contains **no images and no document content** — the only trace of "evidence" is a text placeholder (`"Images"`) in one column, not an actual image, link, or file.

**Consequence:** Document Intelligence (Module 6, 7) and Image Verification (Module 8, checks A–F) cannot run on real data. Building them anyway means demoing entirely synthetic images/documents and hoping no judge asks "is this real?" — that's a credibility risk, not a differentiator.

**Decision:** these modules move to **Phase 2 / Future** in this spec. Every section below that depends on them is marked `[DEFERRED]`. The MVP AI stack (Section 28) has been rewritten to only include what real data supports. This keeps the spec internally consistent with `SIH26102_Complete_Knowledge_Base.md` §27 (MUST / BONUS / FUTURE) and `MPLADS_Sentinel_Curated_Project_Definition.md`.

---

# 1. AI Philosophy

The project should not use one AI model for everything.

Use:

> **Rules for certainty + ML for patterns + NLP/LLMs for language + Computer Vision for images + Graph AI for relationships + Prediction for future risk.**

Architecture:

```text
                 MPLADS AI
                     │
      ┌──────────────┼──────────────┐
      ↓              ↓              ↓
 Financial AI     Document AI     Vision AI
      │              │              │
      └──────────────┼──────────────┘
                     ↓
                  Graph AI
                     ↓
              Predictive AI
                     ↓
                Risk Engine
                     ↓
             Explanation AI
```

---

# 2. AI Module Map

| Module | Purpose | Technique | Priority |
|---|---|---|---|
| Compliance AI | Check rules/guidelines | Rules + NLP | 🔥 MVP |
| Cost AI | Detect unusual estimates | ML/statistics | 🔥 MVP |
| Timeline AI | Detect/predict delays | rules + ML | 🔥 MVP |
| Duplicate AI | Find similar projects (text-based, no GIS/images) | NLP + embeddings | 🔥 MVP |
| Financial AI | Detect payment anomalies | statistics/ML | 🔥 MVP |
| Graph AI | Detect network anomalies (vendor/agency concentration) | graph algorithms/ML | 🔥 MVP — already validated on real data (see §17 note) |
| Prediction AI | Forecast risk | ML | ⭐ Bonus |
| Audit Copilot | Explain/query cases (over structured data only) | LLM + structured retrieval | ⭐ Bonus |
| Proposal AI | Evaluate proposal anomalies | NLP + statistics | ⭐ Bonus — mostly overlaps Cost AI + Duplicate AI |
| Document AI | Understand documents | OCR + NLP/LLM | 🔮 **[DEFERRED — no real document data]** |
| Image AI | Verify visual evidence | CV | 🔮 **[DEFERRED — no real image data]** |
| Evidence AI | Cross-check claims across docs/images | multimodal reasoning | 🔮 **[DEFERRED — depends on Document AI + Image AI]** |

---

# 3. AI Module 1 — Proposal Intelligence *(⭐ Bonus, not MVP)*

> This module is really Cost AI (§5) + Duplicate AI (§7) applied at the recommendation stage instead of the sanctioned stage. Don't build it as a separate pipeline — reuse those two modules and just run them earlier in the lifecycle if time permits. Listed here for completeness only.

## Objective

Evaluate a proposal before or around sanction, using the same cost-comparison and description-similarity logic as Modules 3 and 5.

## Inputs available in real data

- Work description, Work category, State, IDA, Recommended amount, Recommended date

## Inputs we do NOT have (drop from scope)

- District/precise location, GPS coordinates — real data only has State + Constituency, not finer geography
- "Similar beneficiary" — no beneficiary field exists in the export

## Output

```text
Proposal Risk: 63/100

Reasons:
⚠️ 34% above comparable median (same category, same state)
⚠️ Description highly similar to Project X (text similarity only — no GPS confirmation available)
```

---

# 4. AI Module 2 — Compliance Intelligence

## Objective

Convert MPLADS rules/guidelines into machine-checkable controls.

## Use two layers

### Deterministic rules

Example:

```text
IF work_type = prohibited
→ Compliance Risk = HIGH
```

### NLP

For unstructured descriptions:

> Does the work description appear consistent with permitted categories?

## Output

```text
Compliance:
✓ Location valid
✓ Required fields present
⚠️ Work description requires review
```

---

# 5. AI Module 3 — Cost Anomaly Detection

## Objective

Detect unusually high/low estimates or expenditure.

## Features

- sanctioned amount
- recommended amount
- project category
- state
- district
- work description embedding
- size/quantity where available
- historical comparable projects
- implementing agency
- vendor

## Models

Start simple:

- Robust Z-score
- Isolation Forest
- Local Outlier Factor

Optional:

- XGBoost for supervised outcomes later

## Output

```text
Cost anomaly: HIGH

Submitted:
₹42L

Comparable median:
₹30L

Deviation:
+40%
```

---

# 6. AI Module 4 — Timeline Intelligence

## Objective

Detect current delays and predict future delays.

## Inputs

- planned dates
- actual dates
- milestone dates
- dependencies
- work status
- expenditure progression

## Detect

- late start
- late milestone
- stalled work
- dependency violation
- unrealistic completion
- repeated extensions

## Prediction

> Probability of missing deadline = 81%

## Output

```text
Timeline Risk: 76

Current delay:
38 days

Predicted delay:
61 days
```

---

# 7. AI Module 5 — Duplicate Project Detection

## Objective

Detect multiple projects that may represent the same or substantially overlapping work.

## Inputs (real fields only — no GPS/coordinates in our data)

- work description
- work category
- State + Constituency (coarse location proxy — not GPS)
- MP / IDA
- amount
- date

## Pipeline

```text
Description
    ↓
Embedding (Sentence-BERT)
    ↓
Similarity search
    ↓
Same State + Constituency check   ← proxy for "location," not true GIS proximity
    ↓
Cost similarity
    ↓
Time overlap
    ↓
Duplicate probability
```

## Output

```text
Possible duplicate

NLP similarity: 92%
Same constituency: yes
Cost similarity: 89%

Overall:
91%
```

Be explicit in the demo that "location similarity" here means *same constituency*, not GPS proximity — we don't have coordinates. Don't imply more precision than the data supports.

---

---

## 🔮 DEFERRED BLOCK — Modules 6, 7, 8 (Sections 8–16)

Everything from here to Section 17 (Document Intelligence, Document Similarity, and all six Image Verification checks) is **kept in this document as a designed-but-not-built roadmap**, not part of the SIH MVP. Reason: zero real document or image data exists in the current MPLADS export (see the Scope Lock note at the top of this file). Do not schedule engineering time against these sections unless the team explicitly decides to build a small, clearly-labeled synthetic demo — and if so, say "synthetic" out loud on every slide and screen that shows it.

---

# 8. AI Module 6 — Document Intelligence *(🔮 deferred)*

## Objective

Understand and cross-check project documents.

## Pipeline

```text
PDF/Image
   ↓
OCR
   ↓
Document Classification
   ↓
Field Extraction
   ↓
Entity Normalization
   ↓
Cross-document Comparison
```

## Extract

- Project ID
- Work description
- Amount
- Date
- Authority
- Agency
- Milestone
- Certificate number
- Vendor
- Reference numbers

## Cross-check

```text
Sanction
   ↕
Work Order
   ↕
Invoice
   ↕
Payment
   ↕
Completion Certificate
```

## Output

> ⚠️ Completion certificate amount differs from verified expenditure.

---

# 9. AI Module 7 — Document Similarity *(🔮 deferred)*

Detect:

- reused certificates
- duplicated reports
- repeated wording
- template manipulation
- near-identical documents

Methods:

- text embeddings
- document fingerprints
- similarity search
- structured field comparison

Output:

> **Potentially reused certificate detected across 7 projects.**

---

# 10. AI Module 8 — Image Verification *(🔮 deferred)*

Designed in full for the Phase 2 roadmap. Not part of the SIH MVP — see the deferred-block note above §8.

## Objective

Determine whether submitted evidence is consistent with:

- project
- location
- milestone
- expected asset
- previous evidence

## Inputs

- Image
- Project ID
- Expected asset
- GPS
- Timestamp
- Milestone
- Previous images

---

# 11. Image Check A — Location *(🔮 deferred)*

Compare:

```text
Project GPS
      ↓
Image GPS
      ↓
Distance
```

Output:

> ⚠️ Image captured 18.7 km from registered project location.

If metadata is unavailable:

> Location verification unavailable.

Do not fabricate certainty.

---

# 12. Image Check B — Reuse *(🔮 deferred)*

Methods:

### Perceptual hashing

Good for near-identical images.

### Image embeddings

Good for visually similar images.

### Vector search

Find nearest images across the project database.

Output:

```text
Similarity:
99.4%

Possible reused evidence.
```

---

# 13. Image Check C — Wrong Asset *(🔮 deferred)*

Compare expected:

> Community Hall

against visual classification.

Potential output:

> ⚠️ Image appears inconsistent with declared asset type.

This is a risk signal, not a final verdict.

---

# 14. Image Check D — Progress *(🔮 deferred)*

Build project-specific visual stages.

Example:

```text
1. Site preparation
2. Foundation
3. Structure
4. Roofing
5. Services
6. Finishing
7. Completion
```

AI estimates an observed stage.

Example:

```text
Reported stage:
6 / 7

Visual signal:
3 / 7

→ Major inconsistency
```

This is feasible for selected project categories in an MVP if the visual taxonomy is controlled.

---

# 15. Image Check E — Temporal Consistency *(🔮 deferred)*

Compare:

- capture time
- upload time
- previous evidence
- milestone dates

Detect:

- image older than milestone
- repeated image over long intervals
- inconsistent sequence

---

# 16. Image Check F — Manipulation Signals *(🔮 deferred)*

Potential signals:

- metadata anomalies
- compression inconsistency
- editing traces
- inconsistent regions
- duplicated regions

Important:

> This should be presented as **image integrity risk**, not definitive deepfake detection.

Advanced forensic detection is a future scope item.

---

# 17. AI Module 9 — Financial Intelligence

## Objective

Find unusual financial patterns.

## Detect

### Amount anomalies

Payment unusually large/small.

### Timing anomalies

Payment unusually close to deadline.

### Frequency anomalies

Many payments in a short time.

### Duplicate payment

Same reference/amount/vendor.

### Split-payment patterns

Many payments just below a threshold.

### Vendor concentration

One vendor receives unusually large share.

### Budget-component mismatch

Component budget ≠ component spending.

---

# 18. AI Module 10 — Financial vs Status Intelligence *(MVP — redefined for real data)*

This should be a core feature — but "Physical Progress %" was originally scoped assuming visual/inspection data we don't have. Redefine using fields that actually exist: `Work Status` (Sanctioned/In Progress/Completed) from `Works_Sanctioned.csv`, cross-referenced with cumulative disbursed amount from `Expenditure.csv`.

Calculate:

```text
Financial Progress  (disbursed ÷ sanctioned amount)
vs
Status Progress     (crude proxy: "Completed" = 100%, "In Progress" = 50%, else 0%)
```

Example:

```text
Financial: 88%
Status: "In Progress" → 50% proxy

Gap: 38 percentage points
```

Large unexplained gaps increase risk — this is your "zombie project" signal (high spend, no completion), and it's fully backed by real data. Label the status-proxy honestly in the UI as an approximation, not verified physical progress.

---

# 19. AI Module 11 — Graph Intelligence

## Graph entities *(real-data version — Document/Image/Officer dropped, none exist in our export)*

```text
MP
PROJECT (Work)
STATE / CONSTITUENCY
AGENCY (IDA)
VENDOR
PAYMENT
```

## Edges

```text
MP → recommends → Project
Project → assigned_to → Agency (IDA)
Agency → uses → Vendor
Vendor → receives → Payment
Project → located_in → State/Constituency
```

This is the module that's already validated on real data — see the "Ajay Kumar Singh" finding in the technical build guide: 119 near-identical payments to one vendor from one MP, ~10x the 99th-percentile vendor concentration across the whole Lok Sabha expenditure dataset. This is your strongest, fully-real demo case. Lead with it.

## Detect

- unusually central vendors
- repeated entities
- project clusters
- shared evidence
- unusual cross-district relationships
- possible related entities

---

# 20. AI Module 12 — Risk Aggregation

All MVP modules feed a common risk engine. (Document Risk and Image Risk removed from the live formula — deferred, see Scope Lock. Re-add them here once real evidence data exists.)

```text
Financial Risk       25%
      +
Timeline Risk        20%
      +
Compliance Risk      20%
      +
Duplicate Risk       15%
      +
Graph/Agency Risk    20%
      ↓
TOTAL RISK (0–100)
```

Example, using the real vendor-concentration case:

```text
PROJECT RISK = 79/100

Financial (payment structuring pattern)   24
Graph (vendor concentration, 10x 99th pctile)  20
Compliance (works below Rs.2.5L threshold)     18
Timeline                                        9
Duplicate                                       8
```

---

# 21. AI Module 13 — Explanation Engine

The AI must answer:

> **Why is this project risky?**

It should retrieve the actual structured evidence.

Example, using only real-data signals:

> "This vendor has a risk score of 79 because it received 119 payments from a single MP — roughly 10x the volume of the 99th-percentile vendor across the entire Lok Sabha dataset — with unusually uniform amounts (~₹20,000 each, minimal variance), a pattern consistent with fund structuring below scrutiny thresholds."

Every statement should link back to a real, queryable data point — no invented evidence.

---

# 22. AI Module 14 — AI Audit Copilot

This is an interface over the structured system.

Examples:

### Query

> Show works where disbursed amount is above 80% of sanctioned but status is still "In Progress."

### Query

> Why is this vendor high risk?

### Query

> Which MPs have the highest share of works below the ₹2.5 lakh sanction threshold?

### Query

> Which vendors are associated with the most high-risk works?

### Query (deferred — needs document data)

> ~~Show projects with repeated completion certificates.~~ *Not possible until Document Intelligence ships — no certificate data exists yet.*

The LLM should query structured data rather than hallucinate.

---

# 23. AI Module 15 — Predictive Risk

Future risk predictions:

### Completion prediction

> Probability of missing deadline.

### Cost overrun prediction

> Probability of exceeding sanctioned amount.

### Stalling prediction

> Probability that a project becomes inactive.

### Evidence risk

> Probability that upcoming milestone submission will be inconsistent.

---

# 24. Custom AI Does NOT Need to Mean “Train an LLM From Scratch”

A legitimate custom AI system can be:

```text
Domain Rules
+
Custom Features
+
ML Models
+
NLP Models
+
Vision Models
+
Graph Algorithms
+
Risk Aggregation
+
Domain-Specific Explanation
```

The value is in the **domain-specific system**, not in training a foundation model from zero.

---

# 25. AI 20/80 Split

## AI can accelerate ~20%

AI-assisted development can rapidly generate:

- APIs
- database models
- UI
- preprocessing
- ML pipelines
- embedding search
- OCR pipelines
- image similarity
- charts
- synthetic data

## The team still owns ~80%

Humans must decide:

- what constitutes risk
- thresholds
- domain rules
- evidence requirements
- acceptable false positives
- model validation
- data strategy
- system architecture
- governance
- deployment

---

# 26. Model Validation Strategy

Because real fraud labels are limited:

## Do not claim:

> 98% fraud detection accuracy.

Instead validate:

### Rule correctness

Does the rule correctly identify known violations?

### Synthetic attack tests

Create controlled examples:

- duplicate payment
- reused image
- inflated amount
- false progress

### Historical audit cases

Where possible, reproduce patterns from CAG findings.

### Ranking quality

Measure:

> Are known/high-risk cases appearing near the top?

This is more meaningful for an investigation-prioritization system.

---

# 27. Synthetic Attack Generator

A powerful development tool:

```text
REAL WORK RECORD
     ↓
ATTACK GENERATOR (structured-data only — MVP scope)
     ├── Inflate cost vs. category median
     ├── Change recommend→sanction date gap
     ├── Delay completion beyond 1 year
     ├── Alter amount below Rs.2.5L threshold (splitting)
     ├── Duplicate work description in same constituency
     └── Create artificial vendor-payment concentration
     ↓
AI
     ↓
Can it detect the attack?
```

("Duplicate image" / "Duplicate document" attacks removed — deferred along with the modules they'd test.) This can become a strong SIH demo precisely because every attack type above is something the AI can actually be shown catching, live, on real data.

---

# 28. Recommended MVP AI Stack *(real-data only)*

## Must build

### Financial

- Robust statistics (Modified Z-score / MAD)
- Isolation Forest
- Vendor concentration analysis (already validated — see §19 note)

### NLP

- Sentence embeddings (Sentence-BERT / all-MiniLM-L6-v2)
- Similarity search over work descriptions

### Compliance

- Deterministic rule engine against MPLADS Guidelines 2023 thresholds (₹2.5L minimum, 45-day sanction SLA, 1-year completion norm, SC/ST quotas, prohibited categories)

### Timeline

- Rule-based delay detection (recommend→sanction, sanction→completion gaps)
- Simple prediction model (optional, if time allows)

### Risk

- Weighted aggregation (5 components, see §20)
- Explainable reason generator — plain-language, cites the actual data field that triggered each flag

---

# 29. Strong Bonus *(if time allows, still real-data only)*

### Graph

- NetworkX — HHI-style agency/vendor concentration scoring
- Full bipartite graph visualization in the dashboard

### AI Copilot

- LLM + retrieval over the structured risk-engine output (not raw documents — none exist yet)
- SQL/function calling against the cleaned CSVs

---

# 29b. Phase 2 / Future *(explicitly out of SIH MVP scope)*

- Document Intelligence (OCR, cross-document consistency, forgery signals) — needs real document data MoSPI doesn't currently expose
- Image Verification (reuse detection, GPS/timestamp checks, progress-stage CV, manipulation signals) — needs real image data MoSPI doesn't currently expose
- Advanced predictive risk models requiring longer historical time series
- Satellite imagery cross-verification

State this plainly in the pitch as a roadmap item, not a gap in your team's ability — the data simply isn't public yet.

---

# 30. AI Safety / Governance

The AI must:

- avoid accusing individuals
- show evidence
- show uncertainty
- record model version
- record rule/model that triggered alert
- allow human override
- maintain audit history

Every prediction should have:

```text
Model version
Timestamp
Input snapshot
Risk score
Reasons
Confidence / uncertainty
```

---

# 31. Final AI Architecture

```text
              MPLADS DATA (structured CSVs, real)
                         │
                         ↓
                  FEATURE ENGINE
                         │
                         ↓
               ┌──────────────────┐
               │   AI ENGINES     │
               │                  │
               │ Financial        │
               │ Timeline         │
               │ Compliance Rules │
               │ Duplicate (NLP)  │
               │ Graph (Vendor/   │
               │   Agency HHI)    │
               │ Prediction ⭐    │
               └────────┬─────────┘
                        ↓
                  RISK ENGINE
                        ↓
              EXPLANATION ENGINE
                        ↓
                AI COPILOT ⭐
                        ↓
                 OFFICER UI
                        ↓
                  CASE OUTCOME
                        ↓
                    FEEDBACK

   ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄
   🔮 Phase 2 (not wired in until real data exists):
   DOCUMENTS → OCR/NLP → Document AI ─┐
   IMAGES    → CV       → Vision AI  ─┴→ feeds into RISK ENGINE above
   ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄
```

---

# 32. Ultimate AI Objective

The custom AI should answer four questions:

### 1. **What is unusual?**

> Anomaly detection.

### 2. **Why is it unusual?**

> Explainability.

### 3. **How serious is it?**

> Risk scoring.

### 4. **What should be investigated first?**

> Prioritization.

That is the real purpose of the AI system.

---

# 33. Final Principle

> **The AI should never replace evidence. It should connect evidence.**

The winning system is not:

> **“AI says fraud.”**

It is:

> **“AI found an inconsistency, here are the independent signals, here is the underlying evidence, and here is why this case should be investigated first.”**
