# Automatic Prediction and Evaluation of Aesthetic Outcomes in Plastic and Oncological Surgery: A Systematic Review

**Authors:** Helena Montenegro*†, Mohammad Hossein Zolfagharnasab†, Fábio Teixeira‡, Gonçalo da Costa Sequeira Pinto‡, Joana Santos‡, Pedro Ferreira‡, Eduard-Alexandru Bonci, Carlos Mavioso, Maria J. Cardoso, Jaime S. Cardoso  
**Corresponding author:** maria.h.sampaio@inesctec.pt  
†‡ Equal contribution

---

## 1) Search strategy and literature retrieval

### 1.1 Selected repositories

To ensure **exhaustive, interdisciplinary coverage** spanning clinical, biomedical, and engineering perspectives, we queried the following repositories:

- **Scopus** – broad interdisciplinary indexing with advanced filtering options, used as the reference platform for query design  
- **PubMed** – primary source for biomedical and clinically oriented research  
- **IEEE Xplore** – core repository for engineering- and algorithm-driven methodologies  
- **Semantic Scholar** – complementary discovery layer capturing cross-indexed records and preprint-linked works  
- **Manual backward reference search** – identification of highly relevant studies cited by included works but not retrieved through automated queries  

Although each repository requires a different query syntax, **the same conceptual keyword logic, inclusion filters, and constraints** were applied consistently across all platforms. Only syntax-level adaptations were made.

All retrieved records from **all repositories** were merged into a single dataset, forming the **Identification** stage of the PRISMA workflow.

Raw merged retrieval (all sources combined):  
`prisma/01_articles_per_source/articles.csv`

This file contains titles, abstracts, DOIs (when available), publication years, venues, and source identifiers.

---

### 1.2 Keyword design and search intent

The search strategy was explicitly designed to capture the **intersection of three core dimensions**:

1. **Aesthetic context**  
   aesthetic, esthetic, cosmetic, plastic, reconstructive, oncological  

2. **Surgical setting**  
   surgery  

3. **Computational task**  
   - **Prediction**: outcome prediction, simulation, pre-operative prediction, post-operative prediction  
   - **Evaluation**: evaluation, assessment, scoring  

To ensure methodological relevance and comparability, additional constraints were imposed:
- English-language publications  
- Journal articles  
- Subject areas limited to Computer Science and Engineering  

This design intentionally filters out purely clinical narratives, non-imaging approaches, and non-computational aesthetic discussions.

---

### 1.3 Example search strings (Scopus syntax)

The following queries illustrate the **Scopus implementation** of the search strategy.  
Equivalent queries were executed on PubMed, IEEE Xplore, and Semantic Scholar with syntax adaptations only.

#### Prediction of aesthetic outcomes

TITLE-ABS-KEY ( ("aesthetic" OR "esthetic" OR "cosmetic" OR "plastic" OR "reconstructive" OR "oncological")  
AND "surgery"  
AND ("outcome prediction" OR "simulation" OR "post-operative prediction" OR "pre-operative prediction") )  
AND ( LIMIT-TO ( DOCTYPE , "re" ) )  
AND ( LIMIT-TO ( SUBJAREA , "COMP" ) OR LIMIT-TO ( SUBJAREA , "ENGI" ) )  
AND ( LIMIT-TO ( LANGUAGE , "English" ) )  
AND ( LIMIT-TO ( SRCTYPE , "j" ) )

#### Evaluation of aesthetic outcomes

TITLE-ABS-KEY ( ("aesthetic" OR "esthetic" OR "cosmetic" OR "plastic" OR "reconstructive" OR "oncological")  
AND "surgery"  
AND ("evaluation" OR "assessment") )  
AND ( LIMIT-TO ( DOCTYPE , "re" ) )  
AND ( LIMIT-TO ( SUBJAREA , "COMP" ) OR LIMIT-TO ( SUBJAREA , "ENGI" ) )  
AND ( LIMIT-TO ( LANGUAGE , "English" ) )  
AND ( LIMIT-TO ( SRCTYPE , "j" ) )

---

## 2) Distribution of retrieved literature

After merging all retrieved records, we analyzed **repository-level contributions** to assess coverage, overlap, and redundancy.

![Distribution per source](figs/distribution_per_source.png)

### Interpretation

- **Scopus** contributes the largest share of records, reflecting its broad interdisciplinary indexing.  
- **IEEE Xplore** and **PubMed** provide complementary coverage, capturing engineering-centric and clinically oriented works respectively.  
- **Semantic Scholar** contributes additional relevant studies that may not be consistently indexed elsewhere.  
- **Manual backward search**, although smaller in volume, is critical for identifying seminal or domain-specific works missed by automated queries.

The presence of substantial contributions from multiple repositories confirms that the retrieval process is **not dominated by a single index** and that combining sources is essential for comprehensive coverage.

---

## 3) Vocabulary analysis and validation of the search strategy

To verify that the selected keywords and filters effectively captured the intended research space, we analyzed the **dominant vocabulary** of the retrieved corpus.

![Word cloud](figs/word_cloud.png)

### Interpretation

