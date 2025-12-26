# Automatic Prediction and Evaluation of Aesthetic Outcomes in Plastic and Oncological Surgery: A Systematic Review

Authors: Helena Montenegro*†, Mohammad Hossein Zolfagharnasab†, Fábio Teixeira‡, Gonçalo da Costa Sequeira Pinto‡, Joana Santos‡, Pedro Ferreira‡, Eduard-Alexandru Bonci, Carlos Mavioso, Maria J. Cardoso, Jaime S. Cardoso  
Corresponding author: maria.h.sampaio@inesctec.pt  
†‡ Equal contribution

---

## 1) Search strategy and literature retrieval

This section explains **where** the literature was retrieved from, **why** those repositories were selected, and **how** the search queries were constructed to target the intended research space.

### 1.1 Selected repositories (and why they matter)

To avoid repository bias and to cover both **clinical** and **computational** perspectives, we deliberately combined repositories with complementary strengths:

- Scopus  
  Chosen as the reference platform for query design due to its broad interdisciplinary indexing and fine-grained filters (subject area, document type, language). It reliably captures work at the interface of engineering and medicine.

- PubMed  
  Ensures coverage of oncological and reconstructive surgery literature, particularly studies grounded in clinical workflows and medical validation.

- IEEE Xplore  
  Essential for capturing algorithmic, machine learning, computer vision, simulation, and 3D modeling approaches that may not appear in medically focused databases.

- Semantic Scholar  
  Acts as a complementary discovery layer, often surfacing cross-disciplinary and recently published works not yet consistently indexed elsewhere.

- Manual backward reference search  
  Used to identify highly relevant or seminal studies cited by included works but missed by automated queries.

Although each repository uses a different query syntax, the **same conceptual keyword logic and constraints** were applied across all platforms. Only syntax-level adaptations were made.

All retrieved records from all repositories were merged into a single dataset representing the **Identification** stage of PRISMA.

Merged raw retrieval (all sources combined):  
prisma/01_articles_per_source/articles.csv

This file contains titles, abstracts, DOIs (when available), publication years, venues, and source identifiers.

---

### 1.2 Keyword design and search intent

The search strategy was explicitly designed to capture the **intersection of three orthogonal dimensions**, ensuring both relevance and specificity:

1) Aesthetic context  
   aesthetic, esthetic, cosmetic, plastic, reconstructive, oncological

2) Surgical domain  
   surgery

3) Computational task  
   - Prediction-oriented terms: outcome prediction, simulation, pre-operative prediction, post-operative prediction  
   - Evaluation-oriented terms: evaluation, assessment, scoring

This structure prevents:
- retrieval of purely clinical or psychological studies without computational contribution,
- inclusion of non-surgical aesthetic interventions,
- dilution of the corpus with non-imaging or non-technical works.

Additional constraints were imposed to improve comparability and rigor:
- English language  
- Journal articles  
- Subject areas restricted to Computer Science and Engineering  

---

### 1.3 Example search strings (Scopus – SQL-like format)

The following blocks show the **exact logical structure** of the Scopus queries used in the study.  
Equivalent queries were executed on PubMed, IEEE Xplore, and Semantic Scholar with syntax adaptations only.

Prediction of aesthetic outcomes (SQL-like representation):

    TITLE-ABS-KEY (
        ("aesthetic" OR "esthetic" OR "cosmetic"
         OR "plastic" OR "reconstructive" OR "oncological")
        AND "surgery"
        AND (
            "outcome prediction"
            OR "simulation"
            OR "post-operative prediction"
            OR "pre-operative prediction"
        )
    )
    AND DOCTYPE = "re"
    AND (SUBJAREA = "COMP" OR SUBJAREA = "ENGI")
    AND LANGUAGE = "English"
    AND SRCTYPE = "j"

Evaluation of aesthetic outcomes (SQL-like representation):

    TITLE-ABS-KEY (
        ("aesthetic" OR "esthetic" OR "cosmetic"
         OR "plastic" OR "reconstructive" OR "oncological")
        AND "surgery"
        AND (
            "evaluation"
            OR "assessment"
        )
    )
    AND DOCTYPE = "re"
    AND (SUBJAREA = "COMP" OR SUBJAREA = "ENGI")
    AND LANGUAGE = "English"
    AND SRCTYPE = "j"

The separation between prediction and evaluation queries directly supports the dual taxonomy adopted in the review.

---

## 2) Analyzing the Retrieved Articles:

### 2.1) Distribution of retrieved literature across repositories

After merging all retrieved records, we analysed **repository-level contributions** to understand coverage, redundancy, and balance.

![Distribution per source](figs/distribution_per_source.png)

