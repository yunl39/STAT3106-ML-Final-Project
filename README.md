# STAT3106-ML-Final-Project
## Summary
## Explaination of the folders
## Data source:
Stock data is from the yahoo finance API

Reddit Data:
We used Reddit post data available through https://academictorrents.com/details/1614740ac8c94505e4ecb9d88be8bed7b6afddd4, which provides compressed .zst files containing full Reddit submissions. To parse these files, we followed the Python script provided in the PushshiftDumps GitHub repository (https://github.com/Watchful1/PushshiftDumps).
From the dataset, we extracted posts from six finance-focused subreddits: r/investing, \r/stocks, r/wallstreetbets, r/StocksAndTrading, r/stockstobuytoday, and r/investingforbeginners. 
We limited our extraction to posts created between January 1, 2022 and December 31, 2024. For each post, we collected the full text content, number of comments, score (an indicator of engagement and influence), upvote ratio, and the creation timestamp. The initial extraction yielded approximately 266,000 posts. However, many entries were incomplete or missing the full post content. To ensure data quality, we filtered out all posts lacking complete content, resulting in a final dataset of 92,237 high-quality posts. All subsequent analyses presented in this study are based on this cleaned and filtered dataset.

