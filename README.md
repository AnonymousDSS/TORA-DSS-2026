# TORA-DSS-2026
This collection serves as an online repository for the TORA framework introduced in the Decision Support Systems paper [Ref], including the framework, metadata, data-collection code, and prompt templates used with large language models.

## Empirical Data Collection

### 🚨 Step 1: Daily Data Collection

#### Prerequisites

- Reddit Developer Access: Create a [Reddit developer account](https://developers.reddit.com/) to obtain the credentials required for API-based data collection. 
  
- Subreddit Selection: Identify a list of subreddits to be included in the data collection process.

📥 
To begin the daily data collection from selected subreddits, please refer to the code provided here: 
[Daily Data Collection](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Daily%20Data%20Collection.ipynb)

### 🚨 Step 2: Data Repull (Moderation Decision Verification)
To enhance ecological validity, a second round of data collection should be conducted after a suitable time interval to confirm the moderation status of previously collected posts. 

📥 
To begin the data repull from the posts that were collected in the daily data collection (i.e., Step 1), please refer to the code provided here: 
[Data Repull](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/Data%20Collection%20-%20Data%20Repull.ipynb)

<p align="center">
  <b>📑 Metadata </b>
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

<div align="left">
  
## 🔬TORA Framework

The TORA framework comprises four core components: post representation, rule representation, topic-based rule affinity measurement, and classification. Additional details on the framework architecture are provided in the Decision Support Systems paper [Ref]. 

⚙️ 
To begin model implementation, please refer to the code provided here: [TORA Framework](https://github.com/AnonymousDSS/TORA-DSS-2026/blob/main/TORA_Framework.ipynb)

## Others
<p align="center">
  <b>✍️ A Prompt Template for Topic Generation </b>
</p>
<div align="center">

<table>
  <tr>
    <th colspan="2">LLM Input</th>
  </tr>
  <tr>
    <th>Task Instruction</th>
    <td>
      Given a document containing a collection of community rules, identify the <strong><em>n</em></strong> most prominent topics. The topics should be concise, capturing the core subject matter of the text. Ensure that the topics are distinct from each other.
    </td>
  </tr>
  <tr>
    <th>Input Query</th>
    <td>
      Here is the document of rules: <strong><em>[Community rules]</em></strong>, please list ten most prominent topics for it. Answer:
    </td>
  </tr>
  <tr>
    <th>LLM Output</th>
    <td><strong><em>[A list of topics]</em></strong></td>
  </tr>
</table>




<p align="center">
  <b>✍️ A Prompt Template for GPT-4o & GPT 5 </b>
</p>
<div align="center">
<table>
  <tr>
    <th colspan="2">LLM Input</th>
  </tr>
  <tr>
    <th>Task Instruction</th>
    <td>
      Content moderation is a typical intervention strategy for regulating online communities on social media platforms, to ensure that social media content complies with the platforms' policies and community standards. Given a user's post and a list of rule topics: <strong><em>[A list of (rule) topics]</em></strong>, determine whether the post should be moderated by answering 'Yes' or 'No'.
    </td>
  </tr>
  <tr>
    <th>Input Query</th>
    <td>
      Should the following social media post be moderated? <strong><em>[A social media post]</em></strong> Answer:
    </td>
  </tr>
  <tr>
    <th>LLM Output</th>
    <td>
      <strong><em>'Yes' or 'No'</em></strong>
    </td>
  </tr>
</table>

<p align="center">
  <b>✍️ A Prompt Template for GPT-4o Few-shot & GPT 5 Few-shot </b>
</p>
<div align="center">

<table>
  <tr>
  <th colspan="2" align="left">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LLM Input</th>
  </tr>
  <tr>
    <th>Task Instruction</th>
    <td>
      Content moderation is a typical intervention strategy for regulating online communities on social media platforms, to ensure that social media content complies with the platforms' policies and community standards. Given a user's post, determine whether the post should be moderated by answering 'Yes' or 'No'.
    </td>
  </tr>
  <tr>
    <th>Demonstrations</th>
    <td>
<pre>
Sample posts moderated under topic-based rules are shown below:
<br>
Rule 1: “Rule Text”
The following posts were moderated in accordance with the rule above:
(1) Illegitimate Post Example 1.
(2) Illegitimate Post Example 2.
(3) Illegitimate Post Example 3.
<br>
Rule 2: “Rule Text”
The following posts were moderated in accordance with the rule above:
(1) Illegitimate Post Example 1.
(2) Illegitimate Post Example 2.
(3) Illegitimate Post Example 3.
<br>
.....

</pre>
    </td>
  </tr>
  <tr>
    <th>Input Query</th>
    <td>
      Should the following social media post be moderated? <strong><em>[A social media post]</em></strong> Answer:
    </td>
  </tr>
  <tr>
    <th>LLM Output</th>
    <td><strong><em>'Yes' or 'No'</em></strong></td>
  </tr>
</table>

<div align="left">
  
## Reference: 
TBD
