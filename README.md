# AI/ML Thesis Landscape at FIS VŠE (2021–2025)

A data-driven analytical study mapping the AI/ML landscape in bachelor theses at the Faculty of Informatics and Statistics, Prague University of Economics and Business.

## Overview

This project analyzes 59 AI/ML-related bachelor theses defended at FIS VŠE between 2021 and 2025. The goal is to provide faculty leadership with an evidence base for strategic decisions around curriculum development, student recruitment, and industry partnerships — replacing anecdotal impressions with structured, reproducible analysis.

The corpus was collected from the [VŠKP repository](https://vskp.vse.cz) and filtered to Czech and Slovak theses with clear AI/ML relevance. Analysis is based primarily on abstracts and keywords, processed using a multilingual NLP pipeline.

## Analytical Views

| # | View | Method |
|---|------|--------|
| 1 | **Thematic map of AI/ML topics** | BERTopic + UMAP + HDBSCAN clustering on multilingual sentence embeddings |
| 2 | **Original research vs. tool deployment** | Rule-based classification using signal dictionaries on abstracts |
| 3 | **Temporal evolution of the AI/ML landscape** | Technology generation tracking + topic cluster trends (2021–2025) |
| 4 | **Application domains** | Keyword-based domain detection (finance, e-commerce, healthcare, ...) |
| 5 | **Technology landscape** | Regex-based tool/model extraction with curriculum momentum scoring |

## Key Findings

- **GPT dominates** — mentioned in 27% of all theses and still growing in 2024–2025
- **NLP and chatbots** are the largest thematic cluster; classical ML and computer vision are underrepresented
- **71% of theses deploy existing tools**; only 3% conduct original model research
- **Finance and e-commerce** are the most consistent application domains across years
- Classical ML frameworks (scikit-learn, PyTorch, TensorFlow) are nearly absent from student abstracts despite being industry staples

## Stack

```
Python 3.10+
sentence-transformers   # multilingual embeddings (paraphrase-multilingual-mpnet-base-v2)
BERTopic                # topic modeling
UMAP + HDBSCAN          # dimensionality reduction and clustering
pandas / matplotlib / seaborn
beautifulsoup4 + requests   # corpus scraping
pdfplumber
```

## Structure

```
├── Thesis_NLP.ipynb        # main analytical notebook
├── scraper_vskp.py         # corpus collection from vskp.vse.cz
├── corpus.csv              # final cleaned corpus (59 theses)
└── outputs/                # saved visualizations (.png) and tables (.csv)
```

## Running the Notebook

The notebook is designed for **Google Colab + Google Drive**. To run it locally, replace the `BASE_PATH` at the top of the notebook:

```python
# Instead of:
BASE_PATH = Path("/content/drive/MyDrive/textova_analytika_projekt")

# Use:
BASE_PATH = Path(".")
```

Then install dependencies:

```bash
pip install beautifulsoup4 bertopic hdbscan pandas pdfplumber requests \
            sentence-transformers stop-words tqdm umap-learn
```

## Context

This analysis was produced as a semester project for the course **Text Analytics 1 (4IZ172 / 4IZ577)** at FIS VŠE Prague. The scenario simulates a real consulting engagement: the Vice-Dean for Research commissioned a data-driven study to inform the faculty's Strategic Plan for AI/ML.
