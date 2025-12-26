# Automatic Prediction and Evaluation of Aesthetic Outcomes in Plastic and Oncological Surgery: A Systematic Review

**Authors:** Helena Montenegro*†, Mohammad Hossein Zolfagharnasab†, Fábio Teixeira‡, Gonçalo da Costa Sequeira Pinto‡, Joana Santos‡, Pedro Ferreira‡, Eduard-Alexandru Bonci, Carlos Mavioso, Maria J. Cardoso, Jaime S. Cardoso  
**Corresponding author:** `maria.h.sampaio@inesctec.pt`  
†‡ Equal contribution

---

## 1. What This Repository Contains

This repository is the **full PRISMA audit trail** for the systematic review:

> **Automatic Prediction and Evaluation of Aesthetic Outcomes in Plastic and Oncological Surgery: A Systematic Review On Current Progress, Challenges, and Future Directions**

It is designed to make the review **transparent, reproducible, and verifiable**, by providing:

- The **complete PRISMA screening pipeline** *(raw retrieval → duplicate removal → title/abstract/full-text screening → qualitative screening → final included studies)*
- A **file-level record** of every inclusion/exclusion decision *(stored in CSVs at each stage)*
- Statistical and qualitative artifacts used in the manuscript *(figures + evidence synthesis files)*

The repository aligns with the manuscript’s goals:
- Review SoTA methods for **aesthetic outcome prediction** and **evaluation**
- Organize datasets/benchmarks/models used in the field
- Identify cross-domain overlaps *(facial/breast/oncological/other body regions)*
- Highlight limitations *(data access, heterogeneity, validation gaps)*
- Discuss clinical integration barriers and future directions *(e.g., multimodal models)*

---

## 2. PRISMA Overview (Audit Trail Entry Point)

This review follows the PRISMA framework:
- **Identification**
- **Screening**
- **Eligibility**
- **Inclusion**

The diagram below summarizes **how records move through the pipeline**, showing both retained counts and where exclusions occur. Every box is backed by the CSV outputs stored under `prisma/`.

![PRISMA workflow](figs/prisma.jpg)

### How to interpret the PRISMA diagram in this repo
- **Top boxes (Identification):** records collected from databases + additional/manual sources  
- **Central vertical path:** records *retained* after each stage  
- **Right-side boxes:** records *excluded* at each stage (with a stage-specific reason category)  
- **Final box:** the **included corpus** used for synthesis (candidate papers + summaries)

---

## 3. Search Strategy (How Studies Were Found)

### Data Sources
- Scopus  
- PubMed  
- IEEE Xplore  
- Semantic Scholar  
- Manual backward reference search *(bibliographies of included works)*

### Two Complementary Search Tracks
To reflect the dual clinical challenge emphasized in the paper—**pre-operative expectation management** (prediction) and **post-operative standardized assessment** (evaluation)—we conducted two focused searches:

1) **Prediction of aesthetic outcomes** *(simulation / post-op prediction / outcome prediction)*  
2) **Evaluation of aesthetic outcomes** *(assessment / scoring / objective evaluation)*

Exact queries are reported verbatim in the manuscript to ensure full reproducibility.

---

## 4. What the High-Level Statistics Say (Before You Dive into CSVs)

This section explains what each figure means and *why it matters* for interpreting the review.

### 4.1 Temporal trend of the field (Prediction vs. Evaluation)

![Trend by year](figs/trend_by_year.png)

**What this figure shows**
- The number of retrieved and retained studies per year, split into two pipelines: **prediction** and **evaluation**.

**How to read it**
- The y-axis is the number of documents; the x-axis is publication year.
- Two curves indicate how research attention evolved across time for each task.

**Why it matters (interpretation)**
- **Evaluation dominates earlier years**: many evaluation studies rely on objective measurements or smaller-scale classical ML, historically more feasible than outcome simulation.
- **Prediction grows strongly in later years**: consistent with the rise of deep learning, generative methods, and improved 3D processing pipelines.
- This trend supports the paper’s taxonomy split and motivates separate discussion of prediction vs. evaluation validation practices.

---

### 4.2 Where the articles came from (database contribution)

![Distribution per source](figs/distribution_per_source.png)

**What this figure shows**
- Relative contribution of each database/source to the retrieved corpus (after harmonization/cleaning).

**How to read it**
- Each slice is one source; the percentage indicates its share of records.

**Why it matters (interpretation)**
- **Scopus** provides broad indexing coverage and the largest share of records.
- **Semantic Scholar** contributes substantial complementary coverage, often capturing preprints/metadata variations that help discovery.
- **Manual search** is smaller but important: it targets references in included works and reduces the chance of missing “hidden” relevant studies.
- This figure justifies multi-source retrieval as a strategy against single-index bias.

---

### 4.3 Interdisciplinary footprint (prediction vs evaluation domains)

![Distribution per category](figs/distribution_per_category.png)

**What this figure shows**
- The disciplinary distribution of records for prediction and evaluation tracks.

**How to read it**
- Two plots summarize which publication areas dominate each track (e.g., Engineering, Computer Science, Medicine).

**Why it matters (interpretation)**
- Prediction and evaluation are **inherently interdisciplinary**, but the balance differs:
  - **Engineering + Computer Science** dominate both tracks, matching the review’s focus on computational methods.
  - **Medical/clinical domains** appear more strongly in evaluation, reflecting the need for clinically meaningful assessment and validation.
- This helps explain differences in typical datasets, validation protocols, and outcome reporting standards between prediction and evaluation studies.

---

### 4.4 Keyword co-occurrence (topic structure of the retained literature)

![Co-occurrence graph](figs/co-occurance_graph.png)

**What this figure shows**
- A network of keywords extracted from retained studies, where edges represent frequent co-occurrence (keywords appearing together in the same record).

**How to read it**
- **Node size** approximates keyword prominence in the corpus.
- **Edges** connect keywords that co-appear often.
- **Clusters/colors** indicate sub-communities (topics that commonly appear together).

**Why it matters (interpretation)**
- The graph exposes how the field organizes around:
  - **Core AI/ML concepts** (e.g., deep learning, classification, neural networks)
  - **Clinical domains** (e.g., breast cancer, plastic surgery, reconstruction)
  - **Task framing** (evaluation vs prediction vs simulation)
- It also highlights cross-domain transfer opportunities:
  - Shared representations/metrics across breast/facial domains
  - Overlap between “objective assessment” and learning-based scoring pipelines
- Practically, this figure is a compact map of the review’s taxonomy backbone.

---

### 4.5 Word cloud (dominant vocabulary after filtering)

![Word cloud](figs/word_cloud.png)

**What this figure shows**
- The most frequent and characteristic terms in the retained corpus (after screening stages).

**How to read it**
- Larger words appear more frequently across titles/abstracts/metadata (depending on how the corpus was tokenized).

**Why it matters (interpretation)**
- It acts as a “scope sanity check”: the dominant terms (e.g., image, assessment, prediction, deep, facial, surgery) confirm that the final corpus remains centered on imaging-based aesthetic outcome prediction/evaluation.
- It also reflects the paper’s observation of increasing AI presence (deep/model/network terms remain visually prominent).

---

## 5. PRISMA Flow Numbers (Backed by Files)

| Stage | Records |
|------|--------:|
| Identified | 1,027 |
| After duplicate removal | 939 |
| After title screening | 744 |
| After abstract screening | 386 |
| Full-text assessed | 250 |
| After qualitative screening | 182 |
| Final included | 182 (102 main + 85 supplementary) |

All transitions are reproducible using the stage outputs in `prisma/`.

---

## 6. PRISMA Screening Stages (What Each Folder Represents)

This section explains **what happened at each stage**, **why it is necessary**, and **which files record the decisions**.

---

### 6.1 Stage 01 — Identification (`prisma/01_articles_per_source/`)

**Goal:** Build the *unfiltered* corpus from database search + manual retrieval.

**Core file**
- `articles.csv` — raw retrieved records (title, abstract, DOI when available, year, venue, source)

**What to expect inside**
- Mixed quality/coverage: duplicates, off-topic records, partially missing metadata, and borderline titles are normal at this stage.
- This stage prioritizes recall (finding “everything possibly relevant”) over precision.

**How it connects to figures**
- The temporal and source distributions originate from this corpus and then become more meaningful as screening progresses:
  - ![Trend by year](figs/trend_by_year.png)
  - ![Distribution per source](figs/distribution_per_source.png)

---

### 6.2 Stage 02 — Duplicate Removal (`prisma/02_duplicate_removal/`)

**Goal:** Remove duplicate studies to prevent double counting and biased synthesis.

