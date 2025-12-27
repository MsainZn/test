 # Automatic Prediction and Evaluation of Aesthetic Outcomes in Plastic and Oncological Surgery: A Systematic Review

Authors: Helena Montenegro*†, Mohammad Hossein Zolfagharnasab†, Fábio Teixeira‡, Gonçalo da Costa Sequeira Pinto‡, Joana Santos‡, Pedro Ferreira‡, Eduard-Alexandru Bonci, Carlos Mavioso, Maria J. Cardoso, Jaime S. Cardoso  
Corresponding author: maria.h.sampaio@inesctec.pt  
†‡ Equal contribution

---

## 1) Search strategy and literature retrieval

This section explains **where** the literature was retrieved from, **why** those repositories were selected, and **how** the search queries were constructed to target the intended research space.

### 1.1) Selected Repositories and Rationale

To reduce repository bias and capture both **clinical** and **computational** literature, multiple complementary databases were searched:

- **Scopus** (primary platform for query design; broad interdisciplinary coverage)
- **PubMed** (clinical and surgical literature)
- **IEEE Xplore** (machine learning, computer vision, and technical methods)
- **Semantic Scholar** (cross-disciplinary and recent publications; easier to find more semantically aligned studies to our objective)
- **Manual backward reference screening** (missed or seminal studies)

Equivalent **conceptual search logic** was applied across all repositories, with only syntax-level adaptations.

All retrieved records were merged into a single dataset representing the **PRISMA Identification** stage:

`prisma/01_articles_per_source/articles.csv`

The dataset contains titles, abstracts, DOIs (when available), publication years, venues, and source identifiers.

---

### 1.2) Keyword design and search intent

The search strategy was constructed to deliberately target studies at the **intersection of aesthetic surgery and computational methodology**, ensuring both relevance and specificity.

Search terms were organized along three complementary dimensions:

1. **Aesthetic and reconstructive context**  
   *aesthetic/esthetic, cosmetic, plastic, reconstructive, oncological*

2. **Surgical domain**  
   *surgery*

3. **Computational objective**  
   - **Prediction-oriented**: outcome prediction, simulation, pre-operative prediction, post-operative prediction  
   - **Evaluation-oriented**: evaluation, assessment, scoring  

Only studies simultaneously addressing all three dimensions were eligible.

### 1.3) Rationale and constraints

This structured design minimized the inclusion of:
- purely clinical or psychological studies lacking a computational component,
- non-surgical aesthetic interventions,
- technically unrelated or non-imaging-based work.

To further improve methodological consistency and cross-study comparability, the following constraints were applied:
- English-language publications,
- journal and conferences only,
- subject areas mostly aligned with **Computer Science** and **Engineering**.

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

All retrieved records entered a **PRISMA-compliant, fully auditable screening pipeline** specifically designed for a **cross-disciplinary systematic review** spanning computer science, engineering, and surgical sciences.  
The pipeline emphasizes **traceability, conservative exclusion, and reproducibility**, ensuring that every decision can be independently inspected and replicated.

Identification → Duplicate Removal → Title Screening → Abstract Screening → Full-Text Screening → Qualitative Screening → Inclusion

![PRISMA workflow](figs/prisma.jpg)

---

### 3) Review Rules and Guidlines

The table below summarizes the **quantitative evolution of the corpus** across PRISMA stages.  
Importantly, reductions at each stage are **intentional and methodologically motivated**, not arbitrary filtering.

| PRISMA stage | Records | Description |
|-------------|---------|-------------|
| Identified | 1,027 | Raw corpus aggregated from all repositories and manual backward searches |
| After duplicate removal | 939 | Redundant indexing across databases removed |
| After title screening | 744 | Clearly irrelevant or out-of-scope studies excluded |
| After abstract screening | 386 | Studies failing methodological relevance criteria excluded |
| Full-text assessed | 250 | Subset eligible for detailed methodological inspection |
| After qualitative screening | 182 | Studies meeting rigor, transparency, and comparability requirements |
| Final included | 182 | 102 primary (core analysis) + 85 supplementary (contextual support) |

