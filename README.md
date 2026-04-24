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
  <b>✍️  Prompt Template for GPT-4o & GPT 5 </b>
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
  <b>✍️  Prompt Template for GPT-4o Few-shot & GPT 5 Few-shot </b>
</p>
<div align="center">

<table>
  <tr>
    <th colspan="2">LLM Input</th>
  </tr>
  <tr>
    <th>Task Instruction</th>
    <td>
      Content moderation is a typical intervention strategy for regulating online communities on social media platforms, to ensure that social media content complies with the platforms' policies and community standards. Given a user's post, determine whether post should be moderated by answering 'Yes' or 'No'.
    </td>
  </tr>
  <tr>
    <th>Demonstrations</th>
    <td>
<pre>
Sample posts moderated under topic-based rules are shown below:


Rule: “Stay on Topic: Keep comments relevant to the subreddit and avoid off-topic posts.”
The following posts were moderated in accordance with the rule above:
(1) Remember ahead of the BYU vs. Notre Dame matchup that both the Mormon and Catholic Churches have a history of covering up child sex abuse amongst clergy and members.
(2) This sub’s moderation policy is atrocious and the mods should be ashamed. Just let us post. Please.
(3) Normalise free wifi in all gyms It’s not 2005.

Rule: “Be Polite and Respectful: Use respectful language and avoid personal attacks. Treat others with kindness and respect.”
The following posts were moderated in accordance with the rule above:
(1) As the title says - what the actual fuck, people?
(2) Awesome. For those that post demeaning things. You suck.
(3) Yet here we are with the most bullshit content filters imaginable.

Rule: “Spam and Self-Promotion: Prevent excessive advertisements, link dumping, or repetitive promotional content that disrupts community interactions.”
The following posts were moderated in accordance with the rule above:
(1) Usually it’s a place or a memorial for ex-F1-driver, like the most saddest public square I have ever seen (The Square of Mika Häkkinen https://fi.wikipedia.org/wiki/Mika_H%C3%A4kkisen_aukio)
(2) Here is a link to their page in Metalarchives:https://www.metal-archives.com/bands/Formula_1/77037https://www.metal-archives.com/bands/Formula_1/77037
(3) Inspo photos: https://www.thereformation.com/products/delphi-silk-dress/1310524IVO.html?glCountry=CA&amp;glCurrency=CAD&amp;lang=en_CA&amp;gclid=Cj0KCQjwpeaYBhDXARIsAEzItbHOkj-NYet-X9okRjPinbiA9AyQ5wJuJV5BxfvQDOvn6xYxrsJ4lugaAukqEALw_wcB (sadly way too pricy) https://www.joom.com/en/products/5fe553ca8392cf010626119b (like this style but won’t ship in time)

Rule: “Be Specific: Clearly state the topic or comment you're referring to. If you're commenting on someone's post, mention the exact post ID and comment number to reference it correctly.”
The following posts were moderated in accordance with the rule above:
(1) Instagram Caption translated by Google Translate: As salam alleykum! A very unusual situation is happening in Dagestan,
(2) I’m doing it! Halfway there! 5 + months ago I posted on here beginning my journey of weight loss.
(3) This sub seems so negative sometimes As most people here are on a weight loss journey, I'm sure there are many gripes and shared experiences that people like to vent about.

Rule: “Avoid Self-Plagiarism: Make sure your comments aren't copied from elsewhere. If you're unsure, check the rules before posting.”
The following posts were moderated in accordance with the rule above:
(1) If you need more information check out my last post.
(2) Flair Request Thread (PLEASE READ INSTRUCTIONS BEFORE COMMENTING)
(3) DE unwilling to change lich name with slur? So I'm a new streamer and was working on making content to help guide players through the early game. I had built a new account showing different ways of getting to the new war with just your starting frame free to play while solo.

Rule: “Personal Information and Privacy: Prohibit sharing personal information, doxing, or engaging in witch-hunts to protect user privacy.”
The following posts were moderated in accordance with the rule above:
(1) My name is Tong and I am grad student studying user experience and HCI.
(2) I’m a 5’5 heavier woman 26 years old.
(3) I know I have to eat good but having Mexican parents is a no.

Rule: “Avoid Overloading: Keep comments concise and on-topic. Avoid making multiple posts about the same idea.”
The following posts were moderated in accordance with the rule above:
(1) Self-damage is not the right solution Title. Even with the precautions that DE is considering, like multishot not doing self-damage and self-damage being related to distance, they will NEVER be able to account for all permutations of self-damage being detrimental and making for a worse experience.
(2) Need silly video recommendations! So I want to teach my girlfriend more about Yu-Gi-Oh but she hates info overload and will mentally check out if I show her something like that Lmao.
(3) I just want to join the world map and say “ hey guys how’s it going?” Or “hey I like that weapon how did you get it” or “can someone help with this quest” - it would make the game feel so much better.

Rule: “Avoid Misinformation: Don't share false information. If you're unsure, ask for clarification.”
The following posts were moderated in accordance with the rule above:
(1) using watches to move undeclared money across borders Recently I've heard how you can use an expensive watch to move &gt;$10k across borders without declaring it.
(2) How plausible is that OU and Texas will become the next Nebraska after their move to the SEC? I’ve been seeing a lot of articles lately of people saying that Texas and OU will have the same fate as Nebraska when they move conferences.
(3) I was just curious if anyone knows if there is a track walk time today. I had heard rumors that it would only be available to last years ticket holders but I would like to take my chances and see if I can’t get on there if possible.

Rule: “Political and Controversial Content: Limit discussions on sensitive topics such as politics, religion, or divisive social issues to maintain a neutral and inclusive space.”
The following posts were moderated in accordance with the rule above:
(1) Do you believe in god? I waver on it, but I want to believe there is a universal power that rewards good and punishes evil.
(2) I hope the UFC can figure out a pay structure to get these guys and girls more money, but as a fan there's no chance I want this turning into boxing with a Ali Act or the promotions not having control of the belts.
(3) Donations from Russia and Belarus Hello, we all probably know about the situation with the inability to buy anything from Russia and Belarus with real currency (specifically Tennogen, Prime Access and even a Tennocon ticket). I do not want to argue about the reasons for such an act or about the current political situation, I think everyone is aware of what is happening.

Rule: “Piracy and Illegal Content: Avoid discussions or links related to piracy, illegal downloads, or content that violates terms of service.”
The following posts were moderated in accordance with the rule above:
(1) Playing 1212 mod for pirated Attila? I want to know if I can download and play 1212 mod for pirated Attila.
(2) Anyways I uploaded it to a free online image host, so here's the link but it's not as cool if I could just post it here.
(3) This is an empty steam account with just Stardew Valley on it. Enjoy. First come first serve. login: structuralcattle4793. Password: 901ccdaebf69d2481!aZ.
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