**Files**
- `articles_duplicate_marked.csv` — all detected duplicates flagged  
- `articles_rejected_by_duplicacy.csv` — duplicates removed  
- `articles_after_duplicates.csv` — unique record set after cleanup  
- `articles_categorized.csv` — intermediate organization/categorization artifact (if used in your pipeline)

**How duplicates were detected**
- DOI matching (primary, most reliable)
- Normalized title similarity (fallback when DOI missing or inconsistent across sources)

**Why it matters**
- A paper indexed in multiple sources can appear as multiple rows with slight metadata differences.
- Duplicate removal ensures that database contribution and yearly trends do not reflect indexing artifacts.

**How it connects to figures**
- Source contribution becomes interpretable only after duplicates are handled:
  - ![Distribution per source](figs/distribution_per_source.png)

---

### 6.3 Stage 03 — Title Screening (`prisma/03_title_screening/`)

**Goal:** Remove clearly out-of-scope records while retaining uncertain ones for abstract screening.

**Files**
- `articles_titles_screened_marked.csv` — decision flag per record  
- `articles_rejected_by_titles.csv` — removed based on title only  
- `articles_after_title_screening.csv` — retained records

**Operational scope rule (applied consistently)**
Include if the title indicates relevance to at least one of:
- plastic / reconstructive / oncological surgery context
- aesthetic outcome (appearance, attractiveness, cosmetic outcome, symmetry, etc.)
- technical method framing (ML/AI, simulation, modeling, measurement, scoring)

Exclude if clearly about:
- non-surgical aesthetic interventions (e.g., fillers)
- unrelated outcomes (no aesthetic/appearance component)
- non-technical or out-of-scope domains

**Why it matters**
- Title screening reduces workload for deeper screening while intentionally remaining conservative to avoid premature exclusion.

---

### 6.4 Stage 04 — Abstract Screening (`prisma/04_abstract_screening/`)

**Goal:** Enforce methodological relevance and lock the review’s core task framing.

**Files**
- `articles_abstract_screened_marked.csv`  
- `articles_rejected_by_abstract.csv`  
- `articles_after_abstract_screening.csv`

**Core inclusion logic (operationalized)**
- Must target prediction or evaluation of aesthetic outcomes
- Must use imaging (2D or 3D); exclude purely tabular/text-only approaches
- Exclude works with insufficient technical novelty (purely clinical narratives without method contribution)
- Exclude off-target outcomes (psychological impact only, satisfaction without computational assessment, etc.)

**Why it matters**
- Abstract screening is where the taxonomy stabilizes (prediction vs evaluation, imaging-based focus).
- It separates “about surgery aesthetics” from “computational methods for surgical aesthetics.”

**How it connects to figures**
- The interdisciplinary distribution becomes meaningful at this stage:
  - ![Distribution per category](figs/distribution_per_category.png)

---

### 6.5 Stage 05 — Full-Text Screening (`prisma/05_fulltext_screening/`)

**Goal:** Confirm eligibility using full-text evidence and ensure the paper adds perceptible value to the review.

**Files**
- `articles_full-text_screened_marked.csv`  
- `articles_rejected_by_full-text.csv`  
- `articles_after_full-text_screening.csv`

**Full-text eligibility checks include**
- Clear technical contribution beyond descriptive reporting
- Adequate evaluation design (metrics, baselines, or validation protocol)
- Alignment with imaging-based prediction/evaluation
- Relevance to surgical aesthetic outcomes (PR/oncological contexts)
- Sufficient methodological detail to enable meaningful comparison in synthesis

**Why it matters**
- Full-text screening protects the review from “false positives” that looked relevant in abstracts but do not contribute substantively.

**How it connects to figures**
- The keyword network reflects the conceptual structure of the retained, eligible literature:
  - ![Co-occurrence graph](figs/co-occurance_graph.png)

---

### 6.6 Stage 06 — Qualitative / Quality Screening (`prisma/06_qualitive_fulltext_qualitive/`)

**Goal:** Apply a structured quality filter so the final synthesis is based on robust, interpretable studies.

**Files**
- `articles_qualitive_screened_marked.csv`  
- `articles_rejected_by_quality.csv`  
- `articles_after_qualitive_screening.csv`

**Quality dimensions (applied consistently)**
- Novelty (not purely incremental)
- Technical rigor (method clarity, soundness, reproducibility)
- Dataset adequacy (size, representativeness, availability)
- Evaluation validity (metrics appropriateness, validation setup, clinical relevance)
- Practical relevance to prediction/evaluation tasks and surgical workflow

