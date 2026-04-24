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

- [removed] in the title or body indicates moderator- or platform-initiated removal. 🎯

- Unchanged title and body indicate that the post remained available on the platform and was therefore treated as legitimate.

📥 
To begin the data repull from the posts that were collected in the daily data collection (i.e., Step 1), please refer to the code provided here: 
[Data Repull](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Data%20Repull.ipynb)

<p align="center">
  <b>📑 Metadata Collected in Steps 1 and 2 </b>
</p>
<div align="center">
  
| Variable Name | Definition |
|----------------------------|------------|
| `Subreddit` | The name of the Reddit community where the post was published (e.g., r/reddit). |
| `Post ID` | A unique identifier assigned by Reddit to each post. |
| `Post Title` | The headline of the Reddit post. |
| `Post Text` | The main body content of the post. |
| `Post Author` | The Reddit username of the creator. |
| `Post Created` | Timestamp of publication (UTC / Unix). ||

<div align="left">
  
### 🚨 Step 3: Community Rule Collection

Community rules differ across communities, domains, and platforms. In Reddit’s community-based governance structure, each subreddit defines its own rules and regulations to guide user behavior and content standards. Based on the subreddit selection specified in Prerequisites (Item 2), you can scrape the most current rules for each selected subreddit.

📥 
To begin the rule scraping, please refer to the code provided here: [Rule Scraping](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Rule%20Scraping.ipynb)

<p align="center">
  <b>📑 Metadata Collected in Step 3 </b>
</p>
<div align="center">
  
| Variable Name | Definition |
|--------------|------------|
| `Subreddit` | The name of a Reddit community (e.g., r/reddit). |
| `Subreddit Description` | Public description of the subreddit and its intended community focus. |
| `Rule Header` | Short title of the community rule. |
| `Rule Description` | Full textual description of the community rule. |
| `Time Created` | Timestamp of rule publication (UTC / Unix). |
| `Rule Violation Reason` | Standardized reason associated with rule violation. |

<div align="left">
  
## TORA Framework

The TORA framework comprises four core components: post representation, rule representation, topic-based rule affinity measurement, and classification. Additional details on the framework architecture are provided in the Decision Support Systems paper [Ref].

⚙️ 
To begin model implementation, please refer to the code provided here:


