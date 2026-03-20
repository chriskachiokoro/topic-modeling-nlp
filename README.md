# BERTopic Topic Modeling on IMDB Movie Reviews

This project applies **BERTopic** to a sample of IMDB movie reviews to uncover the main themes people discuss when reviewing films. Instead of focusing only on sentiment, the project explores *what* viewers are talking about, such as horror content, TV episodes, movie quality, plot structure, and musicals.

## Project Overview

The dataset used in this project is the **IMDB Movie Reviews** dataset from Kaggle. A random sample of **2,500 reviews** was taken from the test split of **25,000 reviews** to balance computational efficiency with topic diversity.

The goal was to identify recurring topics in movie reviews using **BERTopic**, supported by transformer embeddings and improved preprocessing.

## Objectives

- Explore recurring themes in IMDB reviews beyond positive/negative sentiment
- Compare minimal vs improved preprocessing for topic modeling
- Improve topic interpretability using `CountVectorizer`
- Analyze the most frequent discovered topics
- Visualize topic frequency and topic similarity

## Dataset

- **Source:** Kaggle IMDB Movie Reviews dataset
- **Original purpose:** Binary sentiment classification
- **Sample used:** 2,500 reviews from the 25,000-review test split

## Methodology

### 1. Text Preprocessing

Two preprocessing approaches were explored:

#### Minimal preprocessing
- Lowercasing
- URL removal

This produced few, highly imbalanced topics.

#### Improved preprocessing
- Lowercasing
- HTML tag removal
- URL removal
- Contraction expansion
- Non-alphabetic character removal
- Whitespace normalization

This improved topic stability and interpretability.

### 2. Topic Modeling

Topic modeling was performed with **BERTopic** using:

- **Embedding model:** `all-MiniLM-L6-v2`
- **Vectorizer:** `CountVectorizer`
- **Stopword removal:** English stopwords removed
- **Goal:** produce cleaner, more meaningful topic representations

## Results

BERTopic identified **34 topics** from the 2,500 sampled reviews.

- **Outlier topic (-1):** 1,235 reviews
- Most interpretable and frequent topics included:

| Topic | Theme | Frequency |
|------|-------|----------:|
| 0 | Horror movies | 152 |
| 1 | TV episodes and series | 130 |
| 2 | Movie quality, acting, effects | 123 |
| 3 | Plot, crime, police storylines | 82 |
| 4 | Musicals, dancing, stage productions | 61 |

## Key Findings

- Preprocessing quality strongly influenced BERTopic output
- Minimal cleaning produced noisier and less balanced topics
- Adding `CountVectorizer` improved topic interpretability by reducing stopword-heavy topic labels
- Topic `-1` captured many outlier reviews that did not strongly align with a single theme
- Topic similarity analysis showed strong overlap between horror-related and crime/plot-related discussions

## Visualizations

The project includes:
- Topic frequency distribution with topic names
- Topic similarity matrix
- Topic info comparison between:
  - default BERTopic pipeline
  - BERTopic + `CountVectorizer`

## Tech Stack

- Python
- pandas
- BERTopic
- sentence-transformers
- scikit-learn
- CountVectorizer
- UMAP
- HDBSCAN
- matplotlib / plotly

## Repository Structure

```bash
topic-modeling-imdb/
│
├── topic_modeling.ipynb
├── README.md
├── requirements.txt
├── images/
│   ├── topic_freq_minimal.png
│   ├── topic_freq_improved.png
│   ├── topic_info_basic.png
│   ├── topic_info_vectorizer.png
│   ├── topic_freq_named.png
│   └── topic_similarity_matrix.png
└── report/
    └── Z639_Topic_Modeling_Report_cookoro.docx
