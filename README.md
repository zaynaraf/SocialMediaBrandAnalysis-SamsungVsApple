# Reddit Smartphone Brand Intelligence: Samsung vs Apple

An end-to-end social media analytics project comparing public Reddit discussion around recent iPhone and Samsung Galaxy S-series smartphones. The analysis combines Reddit data collection, text cleaning, LLM-assisted product labeling, transformer-based sentiment analysis, topic modeling, and visual reporting to surface how users discuss competing smartphone models.

## Project Snapshot

- **Domain:** Social media analytics, consumer intelligence, brand perception
- **Platforms/Data:** Reddit posts and comments from smartphone-related subreddits
- **Brands:** Apple iPhone and Samsung Galaxy S series
- **Main objective:** Compare sentiment and discussion themes by brand, model, and topic
- **Primary workflow:** Data collection -> cleaning -> target labeling -> sentiment analysis -> topic modeling -> visualization

## What This Project Demonstrates

- Built a Reddit data pipeline with `PRAW` to collect posts, comments, metadata, timestamps, authors, scores, and engagement signals.
- Cleaned and filtered noisy social text using deduplication, date filters, bot/deleted-user handling, keyword relevance checks, language detection, and NLP-ready normalization.
- Used LLM-assisted labeling with Gemma to identify phone models mentioned or implied in context-rich Reddit comments.
- Standardized weak labels into a controlled taxonomy for iPhone 14/15 and Samsung S22/S23/S24 model families.
- Fine-tuned a DeBERTa-based multi-label classifier to predict smartphone model targets across posts and comments.
- Applied a RoBERTa social-media sentiment model to classify text into positive, neutral, and negative sentiment.
- Aggregated sentiment at user, brand, model, and topic levels to support more granular interpretation.
- Used BERTopic and sentence embeddings to discover recurring discussion themes such as camera quality, battery, display, performance, overheating, pricing, and device comparisons.
- Created visualization-ready datasets and charts for brand-level, model-level, and topic-level sentiment comparison.

## Repository Structure

```text
.
|-- README.md
|-- requirements.txt
|-- docs/
|   |-- presentation.pdf
|   `-- report.pdf
`-- notebooks/
    `-- reddit_smartphone_brand_analysis.ipynb
```

## Deliverables

- [Analysis notebook](notebooks/reddit_smartphone_brand_analysis.ipynb) - full workflow with saved outputs.
- [Final report](docs/report.pdf) - written project report.
- [Presentation deck](docs/presentation.pdf) - summary slides for communicating findings.

## Methodology

### 1. Reddit Data Collection

Posts and comments were collected from smartphone and brand-specific subreddits using the Reddit API through `PRAW`. The dataset includes titles, post bodies, comment text, URLs, timestamps, scores, comment counts, author fields, and parent-thread context.

### 2. Data Cleaning and Filtering

The cleaning pipeline removes duplicates, deleted or bot-generated content, low-information text, non-English content, and irrelevant posts. Text was normalized for downstream NLP while preserving model identifiers such as iPhone 15 Pro, S24 Ultra, and related product variants.

### 3. Model Target Labeling

Gemma was used to label whether each Reddit comment referred to a specific smartphone model. Labels were standardized into a controlled taxonomy and used to prepare a supervised dataset for model-target classification.

### 4. Transformer Modeling

The project uses a DeBERTa-based multi-label classification workflow for smartphone model detection, followed by RoBERTa-based sentiment analysis optimized for social media text. This creates a structured dataset linking each post or comment to predicted phone models and sentiment labels.

### 5. Topic Modeling and Visualization

BERTopic was used to cluster discussion themes from Reddit text. The final analysis compares sentiment by brand, individual model, and topic so that broad brand perception can be interpreted alongside specific product issues and strengths.

## Key Insight

Brand-level sentiment alone can hide important differences. The analysis shows that Reddit users often express different opinions depending on the exact model and topic being discussed, such as camera quality, battery life, display performance, overheating, software experience, or pricing.

## Tools and Technologies

`Python`, `Jupyter Notebook`, `Google Colab`, `PRAW`, `pandas`, `NumPy`, `langdetect`, `Hugging Face Transformers`, `PyTorch`, `DeBERTa`, `RoBERTa`, `Gemma`, `BERTopic`, `Sentence Transformers`, `scikit-learn`, `NLTK`, `Matplotlib`, `Seaborn`

## Portfolio Keywords

NLP, social media analytics, sentiment analysis, topic modeling, brand analytics, consumer intelligence, Reddit data mining, transformer models, LLM-assisted annotation, weak supervision, multi-label classification, text classification, data cleaning, feature engineering, Hugging Face, BERTopic, Python data science, machine learning workflow, data visualization.

## Notes on Reproducibility

The notebook contains saved outputs from the completed workflow. Re-running the full pipeline requires Reddit API credentials, access to the original working data location, a Gemini/Gemma API setup, and sufficient compute for transformer inference and fine-tuning. Raw data, API keys, local model checkpoints, and generated intermediate artifacts are intentionally not included in the repository.

## Authors

Anas Mahfooz and Arib Zayn Araf

