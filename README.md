# 🛡️ MPLADS Sentinel (रक्षक)
### *AI-Powered Anomaly, Fraud & Inefficiency Detection Layer for eSAKSHI*

[![Smart India Hackathon 2026](https://img.shields.io/badge/SIH-2026-orange.svg)](https://sih.gov.in)
[![Problem Statement ID](https://img.shields.io/badge/PS%20ID-SIH26102-blue.svg)](https://sih.gov.in/sih2026PS)
[![Ministry](https://img.shields.io/badge/Ministry-MoSPI%20(DIID)-green.svg)](https://www.mospi.gov.in)
[![Category](https://img.shields.io/badge/Category-Software%20%7C%20Miscellaneous-purple.svg)](https://sih.gov.in)
[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)

---

## 🏛️ Executive Summary

Under the **Members of Parliament Local Area Development Scheme (MPLADS)**, Hon’ble MPs recommend developmental works to create durable community assets with an entitlement of **₹5.00 Crore per MP per year** (₹4,000+ Crore annually across 790+ MPs).

While MoSPI modernized transaction workflows via the **eSAKSHI portal** and the **Central Nodal Agency (CNA)** model, monitoring 18,000+ simultaneous works across 700+ districts remains a manual, post-facto challenge.

**MPLADS Sentinel (रक्षक)** is an **Explainable AI (XAI) & Audit Intelligence Layer** that analyzes multi-year developmental projects, detects cost/timeline/cartel anomalies, and provides District Collectors and CAG auditors with **prioritized, evidence-backed investigation dossiers**.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           CORE STRATEGIC POSITIONING                        │
│                                                                             │
│  "eSAKSHI is the system of record—it captures WHAT has happened.             │
│   MPLADS Sentinel is the intelligence layer—it prioritizes WHAT requires    │
│   human investigation, WHY it is anomalous, and WHERE auditors must look." │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📂 Repository File Directory Map

All project assets, official datasets, statutory guidelines, case studies, and presentation decks are systematically organized:

| # | File Name | Category | Description |
| :-: | :--- | :---: | :--- |
| **1** | [**`index.html`**](file:///d:/Clg/SIH%2726/index.html) | 🌐 **Web Portal** | Modern interactive browser portal with Markdown reader, CSV explorer, and repository hub at `http://localhost:8000`. |
| **2** | [**`SIH26102_Official_6_Slide_PPT_Deck.md`**](file:///d:/Clg/SIH%2726/SIH26102_Official_6_Slide_PPT_Deck.md) | 🎯 **Presentation** | Strict 6-slide SIH template PPT deck with complete slide text, tables, and a 3-minute pitch script (matches *Chakravyuh* format). |
| **3** | [**`SIH26102_Comprehensive_12_Slide_Presentation_Deck.md`**](file:///d:/Clg/SIH%2726/SIH26102_Comprehensive_12_Slide_Presentation_Deck.md) | 🎯 **Presentation** | In-depth 12-slide master deck with full speaker notes, risk formulas, and feasibility analysis. |
| **4** | [**`SIH_Sample_6_Slide_PPT_Chakravyuh.pdf`**](file:///d:/Clg/SIH%2726/SIH_Sample_6_Slide_PPT_Chakravyuh.pdf) | 🎯 **Sample PPT** | Official benchmark presentation PDF from SIH'25 demonstrating the ideal 6-slide visual layout. |
| **5** | [**`MASTER_EXECUTION_GUIDE.md`**](file:///d:/Clg/SIH%2726/MASTER_EXECUTION_GUIDE.md) | 🛠️ **Tech Guide** | Master technical blueprint with SQLite DDL, 5-Pillar Python risk engine code, FastAPI routes, and judge defense. |
| **6** | [**`MPLADS_Sentinel_Free_AI_Agent_Build_Guide.md`**](file:///d:/Clg/SIH%2726/MPLADS_Sentinel_Free_AI_Agent_Build_Guide.md) | 🛠️ **AI Guide** | Step-by-step guide and working Python scripts for an autonomous, 100% free AI investigation agent using local Ollama LLMs and FAISS RAG. |
| **7** | [**`Official_MPLADS_Allocated_Limit_Dataset.csv`**](file:///d:/Clg/SIH%2726/Official_MPLADS_Allocated_Limit_Dataset.csv) | 📊 **Official Dataset** | The official dataset provided: 544 Lok Sabha MP allocations across 37 States/UTs totaling **₹8,306.21 Crore**. |
| **8** | [**`MPLADS_12_Stage_Financial_Workflow.md`**](file:///d:/Clg/SIH%2726/MPLADS_12_Stage_Financial_Workflow.md) | 📊 **Workflow** | End-to-end mapping of the 12-stage MPLADS financial lifecycle from recommendation to asset handover. |
| **9** | [**`MPLADS_Data_Sources_and_Gaps_Overview.md`**](file:///d:/Clg/SIH%2726/MPLADS_Data_Sources_and_Gaps_Overview.md) | 📊 **Research** | Evaluation of data sources (eSAKSHI, Dataful.in, CAG), data gaps (no GPS/labels), and mentor strategies. |
| **10** | [**`Official_MPLADS_Guidelines_2023.pdf`**](file:///d:/Clg/SIH%2726/Official_MPLADS_Guidelines_2023.pdf) | 📜 **Statutory Rules** | Official revised 2023 Guidelines: CNA model, SBI Zero-Balance Accounts, 15% SC & 7.5% ST earmarking, and prohibited assets. |
| **11** | [**`CAG_Compliance_Audit_Case_Study.pdf`**](file:///d:/Clg/SIH%2726/CAG_Compliance_Audit_Case_Study.pdf) | 📜 **Case Study** | Ground-truth CAG audit findings: work splitting below ₹10L, unspent balance parking, delayed execution, and lack of inspections. |
| **12** | [**`SIH26102_Deep_Dive_Problem_Analysis.md`**](file:///d:/Clg/SIH%2726/SIH26102_Deep_Dive_Problem_Analysis.md) | 📜 **Deep Dive** | In-depth breakdown of the 6 anomaly classes, research inspirations (arXiv procurement fraud), and competitor matrix. |
| **13** | [**`SIH_2026_All_Problem_Statements_Directory.md`**](file:///d:/Clg/SIH%2726/SIH_2026_All_Problem_Statements_Directory.md) | 📜 **SIH Directory** | Complete master index of all 226 Smart India Hackathon 2026 problem statements across 30 ministries. |

---

## 🧠 The 5-Pillar AI Risk Engine

```
                                  INGESTED DATASETS
            (Official Allocated Limit CSV + eSAKSHI Reports + Dataful.in)
                                         │
    ┌────────────────┬───────────────────┼───────────────────┬────────────────┐
    ▼                ▼                   ▼                   ▼                ▼
[ Pillar 1: NLP ] [ Pillar 2: Stats ] [ Pillar 3: Graph ] [ Pillar 4: Rules ][ Pillar 5: XAI ]
Sentence-BERT     Isolation Forest &  Bipartite Network   2023 Guidelines    SHAP Attribution
Embeddings for    Robust Z-Score for  HHI for Agency      Engine (SC/ST,     & Dynamic Audit
Duplicates        Cost/Progress Lag   Monopolies          Prohibitions)      Evidence Cards
    │                │                   │                   │                │
    └────────────────┴───────────────────┼───────────────────┴────────────────┘
                                         ▼
                        COMPOSITE RISK SCORING ENGINE (0–100)
                                         │
                                         ▼
                             AUDITOR COMMAND CENTER
                     (FastAPI Backend + React/Next.js UI)
```

1. **Pillar 1 — Multilingual NLP Duplicate Matcher:** Uses `sentence-transformers/all-MiniLM-L6-v2` dense vector embeddings to flag re-sanctioned and split works (`<₹10L`) across fiscal years.
2. **Pillar 2 — Unsupervised Cost & Timeline Anomaly ML:** `IsolationForest` and Modified Z-scores benchmark unit costs against local district medians and flag high-disbursement / low-progress zombie projects.
3. **Pillar 3 — Bipartite Graph Cartel Intelligence:** `NetworkX` calculates the Herfindahl-Hirschman Index (HHI) to detect contractor and implementing agency monopolies.
4. **Pillar 4 — Statutory Rule Compliance:** Enforces the official 2023 Guidelines (15% SC / 7.5% ST allocation quotas and Annexure-I non-permissible asset filters).
5. **Pillar 5 — Explainable AI (XAI) & RAG Copilot:** Combines SHAP feature attribution with FAISS vector retrieval over the official Guidelines and CAG audit PDFs to produce cited investigation briefs.

---

## 🚀 Quickstart & Local Setup

### 1. Clone & Setup Python Environment
```bash
# Clone the repository
git clone https://github.com/akshhq/SIH-26.git
cd SIH-26

# Activate virtual environment
.venv\Scripts\activate      # Windows
# source .venv/bin/activate # Linux / macOS

# Install core dependencies
pip install pandas numpy scikit-learn sentence-transformers networkx fastapi uvicorn pydantic faiss-cpu pypdf requests ollama
```

### 2. Run the Web Portal
```bash
# Start local HTTP server on port 8000
python -m http.server 8000
```
Open **[http://localhost:8000](http://localhost:8000)** in your browser to view the interactive portal, read markdown docs, and explore the 544 MP allocations dataset.

---

## 🏆 Key Impacts & Societal Benefits
* **💰 Fiscal Protection:** Prevents fund diversion, repeated billings, and unauthorized fund parking. In a state with ₹500 Cr annual funds, identifying 3% leakage saves **₹15 Crore annually** (enough for 150+ rural Anganwadis).
* **🏛️ 80% Audit Workload Reduction:** Shifts CAG and District Collectors from random sample checks to targeted, high-risk triage.
* **👥 Faster Asset Delivery:** Unblocks stalled community projects and guarantees mandatory SC/ST fund flow on the ground.

---
*Developed for Smart India Hackathon 2026 | Ministry of Statistics and Programme Implementation (MoSPI)*
