# PRISMA-Based Systematic Review Repository

**Transparent, Reproducible, and Auditable Literature Screening Pipeline**

---

## 1. Purpose of This Repository

This repository documents the complete **PRISMA 2020–compliant workflow** used in the associated systematic review on **prediction and evaluation of aesthetic surgical outcomes**.

The repository is designed to:

- Ensure **methodological transparency**
- Directly address **reviewer concerns on PRISMA reporting**
- Enable **file-level reproducibility** of all screening decisions
- Link **all figures** to their **underlying screened data**

Every inclusion and exclusion decision is explicitly logged and traceable.

---

## 2. PRISMA Overview

The review strictly follows the PRISMA 2020 framework:

- Identification
- Screening
- Eligibility
- Inclusion

The PRISMA flow diagram used in the manuscript summarizes the numerical transitions across these stages.

![PRISMA workflow](figs/prisma.png)

---

## 3. Search Strategy

### Databases

- Scopus
- PubMed
- IEEE Xplore
- Semantic Scholar
- Manual backward reference search

Two independent searches were conducted:

1. **Prediction of aesthetic outcomes**
2. **Evaluation of aesthetic outcomes**

Exact search strings are reported verbatim in the manuscript to ensure reproducibility.

---

## 4. PRISMA Flow Statistics

| Stage                       | Records                           |
| --------------------------- | --------------------------------- |
| Identified                  | 1,027                             |
| After duplicate removal     | 939                               |
| After title screening       | 744                               |
| After abstract screening    | 386                               |
| Full-text assessed          | 250                               |
| After qualitative screening | 182                               |
| Final included              | 182 (102 main + 85 supplementary) |

Each numerical transition is backed by explicit CSV files under `prisma/`.

---

## 5. Repository Structure (PRISMA Hierarchy)

    review-paper tree
    ├── README.md
    ├── figs
    │   ├── co-occurance_graph.png
    │   ├── distribution_per_category.png
    │   ├── distribution_per_source.png
    │   ├── trend_by_year.png
    │   └── word_cloud.png
    └── prisma
        ├── 01_articles_per_source
        ├── 02_duplicate_removal
        ├── 03_title_screening
        ├── 04_abstract_screening
        ├── 05_fulltext_screening
        ├── 06_qualitive_fulltext_qualitive
        ├── 07_candidate_papers
        └── 08_summarized_texts

---

## 6. PRISMA Screening Stages and Statistical Insights

### 6.1 Identification — `01_articles_per_source`

Raw records retrieved from all databases are stored in `articles.csv`.

To contextualize the scope and temporal evolution of the retrieved literature, the following figure shows the **publication trend over time**.

![Trend by year](figs/trend_by_year.png)

This trend highlights the increasing research interest in recent years, particularly for prediction-based methods.

---

### 6.2 Duplicate Removal — `02_duplicate_removal`

Duplicates were detected using DOI matching and normalized title similarity.

The contribution of each data source before and after duplicate removal is visualized below.

![Distribution per source](figs/distribution_per_source.png)

This confirms that Scopus and IEEE Xplore contribute the majority of unique records.

---

### 6.3 Title Screening — `03_title_screening`

Title screening removes out-of-scope studies that do not address:

- Surgical procedures
- Aesthetic outcomes
- Technical or computational methods

The thematic distribution of retained studies begins to emerge at this stage.

---

### 6.4 Abstract Screening — `04_abstract_screening`

Abstract screening enforces methodological relevance:

- Prediction or evaluation of aesthetics
- Imaging-based approaches (2D or 3D)
- Exclusion of purely clinical, psychological, or non-technical studies

The distribution of retained studies across task categories is shown below.

![Distribution per category](figs/distribution_per_category.png)

This illustrates the dominance of evaluation-related studies and the comparatively recent growth of prediction-focused research.

---

### 6.5 Full-Text Screening — `05_fulltext_screening`

Full-text screening evaluates:

- Technical novelty
- Adequate experimental validation
- Reproducibility of methods

Keyword-level relationships among the retained studies are visualized using co-occurrence analysis.

![Co-occurrence graph](figs/co-occurance_graph.png)

This highlights recurring concepts such as shape analysis, learning-based models, and aesthetic scoring.

---

### 6.6 Qualitative / Quality Screening — `06_qualitive_fulltext_qualitive`

A structured qualitative assessment was applied using domain-specific criteria:

- Novelty
- Technical rigor
- Dataset adequacy
- Evaluation validity
- Contribution beyond medical reporting

The dominant terminology after quality screening is illustrated below.

![Word cloud](figs/word_cloud.png)

This confirms alignment with the core themes discussed in the manuscript.

---

### 6.7 Final Included Studies — `07_candidate_papers`

`candidate_papers.csv` contains the final set of studies used in:

- Comparative tables
- Methodological taxonomy
- Critical discussion

---

### 6.8 Evidence Synthesis — `08_summarized_texts`

Structured summaries are provided:

- `combined_summs.xlsx`: unified synthesis
- Task-specific CSV files (prediction, evaluation, datasets, reviews, subjective evaluation, support tasks)

---

## 7. Reviewer Roles and Conflict Resolution

- Deterministic inclusion/exclusion rules were applied
- Decisions are logged as explicit binary flags
- Ambiguous cases were conservatively retained until later stages
- Final inclusion required satisfying **all eligibility and quality criteria**

---

## 8. Protocol Registration Statement

This review was **not registered in PROSPERO** due to its strong focus on **computer science, engineering, and imaging-based methodologies**, which extend beyond PROSPERO’s primary biomedical scope.

Full transparency is achieved through:

- Public repository access
- Immutable CSV screening logs
- Explicit exclusion rationales

---

## 9. Reproducibility Statement

Any researcher can:

1. Start from `prisma/01_articles_per_source/articles.csv`
2. Reapply each screening step
3. Recover identical PRISMA counts
4. Trace every excluded study to a documented reason

This repository fully satisfies PRISMA requirements for **transparency, auditability, and reproducibility**.
