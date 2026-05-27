# IMDb Sentiment Analysis — Text Preprocessing Module

A structured NLP preprocessing pipeline built on the IMDb movie review dataset. This is **Phase 1** of a complete end-to-end sentiment analysis system, focused on cleaning and normalizing raw text for downstream machine learning tasks.

---

## Overview

Raw movie reviews contain noise — HTML tags, punctuation, emojis, stopwords, and inflected word forms — that can degrade model performance. This module transforms messy review text into clean, normalized input ready for feature engineering and classification.

**Downstream applications:**
- Sentiment analysis and text classification
- Feature engineering (TF-IDF, Bag-of-Words, n-grams)
- Machine learning modeling (Logistic Regression, SVM, Neural Networks)

---

## Preprocessing Pipeline

All steps are encapsulated in a single reusable function.

| Step | Operation | Description |
|------|-----------|-------------|
| 1 | Lowercasing | Normalize case across all tokens |
| 2 | HTML tag removal | Strip `<br/>`, `<div>`, and other markup |
| 3 | URL & special char removal | Clean links, symbols, and punctuation |
| 4 | Emoji handling | Remove or convert emoji characters |
| 5 | Tokenization | Split text into individual word tokens |
| 6 | Stopword removal | Drop common words via NLTK (`the`, `is`, `was`…) |
| 7 | Lemmatization | Reduce words to base form via spaCy |
| 8 | Text reconstruction | Rejoin tokens into a final clean string |

### Before vs. After

```
Input:   "I loved this movie!!! 😍 It was amazing <br /> Best film ever."
Output:  "love movie amazing best film"
```

---

## Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Dataset loading and manipulation |
| `nltk` | Tokenization and stopword removal |
| `spacy` | Lemmatization (`en_core_web_sm`) |
| `re` | Regex-based cleaning |

---

## Getting Started

### 1. Install dependencies

```bash
pip install pandas nltk spacy
python -m spacy download en_core_web_sm
```

### 2. Download NLTK data

```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
```

### 3. Run the pipeline

```python
from preprocessing import clean_text

raw = "I loved this movie!!! 😍 It was amazing <br /> Best film ever."
cleaned = clean_text(raw)
# → "love movie amazing best film"
```

---

## Project Roadmap

This repository represents Phase 1 of a complete NLP pipeline.

- [x] **Phase 1** — Text preprocessing (this module)
- [ ] **Phase 2** — Feature engineering (TF-IDF, CountVectorizer, n-grams)
- [ ] **Phase 3** — Sentiment classification model
- [ ] **Phase 4** — Model evaluation and visualization
- [ ] **Phase 5** — Performance comparison: raw vs. cleaned input

---

## Why This Matters

Text preprocessing is the foundation of any production NLP system. A well-designed pipeline:

- Reduces vocabulary size and model complexity
- Surfaces the semantically meaningful tokens
- Ensures consistent input across training and inference
- Makes downstream feature extraction more effective

This module demonstrates clean pipeline design, reusable function architecture, and real-world dataset handling — key skills for building end-to-end NLP systems.

---

## Author

Built as part of a personal NLP learning journey toward developing complete end-to-end sentiment analysis systems.