Each numerical transition is supported by **explicit CSV decision logs**, ensuring full transparency.

### 3.1) Eligibility criteria (explicit and prespecified)

To minimize subjectivity and ensure consistency across reviewers, explicit eligibility criteria were defined a priori.

#### 3.1.1) Inclusion criteria

Studies were included if they satisfied all of the following:

- Focused on aesthetic outcomes in plastic, reconstructive, or oncological surgery

- Addressed outcome prediction or outcome evaluation/assessment

- Employed a computational, algorithmic, or imaging-based methodology

- Used medical images (e.g., photographs, 2D/3D imaging) as a primary data source

- Were peer-reviewed journal articles

- Published in English

#### 3.1.2) Exclusion criteria

Studies were excluded if they met any of the following:

- Purely clinical, psychological, or survey-based studies without computational methods

- Non-surgical aesthetic procedures (e.g., dermatology, makeup, non-invasive cosmetics)

- Editorials, commentaries, conference abstracts, theses, or non-peer-reviewed material

- Studies lacking sufficient methodological detail to allow comparative analysis

- Duplicate publications of the same study (only one canonical version retained)

### 3.2) Disagreement Resolution and Reviewing Roles

Two independent reviewers (Helena & Moe) conducted all screening stages (Title, Abstract, Full-text, and Qualitive) following below rules:

- Screening decisions were initially made independently

- Disagreements were resolved through consensus discussion. To do so, the rejection reasons for each study is written im short details as justification. These notes can be found in csv files `rejection_by_stage.csv` at each stage directory. 

- If consensus could not be reached, the manuscript is passed down the next screening stage in order to assess more thoroughly.

This process was applied consistently across all screening stages to minimize selection bias and subjective inclusion.


### 3.3) Protocol registration and reporting standards

This review was not registered in PROSPERO due to its primary emphasis on computer science, engineering, and imaging-based computational methodologies, which extend beyond PROSPERO’s core biomedical scope.

- PROSPERO is primarily designed for biomedical intervention reviews (e.g., clinical trials, therapeutic effectiveness). 
- The present review focuses on computational, imaging-based, and algorithmic methods for aesthetic outcome prediction and evaluation, spanning computer science, engineering, and surgical domains. 
- As such, it falls partially outside PROSPERO’s intended scope.

However, transparency and reproducibility are ensured through:

- A full, publicly accessible PRISMA audit trail  
- Immutable CSV-based decision logs for every screening stage  
- Explicit, stage-level rejection files documenting exclusion rationale  

All screening transitions, inclusion decisions, and exclusions are traceable through version-controlled artifacts in the repository, enabling complete methodological inspection and independent reproducibility.

### 3.4) Risk of bias and quality assessment

To ensure a structured and reproducible evaluation of study quality, a custom quality assessment framework was applied. This framework was adapted from the conceptual principles of QUADAS-2 and PROBAST, but specifically tailored to machine learning–based, imaging-driven, and methodological studies.

Each included full-text article was assessed across five predefined quality domains, as summarized in Table X.

| Domain               | Assessment Criteria |
|---------------------|---------------------|
| Methodological rigor | Clear problem formulation; appropriate model selection; transparent training and inference procedures |
| Data transparency    | Adequate dataset description; sample size reporting; clear image acquisition protocols |
| Evaluation validity  | Use of appropriate evaluation metrics; inclusion of validation and/or test splits; comparison against baselines or gold standards |
| Reproducibility      | Sufficient implementation details; availability of code or pseudocode; clearly described experimental setup |
| Clinical relevance   | Alignment with real-world surgical workflows; interpretability of model outputs; practical applicability |

Each domain was independently rated using a three-level scale:

- **Adequate**: All criteria within the domain were fully addressed and clearly reported.  
- **Partially adequate**: Some criteria were addressed, but reporting was incomplete or lacked sufficient detail.  
- **Inadequate**: Criteria were largely unmet or insufficiently described.

Only studies rated as **adequate** or **partially adequate** across all domains were retained for qualitative synthesis. Studies excluded at this stage were not considered scientifically invalid; rather, exclusion reflected limited interpretability, transparency, or comparability for cross-study synthesis.

All quality assessment decisions and justifications are documented in  `prisma/06_qualitive_fulltext_qualitive/` 

---

### 4) Stage-wise PRISMA screening details and artifacts

This subsection explains **why each stage exists**, **how decisions were made**, **which studies were excluded**, and **where the evidence for those decisions resides**.

---

#### 4.1) Identification — `prisma/01_articles_per_source`

**Rationale**  
Given the interdisciplinary nature of aesthetic outcome prediction and evaluation, the identification stage was intentionally **recall-oriented**. Missing relevant computational studies would be more harmful than temporarily including marginal ones.

**What happens here**
- Aggregation of all automated query outputs
- Inclusion of manually identified references
- No quality or relevance judgment at this stage

**Why this matters**
- Prevents early bias toward a single discipline or publication venue
- Ensures visibility of emerging or hybrid research not consistently indexed

**Artifact**

| File | Description |
|-----|-------------|
| `articles.csv` | Complete raw retrieval with metadata (titles, abstracts, DOIs, years, venues, sources) |

---

#### 4.2) Duplicate removal — `prisma/02_duplicate_removal`

**Rationale**  
The same study frequently appears across multiple repositories with slight metadata variations. Without explicit duplicate handling, downstream analyses (e.g., trends, distributions) would be distorted.

**How duplicates are detected**
- DOI matching ensures high-confidence identification
- Title similarity acts as a robust fallback for missing or inconsistent DOIs

**Decision principle**
- Only **one canonical record** is retained
- No study is excluded for scientific reasons at this stage

**Artifacts**

| File | Description |
|-----|-------------|
| `articles_duplicate_marked.csv` | All detected duplicate groupings |
| `articles_rejected_by_duplicacy.csv` | Records removed due to redundancy |
| `articles_after_duplicates.csv` | Clean, de-duplicated corpus |
| `articles_categorized.csv` | Optional organization layer for inspection |

---

#### 4.3) Title screening — `prisma/03_title_screening`

**Rationale**  
Title screening acts as a **first relevance filter**, removing studies that are unmistakably outside the review’s scope while preserving ambiguous cases.

**Why conservative exclusion is used**
- Titles often underspecify methods
- Overly aggressive filtering risks false negatives

**Typical exclusion logic**
- No surgical context
- No aesthetic outcome dimension
- No computational or technical contribution

**Artifacts**

| File | Description |
|-----|-------------|
| `articles_titles_screened_marked.csv` | Title-level inclusion flags |
| `articles_rejected_by_titles.csv` | Excluded records with reason labels |
| `articles_after_title_screening.csv` | Retained set for abstract review |

---

#### 4.4) Abstract screening — `prisma/04_abstract_screening`

**Rationale**  
Abstract screening enforces **methodological relevance** and formalizes the **prediction vs. evaluation taxonomy** used throughout the review.

**Key evaluation questions**
- Is the task clearly prediction or evaluation?
- Is imaging data central to the methodology?
- Is a computational method actually proposed or used?

**Why this stage is critical**
- Prevents inclusion of studies that only mention computation superficially
- Aligns the corpus with the analytical structure of the review

**Artifacts**

| File | Description |
|-----|-------------|
| `articles_abstract_screened_marked.csv` | Abstract-level decisions |
| `articles_rejected_by_abstract.csv` | Excluded studies with rationale |
| `articles_after_abstract_screening.csv` | Corpus entering full-text review |

---

#### 4.5) Full-text screening — `prisma/05_fulltext_screening`

