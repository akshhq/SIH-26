# 📊 MPLADS Data Sources, Gaps & Mentor Strategy Blueprint
### *Problem Statement ID: SIH26102 | Ministry of Statistics and Programme Implementation (MoSPI)*

---

## 1. Primary Public Data Sources & Verification

| Data Source | Portal URL | Scope & Granularity | Strengths | Limitations & Gaps |
| :--- | :--- | :--- | :--- | :--- |
| **eSAKSHI Portal (Official)** | `mplads.mospi.gov.in` | Real-time portal active since April 1, 2023. Captures MP, District Authority, and IA logins. | Live transaction status, CNA Zero Balance Account payments, Maker-Checker tracking. | Pre-2023 historical data not digitized; no automated pattern detection layer. |
| **Official 18th LS Dataset** | [`Official_MPLADS_Allocated_Limit_Dataset.csv`](file:///d:/Clg/SIH%2726/Official_MPLADS_Allocated_Limit_Dataset.csv) | 544 Lok Sabha MPs across 37 States/UTs totaling **₹8,306.21 Crore**. | Contains actual 18th Lok Sabha baseline limits (₹14.70 Cr standard 3-tranche) and carryover balances. | Constituency-level entitlement snapshot; individual works require drill-down. |
| **Dataful.in Datasets** | `dataful.in/datasets/` | Comprehensive historical datasets (14th to 17th Lok Sabha). | Pre-cleaned tabular data: State/MP/Constituency works list, unspent balances, SC/ST expenditure. | Community compiled; requires cross-verification against government gazettes. |
| **CAG Compliance Audits** | [`CAG_Compliance_Audit_Case_Study.pdf`](file:///d:/Clg/SIH%2726/CAG_Compliance_Audit_Case_Study.pdf) | Historical compliance audits (e.g. CAG Report No. 4 of 2018). | **Authentic Ground Truth:** Documents actual modus operandi (work splitting $<₹10\text{L}$, unspent balance parking). | Conducted post-facto; sample-based test checks cover only ~10% of districts. |
| **PIB & Parliamentary Q&A** | `pib.gov.in` / `sansad.in` | Official parliamentary replies on state-wise pending works and unspent funds. | Qualitative administrative context on state-wise delay drivers. | Aggregated at state level; non-continuous. |

---

## 2. Required Input Fields vs. Feasible Extraction

```
┌────────────────────────────────────────────────────────┬──────────────────────────────────────────┐
│                   REQUIRED INPUT FIELD                 │            FEASIBLE DATA SOURCE          │
├────────────────────────────────────────────────────────┼──────────────────────────────────────────┤
│ 1. Unique Work ID, Description, Sector Category        │ eSAKSHI Work Details / Dataful Works List│
│ 2. Recommended Cost vs. Sanctioned Financial Limit     │ eSAKSHI AS/FS Orders                     │
│ 3. Cumulative Fund Disbursed vs. Physical Progress (%) │ eSAKSHI Milestone Tracking Reports       │
│ 4. Implementing Agency (IA) Name & Registration ID     │ eSAKSHI IA Assignment Records            │
│ 5. Geotagged Coordinates (Lat/Long)                    │ Text address parsing / Geocoding API     │
│ 6. Mandatory 15% SC / 7.5% ST Budget Allocation Flags  │ Constituency & Work Category Metadata    │
└────────────────────────────────────────────────────────┴──────────────────────────────────────────┘
```

---

## 3. Critical Data Gaps & Technical Mitigations

### 1️⃣ Absence of Ground-Truth "Fraud" Labels in Public Data
* **The Gap:** No government dataset contains a labeled column marked `"is_fraud = True"`.
* **Technical Mitigation:** Avoid supervised classifiers (which would hallucinate on unlabelled data). Instead, use an **Unsupervised Anomaly Detection & Triage Architecture**:
  * Isolation Forest & Modified Z-Scores for cost outliers.
  * Disparity-Lag indices for zombie projects.
  * Sentence-BERT dense vector embeddings for duplicate titles.

### 2️⃣ Inconsistent Geotagging & GPS Coordinates
* **The Gap:** Legacy works often lack standardized latitude/longitude coordinates.
* **Technical Mitigation:** Use NLP-driven **Semantic Text Similarity** + local administrative hierarchy matching (District + Block + Village/Ward) to detect duplicate or split works within identical administrative clusters.

### 3️⃣ Evolving Guidelines & Procedure Shifts
* **The Gap:** 2023 Guidelines introduced the CNA SBI Zero Balance Account model, replacing old district bank account parking.
* **Technical Mitigation:** Integrate an **Agentic RAG Engine** indexing both the [`Official_MPLADS_Guidelines_2023.pdf`](file:///d:/Clg/SIH%2726/Official_MPLADS_Guidelines_2023.pdf) and historical [`CAG_Compliance_Audit_Case_Study.pdf`](file:///d:/Clg/SIH%2726/CAG_Compliance_Audit_Case_Study.pdf) to ensure automated checks reflect contemporary rules.

---

## 4. Root Cause Analysis: Why Previous Monitoring Failed

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        WHY HASN'T THIS BEEN SOLVED AT SCALE BEFORE?                    │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Scale vs. Manual Capacity: CAG & District Authorities cannot manually review        │
│    18,000+ works across 700+ districts. Random sample checks cover only ~10% of works. │
│ 2. Digitization Without Intelligence: eSAKSHI digitizes records, but lacks automated   │
│    pattern-detection algorithms to flag cross-year anomalies or contractor cartels.    │
│ 3. Black-Box Rejection: Previous academic models produced unexplainable risk scores    │
│    that officers could not legally defend in court or PAC hearings.                    │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. Winning Strategy & Judge Defense Blueprint

1. **Explainability-First Framing:**  
   Position Sentinel as an **"Audit Prioritization & Triage Engine"** rather than an accusatory "fraud predictor". Every flag is backed by a verifiable Explainable AI (XAI) Evidence Card.
2. **Demonstrate Low-Risk Discrimination:**  
   Show judges that compliant, on-time works receive low risk scores (e.g. 25–35/100), proving the system is not generating false alarms or alert fatigue.
3. **Statutory & Empirical Grounding:**  
   Ground every rule in the official 2023 MoSPI Guidelines and actual CAG audit findings.
4. **Quantifiable ROI:**  
   In a state with ₹500 Cr annual funds, identifying just 3% leakage saves **₹15 Crore annually**—funds that directly build 150+ rural Anganwadis and health sub-centers.

---
*Maintained in `MPLADS_Data_Sources_and_Gaps_Overview.md` for SIH 2026 Problem Statement SIH26102.*