### Detailed interpretation

- Scopus contributes the largest fraction of records, reflecting its broad interdisciplinary scope and justifying its role as the reference platform.
- IEEE Xplore contributes a substantial share of technically oriented studies, confirming that algorithmic and ML-based approaches are well represented.
- PubMed contributes fewer records overall but with high clinical density, often focused on validation and medical interpretation of aesthetic outcomes.
- Semantic Scholar adds complementary coverage, particularly for cross-domain or recently published works.
- Manual backward search, while smaller in volume, is critical for recovering influential or domain-specific papers missed by automated querying.

This distribution confirms that the retrieval process is **not dominated by a single database** and that multi-source querying is necessary for this research topic.

### 2.2) Vocabulary analysis: validating the search strategy

To assess whether the keyword design and filters successfully captured the intended research space, we analysed the dominant terminology present in the retrieved corpus.

![Word cloud](figs/word_cloud.png)

### Detailed interpretation

- Prominent terms such as image, assessment, prediction, deep, model, surgery, aesthetic, and outcome directly align with the review’s focus on imaging-based computational analysis of aesthetic surgical results.
- The simultaneous presence of technical terms (deep, network, model) and clinical terms (patient, surgery, outcome) indicates that the retrieved literature lies at the intended intersection of artificial intelligence and surgical practice.
- The absence of dominant off-topic terminology (e.g., unrelated cosmetic procedures or purely psychological studies) suggests that the keyword design and imposed constraints were effective.


### 2.3) Disciplinary composition of prediction and evaluation studies

To further characterize the retrieved corpus, we analysed the **disciplinary distribution** of studies, distinguishing between **aesthetic prediction** and **aesthetic evaluation** tasks.

![Distribution per category](figs/distribution_per_category.png)

**Aesthetic prediction**
- Dominated by **Engineering (33.7%)** and **Computer Science (16.3%)**
- Strong focus on:
  - algorithm design
  - machine learning and simulation
  - modeling and optimization
- **Medicine (15.2%)** and **Biochemistry (10.5%)** mainly provide:
  - clinical grounding
  - data acquisition and validation context
- Minor contributions from:
  - Materials Science, Chemistry, Physics, Mathematics  
- Very limited involvement of **Health Professions**, indicating low practitioner-driven method development

**Aesthetic evaluation**
- More **balanced interdisciplinary profile**
- Major contributors:
  - Engineering (28.7%)
  - Medicine (17.8%)
  - Biochemistry (13.5%)
  - Computer Science (13.4%)
- Reflects emphasis on:
  - clinical interpretation
  - outcome scoring
  - perceptual and validation frameworks
- Higher presence of **Materials Science** and **Chemistry**, often linked to:
  - imaging modalities
  - tissue and reconstruction analysis
- Minimal role of Physics and Mathematics, suggesting reduced reliance on first-principles modeling

**Overall takeaway**
- Prediction → method-driven, engineering-centric  
- Evaluation → clinically integrated, validation-oriented  
- This asymmetry explains later differences in datasets, evaluation protocols, and reported metrics.

---

### 2.4) Temporal evolution of the literature (2000–2025)

We analysed the **yearly publication trends** to assess the maturity and growth dynamics of the field.

![Yearly publication trend](figs/trend_by_year.png)

#### Key observations

**2000–2005: Early exploratory phase**
- Very low publication counts
- No clear separation between prediction and evaluation
- Limited computational support in surgical aesthetics

**2006–2012: Gradual growth**
- Steady increase in both streams
- Driven by:
  - digital imaging adoption
  - early machine learning methods
  - standardized photographic documentation

**2013–2019: Divergence phase**
- **Evaluation studies grow faster than prediction**
- Reflects:
  - increasing demand for objective outcome assessment
  - easier validation compared to prediction tasks

**2020–2025: Consolidation and expansion**
- High activity in both streams
- Evaluation peaks around 2021–2022
- Prediction shows steady but more variable growth
- Indicates transition from niche research to a consolidated field

**Overall takeaway**
- Outcome **evaluation currently outpaces prediction**
- Predictive modeling remains more constrained by:
  - data availability
  - validation complexity
- This imbalance motivates the future research directions discussed later.

Together, these analyses confirm that the retrieved corpus is coherent, interdisciplinary, and temporally aligned with the stated scope of the review, supporting its progression into the PRISMA screening pipeline.

---

## 3) PRISMA workflow and screening pipeline

All retrieved records entered a PRISMA-compliant screening pipeline:

Identification → Duplicate Removal → Title Screening → Abstract Screening → Full-Text Screening → Qualitative Screening → Inclusion

