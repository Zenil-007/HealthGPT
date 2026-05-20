# 🩺 HealthGPT – Cardiovascular Literature Assistant

HealthGPT is a **medical literature retrieval assistant** built to help doctors, researchers, and healthcare professionals search through large-scale biomedical research papers using natural language queries.

It uses **PubMed metadata**, **PMC full-text papers**, **semantic embeddings**, and **FAISS vector search** to retrieve relevant medical evidence and present it in a chatbot-style interface.

---

# 🚀 Problem Statement

Doctors and researchers often need to search through hundreds of research papers to find evidence related to cardiovascular diseases.

Traditional keyword-based search has limitations:
- Exact keyword dependency
- Poor semantic understanding
- Difficult section-level retrieval
- Slow literature review process

HealthGPT solves this by enabling **semantic search over medical literature**.

Example:

**User Query:**
> Does smoking increase coronary artery disease risk?

HealthGPT retrieves:
- Relevant research papers
- PMID
- Discussion / Results / Methods sections
- Evidence snippets
- Relevance score

---

# 🎯 Objective

To build a **Doctor Research Assistant (RAG-based chatbot)** capable of:
- Searching biomedical literature using natural language
- Understanding semantic medical queries
- Retrieving evidence from PubMed / PMC papers
- Returning medically relevant sections
- Assisting literature review

---

# 🏗️ Architecture

```text
PubMed + PMC Corpus
        ↓
Metadata + Abstract Collection
        ↓
Full-Text XML Extraction
        ↓
XML Parsing
        ↓
Section-wise Chunking
        ↓
Embedding Generation
        ↓
FAISS Vector Index
        ↓
Semantic Retrieval
        ↓
Chatbot UI
```

---

# 📚 Dataset Sources

## 1. PubMed
Used for:
- Metadata
- Abstracts
- PMID
- Journal
- Authors
- DOI
- MeSH terms
- Study types

## 2. PubMed Central (PMC)
Used for:
- Full-text XML papers
- Methods
- Results
- Discussion
- Conclusion

---

# 📊 Corpus Built

### Medical Papers
- 299 PubMed research papers

### Full-text Papers
- 123 PMC XML papers

### Parsed Research Corpus
- Section-aware biomedical content

### Chunks Created
- 3467 semantic chunks

---

# 🧠 Core Concepts Used

## 1. Retrieval-Augmented Generation (RAG)
Instead of training a model directly, relevant medical knowledge is retrieved from a vector database.

Why:
- Reduces hallucination
- Supports evidence-based retrieval
- Easily expandable with new papers

---

## 2. Semantic Search
HealthGPT does not depend on exact keywords.

Example:
"Smoking" → retrieves:
- tobacco exposure
- cigarette usage
- vascular damage
- endothelial dysfunction

Used embeddings for meaning-based similarity.

---

## 3. Vector Similarity Search
Medical chunks converted into vectors.

Used:
FAISS

Purpose:
- Fast nearest-neighbor retrieval
- Scalable search

---

## 4. Chunking Strategy
Full papers were split by sections:
- Abstract
- Methods
- Results
- Discussion
- Conclusion

This improved precision.

---

## 5. Embeddings
Converted medical text into dense vectors.

Model:
BAAI/bge-small-en-v1.5

---

## 6. Metadata-Aware Retrieval
Each chunk stores:
- PMID
- Title
- Section
- Study information

Improves explainability.

---

# ⚙️ Technologies Used

## Programming
- Python

## Data Collection
- Biopython (NCBI Entrez API)
- Requests

## Data Processing
- Pandas
- BeautifulSoup
- JSON
- XML Parsing

## NLP / Semantic Search
- Sentence Transformers
- BAAI/bge-small-en-v1.5

## Vector Database
- FAISS

## RAG Pipeline Concepts
- Chunking
- Embeddings
- Retrieval
- Metadata indexing

## UI
- Gradio (Jupyter-friendly chatbot UI)
- Streamlit (prototype UI)

---

# 📂 Project Structure

```bash
HealthGPT/
│
├── data/
│   ├── raw/
│   ├── fulltext_xml/
│   ├── parsed_fulltext/
│   ├── chunks/
│   └── vector_db/
│
├── notebooks/
├── app/
├── rag/
└── README.md
```

---

# 🔍 Pipeline Workflow

## Step 1 — PubMed Ingestion
Fetched biomedical papers using NCBI Entrez API.

Extracted:
- PMID
- Title
- Abstract
- Journal
- DOI
- MeSH terms
- Study type

---

## Step 2 — PMC Full Text Extraction
Downloaded available XML full-text papers.

---

## Step 3 — XML Parsing
Extracted:
- Abstract
- Methods
- Results
- Discussion
- Conclusion

---

## Step 4 — Section-wise Chunking
Created smaller semantic chunks.

Final chunks:
3467

---

## Step 5 — Embedding Generation
Generated dense vector embeddings.

Model:
BAAI/bge-small-en-v1.5

---

## Step 6 — FAISS Indexing
Stored embeddings for high-speed retrieval.

---

## Step 7 — Semantic Retrieval
Doctor query converted into vector → nearest chunks retrieved.

---

## Step 8 — Chatbot UI
Jupyter-compatible chatbot.

Features:
- Query input
- Evidence retrieval
- PMID references
- Section highlighting

---

# 🧪 Example Queries

- Does smoking increase coronary artery disease risk?
- What is the role of LDL in atherosclerosis?
- How does hypertension affect cardiovascular mortality?
- Compare LDL and HDL effects on plaque progression.
- Are there contradictory findings on HDL and CAD risk?

---

# 📈 Future Improvements

- Add reranker model
- Add LLM answer synthesis
- Add contradiction detection
- Add citation scoring
- Add multi-specialty medical corpus
- Add doctor-grade evidence ranking
- Add BioBERT embeddings
- Add fine-tuned biomedical summarization

---

# ⚠️ Disclaimer

HealthGPT is intended for:
- Research support
- Literature review
- Educational use

It is **NOT** a medical diagnosis system.

---
Built as an AI + Healthcare RAG project focused on semantic medical literature retrieval.
