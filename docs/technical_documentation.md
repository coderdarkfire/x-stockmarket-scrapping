Technical Documentation

Project: Stock Market Tweets Scraper & Analyzer
Author: Saksham Purohit

1. Introduction

This project scrapes, processes, and analyzes Twitter/X data related to the Indian stock market.
It is optimized for real-time collection, memory efficiency, and converting unstructured tweets into trading signals.

2. Architecture Overview
main.py
│
├── scraper.py      # Handles scraping using Playwright + BeautifulSoup
├── processor.py    # Cleans, normalizes, and deduplicates tweets
├── analysis.py     # TF-IDF, sentiment analysis, and signal generation
│
├── data/           # Stores raw and processed datasets
│   ├── indian_stock_tweets.parquet
│   └── sample_output.csv
│
├── requirements.txt
└── README.md

3. Data Collection

Tools Used:

Playwright (headless Chromium browser for dynamic scraping)

BeautifulSoup (HTML parsing)

Target Hashtags:

#nifty50, #sensex, #banknifty, #intraday

Extracted Fields:

Username

Timestamp

Content

Mentions

Hashtags

Engagement metrics (likes, retweets, replies)

Anti-Bot Measures:

Randomized delays between scrolls

Incremental scrolling until no new tweets load

Auth token cookies for authenticated scraping

4. Data Processing

Deduplication: Unique key = username + timestamp + content

Normalization:

Unicode normalization (NFKC)

Lowercasing

Trimming whitespace

Storage: Saved in Parquet (preferred) for efficiency, with fallback CSV sample.

5. Analysis & Signal Generation

Vectorization:

TF-IDF with max_features=5000

Sentiment Analysis:

TextBlob polarity scores ∈ [-1,1]

Signal Formula:

signal = sentiment + 0.001*(likes + retweets + replies)


Visualization:

Lightweight plots with data sampling

Memory-efficient processing

6. Performance & Scalability

Data Structures: deque(maxlen=10000) for memory-efficient streaming

Concurrency: Playwright handles multiple hashtags sequentially with minimal overhead

Scalability: Designed to scale for 10x more tweets by:

Efficient I/O with Parquet

Deduplication

Incremental saving after each hashtag

7. Setup & Usage
Installation
git clone https://github.com/coderdarkfire/x-stockmarket-scrapping.git
cd x-stockmarket-scrapping
python -m venv myenv
source myenv/bin/activate   # On Windows: myenv\Scripts\activate
pip install -r requirements.txt

Run the Project
python main.py

Notes

Requires Twitter Auth Token (auth_token & ct0) for scraping.

If tokens are missing or scraping fails, you can use the sample dataset:

data/sample_output.csv

8. Limitations

Dependent on Twitter/X front-end structure (can break if layout changes).

Requires valid authentication tokens.

Sentiment analysis (TextBlob) is simplistic; domain-specific models may improve accuracy.

9. Future Improvements

Use deep learning embeddings (e.g., BERT, FinBERT) for better sentiment.

Implement async scraping for faster throughput.

Integrate a database (PostgreSQL/ClickHouse) for scalable storage.

Deploy pipeline with Airflow or Prefect for automation.
