# TORA-DSS-2026
This collection serves as an online repository for the TORA framework introduced in the Decision Support Systems paper [Ref], including metadata, code used for empirical data collection and community rule collection, and prompt templates used with large language models.

<mark>The research project consists of THREE primary stages of implementation.</mark>

## Stage 1: Empirical Data Collection
The project begins with empirical data collection, involving daily data retrieval from selected subreddits

Due to content moderation practices on social media platforms and API limitations imposed by Reddit, each request allows you to collect up to 500 posts, depending on the filtering criteria applied.

| Variable Name | Definition |
|--------------|------------|
| Subreddit | The name of the Reddit community where the post was published (e.g., r/reddit). It represents the topic or category of the post. |
| Post ID | A unique identifier assigned by Reddit to each post. It is used to distinguish and retrieve individual posts from the API or dataset. |
| Post Title | The headline of the Reddit post. It summarizes the main idea or topic of the post and is the first text users see. |
| Post Text | The main body content of the post. This is optional and may be empty if the post is a link-only or image-based submission. |
| Post Author | The Reddit username of the person who created the post. |
| Post Created | The timestamp indicating when the post was published on Reddit, usually stored in UTC format or Unix timestamp. |

[Data Collection - Daily Post Collection](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Post%20Collection.ipynb)

[Data Collection - Post Repull](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Post%20Collection.ipynb)

[Data Collection - Rule Scraping](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Post%20Collection.ipynb)
