# Exploring Semantic Search and Transformer Architectures

## Project Overview

This project focuses on building an advanced semantic search and document ranking pipeline using both traditional Information Retrieval (IR) techniques and deep learning-based transformer architectures.

The system was designed to improve search relevance by combining:
- BM25-based lexical retrieval
- Transformer-based Cross Encoder ranking
- BiGRU-based neural ranking
- Semantic similarity learning using BERT embeddings

The project explores how modern NLP architectures can improve search quality beyond simple keyword matching.

---

# Objective

Traditional search systems rely heavily on keyword overlap, which often fails to capture semantic meaning.

This project aims to:
- Retrieve relevant passages for user queries
- Improve ranking quality using deep learning
- Compare traditional retrieval vs neural ranking
- Understand semantic search pipelines used in modern AI systems

---

# Workflow

## Step 1 — Dataset Preparation

A subset of the MS MARCO passage ranking dataset was used.

### Files Used
- `collection.tsv`
- `queries.train.tsv`
- `qrels.train.tsv`

The dataset preparation phase involved:
- Loading passages and query datasets
- Mapping relevant query–document pairs
- Creating labeled datasets for training and evaluation

Notebook:
- `step1a_build_label_dataset.ipynb`

---

## Step 2 — BM25 Candidate Retrieval

A traditional BM25 retrieval pipeline was implemented using the `rank_bm25` library.

### Purpose
Instead of passing all documents into deep learning models, BM25 was first used to retrieve the top candidate passages for each query.

### Process
- Tokenized all passages
- Built BM25 indices
- Retrieved top-k relevant passages
- Stored candidate rankings

Notebook:
- `step1_bm25_subset.ipynb`

### Why This Matters
This significantly reduces computational cost while preserving retrieval quality.

---

## Step 3 — Building Training Pairs

Training pairs were generated using:
- User query
- Relevant passage
- Non-relevant passage

### Process
- Combined BM25 candidates with relevance labels
- Created positive and negative ranking examples
- Generated training datasets for neural models

Notebook:
- `step2_build_training_pairs.ipynb`

---

# Deep Learning Models

## 1. Transformer-based Cross Encoder

A BERT-based Cross Encoder architecture was implemented for semantic ranking.

### Architecture
- `bert-base-uncased`
- Fully connected ranking layer
- Query and passage jointly encoded

### Features
- Context-aware semantic matching
- Better understanding of sentence relationships
- Deep semantic relevance scoring

### Training
- Tokenization using Hugging Face tokenizer
- Sequence truncation and padding
- Binary relevance prediction

Notebook:
- `transformer copy.ipynb`

---

## 2. BiGRU Neural Ranker

A BiGRU-based ranking model was implemented as a lightweight neural alternative.

### Architecture
- Embedding layer
- Bidirectional GRU
- Attention-style pooling
- Dense ranking layers

### Purpose
- Faster inference
- Reduced computational complexity
- Neural ranking without full transformers

Notebook:
- `bigru_ranker.ipynb`

---

# Inference and Testing

Two separate inference pipelines were implemented:

## Transformer Inference
Notebook:
- `example_working copy.ipynb`

### Workflow
1. User query is given
2. BM25 retrieves top candidates
3. Cross Encoder reranks candidates
4. Most semantically relevant passages are returned

---

## BiGRU Inference
Notebook:
- `bigru_example_working.ipynb`

### Workflow
1. Query preprocessing
2. Vocabulary encoding
3. Neural relevance scoring
4. Ranked output generation

---

# Technologies Used

## NLP and Deep Learning
- Python
- PyTorch
- Hugging Face Transformers
- BERT
- BiGRU

## Information Retrieval
- BM25
- rank_bm25

## Data Processing
- Pandas
- NumPy
- tqdm

---

# Key Learnings

This project helped in understanding:
- Semantic search systems
- Transformer architectures
- Neural ranking pipelines
- Information retrieval systems
- Query-document relevance learning
- Hybrid search architectures

---

# Outcomes

The project successfully demonstrated:
- Improved semantic ranking over traditional keyword matching
- Transformer-based contextual understanding
- Efficient candidate retrieval using BM25
- Practical implementation of modern NLP retrieval pipelines

---

# Repository

GitHub Repository:
https://github.com/ved-source/Exploring-semantic-search-and-Transformers-architectures
