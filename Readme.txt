Project Title: iPhone vs. Samsung: A Reddit Deep Dive
Authors: Anas Mahfooz & Arib Zayn Araf

Project Overview:
This project investigates public sentiment and discussion topics surrounding recent iPhone and Samsung Galaxy S series smartphones on Reddit. The primary objectives were to collect, clean, and analyze Reddit data to understand user opinions, identify prevalent discussion themes, and visualize comparative sentiment between the two major smartphone brands.

Methodology:

Data Collection:
- Source: Reddit, utilizing the PRAW (Python Reddit API Wrapper) library.
- Subreddits: r/Android, r/Apple, r/GalaxyS23, r/GalaxyS24, r/iPhone, r/Smartphones, r/samsung.
- Data Points: Post titles, body text, URLs, creation timestamps, comment counts, scores, and author information.
- Timeframe: Discussions posted after June 1, 2023.
- Storage: Initial raw data saved in JSON Lines (.jsonl) format.

Data Cleaning:
- Duplicate Removal: Eliminated redundant posts and comments.
- Date Filtering: Ensured content adhered to the specified date range.
- Bot and Deleted User Exclusion: Filtered out content from automated accounts (e.g., AutoModerator) and deleted users.
- Keyword-Based Relevance: Used a comprehensive keyword list covering iPhone (14, 15, Pro, Pro Max, Mini) and Samsung Galaxy S series (S22, S23, S24, Ultra, Plus) models.
- Content Length Filtering: Removed exceptionally short or empty entries.
- Language Identification: Used 'langdetect' to retain only English-language content.
- Text Normalization for NLP: Converted text to lowercase, removed URLs, Reddit-specific mentions (r/, u/), and most non-alphabetic characters.

LLM-Based Labeling:
- Model: Google's Gemma-3-27b-it.
- Task: Identify specific iPhone or Samsung Galaxy S series models discussed or implied in each cleaned comment.
- Contextual Input: Provided the comment, post title/body, and parent comment body to enhance contextual understanding.
- Irrelevance Handling: Non-relevant comments were labeled as "None".
- Output Format: Labels were generated in a structured JSON array format.

Sentiment Analysis:
- Model: Pre-trained RoBERTa ('cardiffnlp/twitter-roberta-base-sentiment-latest').
- Fine-tuning: Model fine-tuned on a subset of Gemma-labeled data for domain-specific sentiment detection.
- Evaluation Metrics: Monitored F1-score, precision, and recall during training.
- Output: Each post/comment was assigned a sentiment label (positive, neutral, negative) and a sentiment score.

User-Level Sentiment Aggregation:
- Consolidation: Combined all cleaned posts and comments.
- Author Filtering: Excluded deleted or bot accounts.
- Model Identification: Determined the primary phone model discussed.
- Aggregation: Grouped by 'author' and 'predicted_model' to compute average sentiment and contribution counts.

Topic Modeling:
- Method: BERTopic.
- Embeddings: Used 'all-MiniLM-L6-v2' for text embedding.
- Clustering: Clustered embeddings to identify coherent topics and representative keywords.
- Topic Mapping: Manually assigned descriptive names (e.g., "Battery Performance & Charging", "Screen & Display Issues").
- Filtering: Removed generic or off-topic clusters.
- Data Enrichment: Appended topic IDs and names to the content.

Visualizations:
- Overall Sentiment by Brand: Bar chart showing sentiment distribution (positive/neutral/negative) for iPhone vs. Samsung.
- Sentiment by Phone Model: Grouped bar charts for sentiment distribution across individual phone models.
- Sentiment by Topic per Model: Bar charts showing sentiment variation per model across key discussion topics.

Key Findings:
The analysis shows that while overall sentiment may favor one brand or the other, opinions vary significantly when broken down by model and topic. For instance, users may praise the iPhone 15 Pro's camera while criticizing its battery, or admire the Samsung S24 Ultra's display but raise concerns about overheating. This underscores the value of topic-level analysis rather than relying solely on overall sentiment.