**Rationale**  
At this stage, claims made in abstracts are verified against **actual methodological content**.

**Assessment focus**
- Are methods reproducible in principle?
- Are datasets sufficiently described?
- Is the evaluation protocol meaningful and aligned with the task?

**Why exclusions occur here**
- Abstracts may overstate contributions
- Full text may lack sufficient detail for comparison or synthesis

**Artifacts**

| File | Description |
|-----|-------------|
| `articles_full-text_screened_marked.csv` | Full-text eligibility decisions |
| `articles_rejected_by_full-text.csv` | Excluded studies with explicit reasons |
| `articles_after_full-text_screening.csv` | Studies retained for quality assessment |

---

#### 4.6) Qualitative / quality screening — `prisma/06_qualitive_fulltext_qualitive`

**Rationale**  
Not all technically valid studies are equally useful for comparative synthesis.  
This stage prioritizes **substantive, interpretable, and transferable contributions**.

**Quality is assessed along multiple axes**
- Methodological rigor
- Dataset transparency
- Evaluation validity
- Practical relevance to real workflows

**Exclusions at this stage**
- Do not indicate poor science
- Reflect limited comparative or analytical value

**Artifacts**

| File | Description |
|-----|-------------|
| `articles_qualitive_screened_marked.csv` | Quality decisions |
| `articles_rejected_by_quality.csv` | Excluded studies with rationale |
| `articles_after_qualitive_screening.csv` | Final high-quality corpus |

---

### 4.7) Final inclusion and synthesis artifacts

The final corpus is structured to **directly support analysis, comparison, and discussion**.

**Included studies**

| File | Description |
|-----|-------------|
| `prisma/07_candidate_papers/candidate_papers.csv` | Definitive list of included studies |

**Synthesis artifacts**

| Path | Description |
|-----|-------------|
| `prisma/08_summarized_texts/combined_summs.xlsx` | Unified summaries for cross-study comparison |
| `prisma/08_summarized_texts/summerized_per_tasks/` | Task-specific structured summaries |

---

**Overall methodological takeaway**

- Screening decisions are **progressive, conservative, and justified**
- Every exclusion is **documented and reversible**
- All artifacts are **machine-readable, immutable, and version-controlled**
- The pipeline supports **independent audit, replication, and extension**

This PRISMA implementation is therefore not only compliant, but **operationally transparent and computationally reproducible**.

**Conceptual structure of retained literature**

![Co-occurrence graph](figs/co-occurance_graph.png)

### Interpretation of the keyword co-occurrence network

The co-occurrence network provides a compact view of the **conceptual organization** of the retained literature, showing how methodological, clinical, and evaluation concepts are connected.

- **Modular but connected structure**
  - Distinct thematic clusters with strong inter-cluster links
  - Indicates an integrative, non-fragmented research field

- **Central bridging concepts**
  - artificial intelligence, machine learning, plastic surgery
  - Link computational methods with clinical application

- **Main clusters**
  - **Prediction / methodology**: CNNs, networks, training, representation, GANs, simulation  
  - **Evaluation / validation**: aesthetic evaluation, objective assessment, gold standard  
  - **Clinical domains**: facial aesthetics and breast surgery (reconstruction, cancer, cosmetic outcome)  
  - **Imaging modality**: photograph and digital photography as dominant data sources

- **Key implication**
  - Prediction and evaluation are distinct but tightly coupled
  - Computational methods are reused across clinical contexts
  - The structure validates the review taxonomy and supports cross-study comparison

This visualization validates thematic coherence and reveals methodological clusters.

---

## 5) Final included studies and synthesis artifacts

Final included studies:
- prisma/07_candidate_papers/candidate_papers.csv

Evidence synthesis:
- prisma/08_summarized_texts/combined_summs.xlsx
- prisma/08_summarized_texts/summerized_per_tasks/

These files directly support the paper’s taxonomy, comparative tables, limitations analysis, and future research directions.

---

## 7) Repository hierarchy

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