**Why it matters**
- Many studies report promising results but lack comparable metrics, robust validation, or dataset transparency.
- This stage ensures the final corpus supports credible comparisons and grounded conclusions.

**How it connects to figures**
- The word cloud summarizes the dominant vocabulary of the post-quality corpus:
  - ![Word cloud](figs/word_cloud.png)

---

### 6.7 Stage 07 — Final Included Studies (`prisma/07_candidate_papers/`)

**Goal:** Provide the final list used in synthesis, tables, and discussion.

**File**
- `candidate_papers.csv`

**What it represents**
- The definitive “included studies” list backing:
  - method taxonomy
  - dataset/benchmark analysis
  - cross-domain comparison
  - limitations and future directions

---

### 6.8 Stage 08 — Evidence Synthesis (`prisma/08_summarized_texts/`)

**Goal:** Provide structured summaries used for comparison and narrative synthesis.

**Files**
- `combined_summs.xlsx` — master synthesis sheet  
- `summerized_per_tasks/` — task-wise synthesis:
  - `Prediction.csv`
  - `Evaluation.csv`
  - `Datasets.csv`
  - `Reviews.csv`
  - `Subjective Evaluation.csv`
  - `Support Tasks.csv`

**Why it matters**
- These files operationalize the review’s key contributions:
  - goal-oriented taxonomy
  - comparative analysis across methods and domains
  - identification of dataset and validation gaps
  - discussion-ready synthesis blocks

---

## 7. Reproducibility and Auditability (How to Verify Everything)

A third party can reproduce the PRISMA trajectory by following the folder order:

1. Start with `prisma/01_articles_per_source/articles.csv`
2. Apply duplicate removal → compare with `prisma/02_duplicate_removal/`
3. Apply title screening → compare with `prisma/03_title_screening/`
4. Apply abstract screening → compare with `prisma/04_abstract_screening/`
5. Apply full-text screening → compare with `prisma/05_fulltext_screening/`
6. Apply qualitative screening → compare with `prisma/06_qualitive_fulltext_qualitive/`
7. Confirm final included list → `prisma/07_candidate_papers/candidate_papers.csv`

Each “rejected” CSV provides an explicit audit trail of exclusions.

---

## 8. Protocol Registration Statement

This review was **not registered in PROSPERO** due to its strong emphasis on **computer science, engineering, and imaging-based computational methodologies**, which extends beyond PROSPERO’s primary biomedical scope.

Protocol transparency is ensured through:
- public release of the full screening trail
- immutable CSV decision logs
- explicit rejection sets at each stage

---

## 9. Repository Hierarchy (Full File Tree)

    review-paper tree
    ├── README.md
    ├── figs
    │   ├── co-occurance_graph.png
    │   ├── distribution_per_category.png
    │   ├── distribution_per_source.png
    │   ├── prisma.jpg
    │   ├── trend_by_year.png
    │   └── word_cloud.png
    └── prisma
        ├── 01_articles_per_source
        │   └── articles.csv
        ├── 02_duplicate_removal
        │   ├── articles_after_duplicates.csv
        │   ├── articles_categorized.csv
        │   ├── articles_duplicate_marked.csv
        │   └── articles_rejected_by_duplicacy.csv
        ├── 03_title_screening
        │   ├── articles_after_title_screening.csv
        │   ├── articles_rejected_by_titles.csv
        │   └── articles_titles_screened_marked.csv
        ├── 04_abstract_screening
        │   ├── articles_abstract_screened_marked.csv
        │   ├── articles_after_abstract_screening.csv
        │   └── articles_rejected_by_abstract.csv
        ├── 05_fulltext_screening
        │   ├── articles_after_full-text_screening.csv
        │   ├── articles_full-text_screened_marked.csv
        │   └── articles_rejected_by_full-text.csv
        ├── 06_qualitive_fulltext_qualitive
        │   ├── articles_after_qualitive_screening.csv
        │   ├── articles_qualitive_screened_marked.csv
        │   └── articles_rejected_by_quality.csv
        ├── 07_candidate_papers
        │   └── candidate_papers.csv
        └── 08_summarized_texts
            ├── combined_summs.xlsx
            └── summerized_per_tasks
                ├── Datasets.csv
                ├── Evaluation.csv
                ├── Prediction.csv
                ├── Reviews.csv
                ├── Subjective Evaluation.csv
                └── Support Tasks.csv