- Dominant terms such as *image*, *assessment*, *prediction*, *deep*, *model*, *surgery*, and *aesthetic* align directly with the review’s focus on **imaging-based computational prediction and evaluation of aesthetic outcomes**.  
- The co-occurrence of technical terms (*deep*, *network*, *model*) with clinical context (*patient*, *surgery*, *outcome*) confirms that the retrieved literature lies at the intended **intersection of AI and surgical aesthetics**.  
- The absence of prominent off-topic terminology indicates that the keyword design and filters were effective.

Together, the source distribution and vocabulary analysis provide strong qualitative evidence that the **search strategy was fruitful and well targeted**.

---

## 4) PRISMA workflow and screening stages

All retrieved records entered a PRISMA-compliant screening pipeline:

Identification → Duplicate Removal → Title Screening → Abstract Screening → Full-Text Screening → Qualitative Screening → Inclusion

![PRISMA workflow](figs/prisma.jpg)

### PRISMA flow numbers (fully backed by CSV files)

| Stage | Records |
|------|--------:|
| Identified | 1,027 |
| After duplicate removal | 939 |
| After title screening | 744 |
| After abstract screening | 386 |
| Full-text assessed | 250 |
| After qualitative screening | 182 |
| Final included | 182 (102 main + 85 supplementary) |

Each transition is traceable to a dedicated folder under `prisma/`.

---

## 5) Duplicate removal — `prisma/02_duplicate_removal/`

**Goal:** remove duplicate studies indexed across multiple repositories.

**Detection strategy**
- DOI matching (primary)
- Normalized title similarity (fallback)

**Files**
- `articles_duplicate_marked.csv` – all detected duplicates  
- `articles_rejected_by_duplicacy.csv` – removed records  
- `articles_after_duplicates.csv` – retained unique corpus  
- `articles_categorized.csv` – intermediate organization artifact (if used)

This step ensures that subsequent statistics and trends are not biased by indexing redundancy.

---

## 6) Title screening — `prisma/03_title_screening/`

**Goal:** remove clearly out-of-scope records conservatively.

**Typical exclusion reasons**
- Not related to surgery or not PR/oncological context  
- No aesthetic outcome focus  
- No computational or technical contribution  

**Files**
- `articles_titles_screened_marked.csv`  
- `articles_rejected_by_titles.csv`  
- `articles_after_title_screening.csv`

---

## 7) Abstract screening — `prisma/04_abstract_screening/`

**Goal:** enforce methodological relevance and lock the review taxonomy.

**Inclusion requirements**
- Addresses aesthetic outcome **prediction** or **evaluation**  
- Uses imaging data (2D or 3D)  
- Presents a computational method (not purely narrative)

**Files**
- `articles_abstract_screened_marked.csv`  
- `articles_rejected_by_abstract.csv`  
- `articles_after_abstract_screening.csv`

At this stage, task- and domain-level distributions become meaningful:

![Distribution per category](figs/distribution_per_category.png)

---

## 8) Full-text screening — `prisma/05_fulltext_screening/`

**Goal:** confirm eligibility using full-text evidence.

**Common exclusion reasons**
- Insufficient methodological detail  
- Weak or unclear evaluation protocol  
- Misalignment with aesthetic prediction/evaluation despite abstract wording  

**Files**
- `articles_full-text_screened_marked.csv`  
- `articles_rejected_by_full-text.csv`  
- `articles_after_full-text_screening.csv`

Conceptual structure of the retained literature:

![Co-occurrence graph](figs/co-occurance_graph.png)

This network highlights dominant methodological themes, subdomains, and cross-domain overlaps.

---

## 9) Qualitative / quality screening — `prisma/06_qualitive_fulltext_qualitive/`

**Goal:** ensure that the final corpus supports robust comparative synthesis.

**Quality dimensions**
- Novelty beyond incremental reporting  
- Technical rigor and clarity  
- Dataset adequacy and transparency  
- Evaluation validity and (when applicable) clinical relevance  
- Practical value for prediction/evaluation workflows  

**Files**
- `articles_qualitive_screened_marked.csv`  
- `articles_rejected_by_quality.csv`  
- `articles_after_qualitive_screening.csv`

---

## 10) Final included studies — `prisma/07_candidate_papers/`

- `candidate_papers.csv` — definitive included corpus used in tables, synthesis, and discussion

---

## 11) Evidence synthesis — `prisma/08_summarized_texts/`

- `combined_summs.xlsx` — unified synthesis  
- `summerized_per_tasks/`:
  - `Prediction.csv`
  - `Evaluation.csv`
  - `Datasets.csv`
  - `Reviews.csv`
  - `Subjective Evaluation.csv`
  - `Support Tasks.csv`

These files operationalize the review’s taxonomy, comparisons, limitations, and future directions.

---

## 12) Reproducibility and protocol statement

This review was not registered in PROSPERO due to its emphasis on **computer science, engineering, and imaging-based computational methodologies**, which extend beyond PROSPERO’s primary biomedical scope.

Transparency and reproducibility are ensured via:
- full public PRISMA audit trail  
- immutable CSV decision logs  
- explicit stage-level rejection files  

---

## 13) Repository hierarchy

review-paper tree  
├── README.md  
├── figs  
│   ├── prisma.jpg  
│   ├── distribution_per_source.png  
│   ├── distribution_per_category.png  
│   ├── trend_by_year.png  
│   ├── co-occurance_graph.png  
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
