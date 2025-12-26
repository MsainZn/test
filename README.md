# PRISMA-Based Systematic Review Repository  
**Transparent, Reproducible, and Auditable Literature Screening Pipeline**

---

## 1. Purpose of This Repository

This repository documents the complete **PRISMA 2020–compliant workflow** used in the associated systematic review on **prediction and evaluation of aesthetic surgical outcomes**.

The repository is designed to:

- Ensure **methodological transparency**
- Explicitly address **reviewer concerns regarding PRISMA reporting**
- Enable **file-level reproducibility** of all screening decisions
- Connect **all figures** directly to the screened and curated datasets

Every inclusion and exclusion decision is explicitly logged and traceable through CSV files.

---

## 2. PRISMA Overview and Study Identification

The review strictly follows the PRISMA 2020 framework:

- Identification  
- Screening  
- Eligibility  
- Inclusion  

The complete PRISMA flow diagram below illustrates how records progress through each stage, including explicit exclusion counts and reasons.

![PRISMA workflow](figs/prisma.jpg)

This diagram corresponds exactly to the CSV files stored under the `prisma/` directory and provides a verifiable numerical audit trail.

---

## 3. Search Strategy

### Databases Searched
- Scopus  
- PubMed  
- IEEE Xplore  
- Semantic Scholar  
- Manual backward reference search  

Two independent searches were conducted:
1. **Prediction of aesthetic outcomes**
2. **Evaluation / assessment of aesthetic outcomes**

Exact search strings, filters, and constraints are reported verbatim in the manuscript to ensure full reproducibility.

---

## 4. Temporal Characteristics of the Retrieved Literature

Following identification, a statistical overview was conducted to understand the **evolution of the field over time**.

![Trend by year](figs/trend_by_year.png)

This figure shows that:
- Aesthetic **evaluation** studies dominate earlier years
- Aesthetic **prediction** studies increase significantly after ~2020
- Growth aligns with advances in deep learning, data availability, and computational resources

This temporal trend motivated the dual focus of the review.

---

## 5. Source Distribution and Database Contribution

After duplicate removal, the relative contribution of each database was analyzed.

![Distribution per source](figs/distribution_per_source.png)

Key observations:
- **Scopus** provides the largest share of unique records
- **Semantic Scholar** contributes substantial complementary coverage
- Manual search ensures inclusion of highly relevant but non-indexed studies

This supports the breadth and completeness of the identification stage.

---

## 6. PRISMA Screening Stages with Analytical Insights

### 6.1 Identification — `01_articles_per_source`

All raw records retrieved from databases are stored in:
- `articles.csv`

This file represents the **unfiltered corpus** and includes title, abstract, DOI, year, venue, and source.

---

### 6.2 Duplicate Removal — `02_duplicate_removal`

Duplicates were identified using:
- DOI matching
- Normalized title similarity

Outputs include:
- Explicitly flagged duplicates
- Retained unique records
- Rejected duplicate entries

This ensures objective and reproducible duplicate handling.

---

### 6.3 Title Screening — `03_title_screening`

Title screening removes out-of-scope studies that do not address:
- Surgical procedures
- Aesthetic outcomes
- Computational or technical methodologies

This stage enforces **scope alignment** while remaining conservative to avoid premature exclusion.

---

### 6.4 Abstract Screening — `04_abstract_screening`

Abstract screening enforces methodological relevance:
- Prediction or evaluation of aesthetics
- Imaging-based methods (2D or 3D)
- Exclusion of purely clinical, psychological, or non-technical studies

The retained studies were categorized by task type.

![Distribution per category](figs/distribution_per_category.png)

This figure highlights:
- Strong dominance of evaluation-related works
- Rapid recent growth in prediction-based approaches
- Interdisciplinary nature across engineering, computer science, and medicine

---

### 6.5 Full-Text Screening — `05_fulltext_screening`

Full-text screening evaluates:
- Technical novelty
- Adequacy of experimental validation
- Reproducibility of methods
- Relevance to surgical planning or outcome assessment

Keyword relationships among retained studies were analyzed.

![Co-occurrence graph](figs/co-occurance_graph.png)

This network reveals:
- Central role of machine learning and deep learning
- Strong linkage between aesthetic evaluation and clinical practice
- Emerging use of generative and simulation-based methods

---

### 6.6 Qualitative / Quality Screening — `06_qualitive_fulltext_qualitive`

A structured qualitative assessment was applied using domain-specific criteria:
- Novelty
- Technical rigor
- Dataset adequacy
- Evaluation validity
- Contribution beyond descriptive medical reporting

Dominant terminology after quality filtering is visualized below.

![Word cloud](figs/word_cloud.png)

This confirms strong alignment with:
- Imaging
- Learning-based models
- Surgical outcome analysis
- Prediction and evaluation tasks

---

### 6.7 Final Included Studies — `07_candidate_papers`

- `candidate_papers.csv` contains the final corpus used for:
  - Comparative tables
  - Methodological taxonomy
  - Critical synthesis and discussion

---

### 6.8 Evidence Synthesis — `08_summarized_texts`

Structured summaries are provided in:
- `combined_summs.xlsx` (global synthesis)
- Task-specific CSV files:
  - Prediction
  - Evaluation
  - Datasets
  - Reviews
  - Subjective Evaluation
  - Support Tasks

These files support transparent qualitative and comparative analysis.

---

## 7. Reviewer Roles and Conflict Resolution

- Deterministic inclusion/exclusion rules were applied
- Decisions are logged as explicit binary flags
- Ambiguous cases were conservatively retained until full-text review
- Final inclusion required satisfying **all eligibility and quality criteria**

---

## 8. Protocol Registration Statement

This review was **not registered in PROSPERO** due to its strong focus on **computer science, engineering, and imaging-based methodologies**, which extend beyond PROSPERO’s primary biomedical scope.

Full transparency is instead achieved through:
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

---

## 10. Repository Structure (PRISMA Hierarchy)

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
