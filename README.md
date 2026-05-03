# Information Retrieval (IR) System Portfolio: Cranfield Collection

This repository contains the implementation, evaluation, and comparative analysis of various Information Retrieval models using the **Cranfield Scientific Dataset** (1,400 abstracts, 225 queries). The project focused on transitioning legacy Python 2 frameworks into a modern Python 3.12 environment and benchmarking custom-built indexing against professional-grade tools like Elasticsearch.

### 👥 Team Members
| Name | Student ID |
| :--- | :--- |
| Nekodimos Million | UGR/1428/17 |
| Dawit Tekeba | UGR/2102/17 |
| Adonay Teferi | UGR/0142/17 |
| Abreham Mehari | UGR/7169/17 |

---

### 📄 Project Documentation
The **Root Directory** of this repository contains the comprehensive **Document Analysis (PDF)**. This report includes:
*   In-depth comparison of all retrieval models.
*   Linguistic analysis of the Cranfield Collection.
*   
## 📂 Project Structure

### [HW1: Elasticsearch Baseline Retrieval](./HW1)
**Location:** `/HW1`  
The objective of this phase was to establish a retrieval baseline using Elasticsearch.
*   **`Evaluation_Reports/`**: Contains the full statistical output from the `trec_eval` utility for all models (MAP, P@10, Recall).
*   **`Files/`**: Stores the raw output `.txt` result files formatted for TREC evaluation.
*   **`Pickles/`**: Serialized Python objects (using `dill`) containing document frequency (DF) and total term frequency (TTF) metadata extracted from the index.
*   **`Manual_Comparison_Report.txt`**: A qualitative analysis of Case Studies (Query ID 1, 20, 50, 100, and 200) comparing how different models "think" when ranking the same query.

### [HW2: Custom Search Engine & Indexing](./HW2)
**Location:** `/HW2`  
In this phase, we replaced Elasticsearch with a custom-engineered Inverted Index built from scratch.
*   **`Files/`**: Contains the physical binary index (`invertedFile.txt`) and the catalog system designed for logarithmic-time access to term postings.
*   **`Pickles/`**: Core metadata including the `termMap`, `docMap`, and `catalog` offsets used by the search engine.
*   **`Results/`**: Final ranking outputs for the custom engine, including results for **Stemmed** vs. **Unstemmed** configurations.
*   **`stoplist.txt`**: The specific list of NLTK stopwords used during the tokenization process to filter non-informative terms.

---

## 🚀 Key Technical Highlights

### 1. Refactoring & Modernization
*   Migrated the entire codebase from Python 2 to **Python 3.12**.
*   Implemented a custom **NumPy 2.0 Patch** to maintain compatibility with modern scientific computing libraries while running legacy scoring logic.

### 2. Custom Indexing (HW2 vs HW1)
*   Developed a **Merge-Sort Indexing strategy** to handle document batches, ensuring high performance without excessive memory usage.
*   Achieved superior accuracy with our custom system compared to the Elasticsearch baseline. **Custom TF-IDF (MAP: 0.3089)** outperformed the **Elasticsearch TF-IDF (MAP: 0.2913)** due to more precise scientific tokenization.

### 3. Preprocessing Impact
*   **Stemming:** Validated that Porter Stemming is critical for technical datasets. Adding stemming provided a **11.4% accuracy boost** for TF-IDF and an **8.6% boost** for BM25.

---

## ⚠️ Note on Remaining Homeworks (HW4+)
The original project repository provided by the instructor included placeholders or skeletal code for HW4 through HW7 (covering Link Analysis, PageRank, and HITS). 

**These assignments were not carried out because:**
1.  They lacked associated **README.md** instruction files.
2.  The required external datasets (such as the **WT2G Web Crawl** link graph) were not provided.
3.  The codebase for these sections relied on a pre-existing "hw3_crawl" Elasticsearch index that was unavailable in the current research environment.

Consequently, this portfolio serves as a finalized evaluation of text-based retrieval models (HW1 & HW2), which constitute the core of the Cranfield Collection research goals.

---
