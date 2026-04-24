# TORA-DSS-2026
This collection serves as an online repository for the TORA framework introduced in the Decision Support Systems paper [Ref], including the framework, metadata, data-collection code, community-rule collection code, and prompt templates used with large language models.

## Empirical Data Collection

### 🚨 Step 1: Daily Data Collection

#### Prerequisites

- Reddit Developer Access: Create a [Reddit developer account](https://developers.reddit.com/) to obtain the credentials required for API-based data collection. If necessary, submit a request for research access to the Reddit dataset, which is subject to Reddit’s review and approval.
  
- Subreddit Selection: Identify the subreddits to be included in the data collection process based on the objectives of your study.
  
- Collection Configuration: Given Reddit API constraints and platform-specific moderation practices, each request can retrieve up to 1,000 items. Configure the retrieval process using an appropriate sorting option (e.g., hot, new, or top) to minimize overlap across daily collection intervals.

📥 
To begin the daily data collection from selected subreddits, please refer to the code provided here: 

[Daily Data Collection](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Data%20Collection.ipynb)

### 🚨 Step 2: Data Repull (Moderation Decision Verification)
To enhance ecological validity, a second round of data collection should be conducted after a suitable time interval to confirm the moderation status of previously collected posts. Three cases are considered during this verification process:

- [deleted] in the title or body indicates author-initiated deletion.

- 🎯 [removed] in the title or body indicates moderator- or platform-initiated removal.

- Unchanged title and body indicate that the post remained available on the platform and was therefore treated as legitimate.

📥 
To begin the data repull from the posts that were collected in the daily data collection (i.e., Step 1), please refer to the code provided here: 

[Data Repull](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Data%20Repull.ipynb)

<p align="center">
  <b>📑 Metadata Collected in Steps 1 and 2 </b>
</p>

| Variable Name | Definition |
|--------------|------------|
| Subreddit | The name of the Reddit community where the post was published (e.g., r/reddit). It represents the topic or category of the post. |
| Post ID | A unique identifier assigned by Reddit to each post. It is used to distinguish and retrieve individual posts from the API or dataset. |
| Post Title | The headline of the Reddit post. It summarizes the main idea or topic of the post and is the first text users see. |
| Post Text | The main body content of the post. This is optional and may be empty if the post is a link-only or image-based submission. |
| Post Author | The Reddit username of the person who created the post. |
| Post Created | The timestamp indicating when the post was published on Reddit, usually stored in UTC format or Unix timestamp. |


[Data Collection - Post Repull](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Post%20Collection.ipynb)

[Data Collection - Rule Scraping](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Post%20Collection.ipynb)