![PRISMA workflow](figs/prisma.jpg)

### PRISMA flow numbers (fully backed by CSV files)

Identified: 1,027  
After duplicate removal: 939  
After title screening: 744  
After abstract screening: 386  
Full-text assessed: 250  
After qualitative screening: 182  
Final included: 182 (102 main + 85 supplementary)

Each transition is traceable to a dedicated folder under prisma/, with explicit retained and rejected records.

---

## 4) Duplicate removal — prisma/02_duplicate_removal

Goal: remove duplicate studies indexed across multiple repositories.

Detection strategy:
- DOI matching (primary)
- Normalized title similarity (fallback when DOI is missing or inconsistent)

Files:
- articles_duplicate_marked.csv – all detected duplicates
- articles_rejected_by_duplicacy.csv – removed records
- articles_after_duplicates.csv – retained unique corpus
- articles_categorized.csv – intermediate organization artifact (if used)

This step ensures that subsequent statistics, trends, and screening decisions are not biased by indexing redundancy.

---

## 5) Title screening — prisma/03_title_screening

Goal: remove clearly out-of-scope records conservatively.

Typical exclusion reasons:
- Not related to surgery or not within PR/oncological context
- No aesthetic outcome focus
- No computational or technical contribution

Files:
- articles_titles_screened_marked.csv
- articles_rejected_by_titles.csv
- articles_after_title_screening.csv

---

## 6) Abstract screening — prisma/04_abstract_screening

Goal: enforce methodological relevance and lock the review taxonomy.

Inclusion requirements:
- Addresses aesthetic outcome prediction or evaluation
- Uses imaging data (2D or 3D)
- Presents a computational method (not purely narrative)

Files:
- articles_abstract_screened_marked.csv
- articles_rejected_by_abstract.csv
- articles_after_abstract_screening.csv

---

## 7) Full-text screening — prisma/05_fulltext_screening

Goal: confirm eligibility using full-text evidence.

Common exclusion reasons:
- Insufficient methodological detail
- Weak or unclear evaluation protocol
- Misalignment with aesthetic prediction/evaluation despite abstract wording

Files:
- articles_full-text_screened_marked.csv
- articles_rejected_by_full-text.csv
- articles_after_full-text_screening.csv

Conceptual structure of the retained literature:

![Co-occurrence graph](figs/co-occurance_graph.png)

This network highlights dominant methodological themes, subdomains (e.g., facial vs. breast aesthetics), and cross-domain overlaps that support transferability arguments in the review.

---

## 8) Qualitative / quality screening — prisma/06_qualitive_fulltext_qualitive

Goal: ensure that the final corpus supports robust comparative synthesis.

Quality dimensions:
- Novelty beyond incremental reporting
- Technical rigor and clarity
- Dataset adequacy and transparency
- Evaluation validity and (when applicable) clinical relevance
- Practical value for prediction/evaluation workflows

Files:
- articles_qualitive_screened_marked.csv
- articles_rejected_by_quality.csv
- articles_after_qualitive_screening.csv

---

## 9) Final included studies and synthesis artifacts

Final included studies:
- prisma/07_candidate_papers/candidate_papers.csv

Evidence synthesis:
- prisma/08_summarized_texts/combined_summs.xlsx
- prisma/08_summarized_texts/summerized_per_tasks/

These files directly support the paper’s taxonomy, comparative tables, limitations analysis, and future research directions.

---

## 10) Reproducibility and protocol statement

This review was not registered in PROSPERO due to its primary emphasis on computer science, engineering, and imaging-based computational methodologies, which extend beyond PROSPERO’s core biomedical scope.

Transparency and reproducibility are ensured through:

- A full, publicly accessible PRISMA audit trail  
- Immutable CSV-based decision logs for every screening stage  
- Explicit, stage-level rejection files documenting exclusion rationale  

All screening transitions, inclusion decisions, and exclusions are traceable through version-controlled artifacts in the repository, enabling complete methodological inspection and independent reproducibility.

---

## 11) Repository hierarchy

review-paper tree  
├── README.md  
├── figs  
│   ├── prisma.jpg  
│   ├── distribution_per_source.png  
│   ├── word_cloud.png  
│   ├── trend_by_year.png  
│   ├── distribution_per_category.png  
│   └── co-occurance_graph.png  
└── prisma  
    ├── 01_articles_per_source  
    ├── 02_duplicate_removal  
    ├── 03_title_screening  
    ├── 04_abstract_screening  
    ├── 05_fulltext_screening  
    ├── 06_qualitive_fulltext_qualitive  
    ├── 07_candidate_papers  
    └── 08_summarized_texts
