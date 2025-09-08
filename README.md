# Indian Stock Market Signal Pipeline
Project overview...
This project collects, processes, and analyzes tweets related to the Indian stock market from Twitter/X.
It was built as part of a web scraping assignment with a focus on efficient data handling, real-time processing, and meaningful insights for algorithmic trading.

Key Features

Web Scraping: Collects live tweets using Playwright and BeautifulSoup without paid APIs.

Target Hashtags: #nifty50, #sensex, #banknifty, #intraday.

Extracted Data: Username, timestamp, tweet content, mentions, hashtags, replies, retweets, and likes.

Data Storage: Deduplicated and saved in Parquet format (with fallback to sample CSV).

Text Processing: Cleans and normalizes text (handles Unicode/Indian languages).

Signal Generation: Converts tweets into quantitative signals using TF-IDF vectors, sentiment analysis, and engagement metrics.

Scalability: Designed with efficient data structures (deque), rate-limit handling, and support for processing 10x more data.

Visualization: Lightweight plotting methods suitable for large datasets.

Deliverables

Complete codebase with modular structure (scraper.py, processor.py, analysis.py, main.py).

Requirements file (requirements.txt) for environment setup.

Sample dataset (data/sample_output.csv) for quick testing.

Detailed documentation inside code and this README.
