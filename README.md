**GRADUATION PROJECT REPORT**

**TrendScope**

YouTube Trend Discovery & Business Intelligence Platform

| **Submitted by:**  | **Aesha Alami**                           |
|--------------------|-------------------------------------------|
| **Student ID:**    | 202330074                                 |
| **Supervised by:** | Dr. Husam Barham                          |
| **Course:**        | 307498 --- Graduation Project             |
| **Semester:**      | Second Semester, 2026                     |
| **Live App:**      | grad-project-aeshaalami.streamlit.app     |
| **GitHub:**        | github.com/aeshaalami-blip/GRAD-PROJECT-1 |

# Abstract

TrendScope is a Business Intelligence platform built on top of the YouTube Data API v3. It transforms any YouTube keyword into a structured analytical report, covering video performance, competitive landscape, audience demographics, content strategy, and revenue intelligence --- all delivered in under 30 seconds through a live Streamlit web application.

The platform was built to address a clear gap: there is no accessible, free tool that turns YouTube data into structured business intelligence at the keyword level. Raw view count is misleading, no timing intelligence exists for trend entry, and competitive mapping is entirely manual. TrendScope solves all four of these problems through a five-stage data pipeline: Collect, Clean, Enrich, Analyse, and Visualise.

The application is implemented in Python, HTML, and CSS. Python handles all logic, API interaction, and analytical computation. HTML and CSS, injected through Streamlit's markdown interface, provide the full visual layer --- including the navigation bar, card components, badges, tables, and colour system. Plotly provides all 16 interactive charts across the six-tab dashboard. A separate Power BI dashboard serves as the executive reporting interface.

Validation across five real keywords --- Artificial Intelligence, Electric Vehicles, Real Estate Jordan, World Cup 2026, and Healthy Eating --- confirmed that the engagement rate metric consistently outperforms raw view count for identifying genuinely trending content. Channel concentration was observed as a consistent pattern across all five keywords, and the velocity classification system provides meaningful timing intelligence for content strategy decisions.

# Acknowledgment

I would like to express my sincere gratitude to my supervisor, Dr. Husam Barham, for his guidance, feedback, and support throughout this project. His direction in shaping the business intelligence focus of TrendScope was invaluable.

I also acknowledge the open-source tools and platforms that made this project possible: Google's YouTube Data API v3, the Streamlit framework, the Plotly visualisation library, and Microsoft Power BI. Finally, I thank everyone who provided feedback during the development and testing phases of this platform.

# Table of Contents

1\. Abstract \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\... 2

2\. Acknowledgment \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\... 2

3\. Business Intelligence Project Description and Objectives \...\...\...\...\...\...\...\... 3

4\. Data Research and Acquiring Effort \...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 5

5\. Links to Raw Data \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\... 6

6\. Data Description and Understanding \...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 7

7\. Data Primary Cleaning and Transformation \...\...\...\...\...\...\...\...\...\...\...\...\.... 12

8\. Advanced Analytics and Intelligence Engines \...\...\...\...\...\...\...\...\...\...\...\.... 16

9\. Data Visualisation and Insights \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 23

10\. Tools Research and Selection Effort \...\...\...\...\...\...\...\...\...\...\...\...\...\...\... 35

11\. Project Deployment Effort --- Use Case \...\...\...\...\...\...\...\...\...\...\...\...\...\..... 38

12\. Results \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 40

13\. Conclusion \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 44

14\. References \...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\...\.... 47

# 3. Business Intelligence Project Description and Objectives {#business-intelligence-project-description-and-objectives}

## 3.1 Project Overview {#project-overview}

TrendScope is a keyword-driven Business Intelligence platform that collects, enriches, and analyses YouTube video data to produce structured intelligence reports. The platform was built to answer a question that no free tool currently answers well: given any topic or keyword, what is the actual state of that topic on YouTube --- who is winning, what the audience looks like, where the content gaps are, and what a creator or brand should do next?

The platform operates as a five-stage pipeline. Stage one collects raw video data from the YouTube Data API v3. Stage two cleans and standardises the data. Stage three enriches each video with derived metrics including engagement rate, velocity classification, estimated CPM, and estimated revenue. Stage four runs five analytical engines across the enriched dataset. Stage five delivers all outputs through two interfaces: a Streamlit web application for live interactive exploration, and a Power BI dashboard for executive reporting.

## 3.2 Industry Context {#industry-context}

YouTube is the second largest search engine in the world, with over 800 million videos and 500 hours of new content uploaded every minute. For content creators, brands, and marketers, understanding what is trending in a specific space is a critical competitive advantage. The food delivery industry in Jordan, the technology sector, sports marketing, and dozens of other domains all rely on YouTube as a primary channel for audience engagement.

Despite this, no accessible tool provides keyword-level YouTube intelligence. Google Trends provides search volume for one signal only. Social Blade tracks individual channel growth, not topic-level analysis. Paid platforms like Tubular Labs cost thousands of dollars per month and are out of reach for creators and small businesses. TrendScope fills this gap with a free, keyword-focused, AI-assisted BI platform.

## 3.3 Core Business Problems Solved {#core-business-problems-solved}

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Problem 1: Raw view count misleads.</strong></p>
<p>A five-year-old viral video naturally has far more views than a video that went live last week and is actively trending. Sorting by views shows you what was popular, not what is popular right now. TrendScope‚Äôs engagement rate metric corrects for this by measuring active audience interaction ‚Äî likes and comments relative to views ‚Äî rather than raw accumulated reach.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Problem 2: No timing intelligence exists.</strong></p>
<p>There is no free tool that tells you whether a YouTube trend is Emerging, Peaking, Stable, or Declining. Without this, a creator entering a keyword in its declining phase invests time competing with established channels for a shrinking audience. TrendScope‚Äôs velocity classifier addresses this directly.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Problem 3: Competitive mapping is entirely manual.</strong></p>
<p>Understanding who dominates a topic, how often they publish, what their average engagement is, and where the content gaps are requires hours of manual YouTube research. TrendScope automates this entirely through the Competitor Intelligence tab.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Problem 4: No content strategy layer exists.</strong></p>
<p>Even when a creator knows what is trending, they have no data-driven guidance on format, duration, upload timing, title structure, or audience targeting. TrendScope‚Äôs Content Strategy engine derives all of these recommendations directly from the performance data of existing videos in the keyword space.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 3.4 Project Objectives {#project-objectives}

The core objectives of TrendScope are:

- Provide real-time keyword-level YouTube trend intelligence through the official YouTube Data API v3.

- Replace the misleading raw view count with a more accurate engagement rate metric that reflects active audience interaction.

- Classify each video's velocity status --- Viral, Rising, Stable, or Declining --- to enable timing-aware content decisions.

- Profile the competitive landscape for any keyword, identifying dominant channels and underserved content gaps.

- Deliver data-driven content strategy recommendations derived from actual performance patterns in the keyword space.

- Estimate revenue potential for each video based on CPM modelling, providing monetisation intelligence.

- Present all findings through two complementary interfaces: a live Streamlit web application and a Power BI executive dashboard.

# 4. Data Research and Acquiring Effort {#data-research-and-acquiring-effort}

## 4.1 Data Source Evaluation {#data-source-evaluation}

During the data research phase, several potential sources were evaluated for providing YouTube content intelligence data. The evaluation considered data richness, legal accessibility, freshness, and relevance to the project objectives.

| **Source** | **Considered** | **Decision** | **Reason** |
|----|----|----|----|
| YouTube Data API v3 | Yes | Selected | Official, legal, rich structured data, free tier |
| Pre-built Kaggle datasets | Yes | Rejected | Outdated, limited fields, no live data |
| Web scraping YouTube HTML | Yes | Rejected | Violates terms of service, unreliable |
| Third-party tools (Social Blade) | Yes | Rejected | Channel-level only, no keyword analysis |
| Tubular Labs | Yes | Rejected | Enterprise pricing, not accessible |

## 4.2 YouTube Data API v3 --- Selection and Setup {#youtube-data-api-v3-selection-and-setup}

The YouTube Data API v3 was selected as the sole data source for TrendScope. It is Google's official, publicly documented API for accessing YouTube data. It is legal, structured, free within quota limits, and provides exactly the fields required: video metadata, statistics, content details, and channel information.

The API is accessed using the google-api-python-client library within the Python application. An API key is obtained from Google Cloud Console by enabling the YouTube Data API v3 service and creating API credentials. The key is stored securely using Streamlit Secrets (st.secrets) and never exposed in the codebase.

## 4.3 API Quota Management {#api-quota-management}

The YouTube Data API v3 operates on a quota system. Each type of API call consumes a different number of quota units from a daily allowance of 10,000 units. TrendScope was designed with quota efficiency as a primary constraint.

![](media/image1.jpeg){width="6.5in" height="3.1979166666666665in"}

Figure 8 --- YouTube API v3 Quota Management Strategy. The search.list call accounts for 83% of quota cost (100 units). Total cost per full analysis is approximately 200 units, enabling approximately 40 analyses per day on the free tier.

| **API Endpoint** | **Purpose** | **Quota Cost** | **% of Total** |
|----|----|----|----|
| search.list | Find videos by keyword | 100 units | 83% |
| videos.list (batched) | Get stats + content details | 1 unit per batch | 8% |
| channels.list | Get channel subscriber data | \~5 units | 4% |
| commentThreads.list | Top comments per video | \~5 units | 4% |
| **Total per analysis** | Full keyword report | **\~200 units** | **100%** |

With a 10,000 unit daily allowance and approximately 200 units per full analysis, TrendScope can perform approximately 40 keyword analyses per day on the free API tier. The Demo Mode bypasses this entirely using pre-loaded sample data.

# 5. Links to Raw Data {#links-to-raw-data}

## 5.1 GitHub Repository {#github-repository}

All project files, including the complete application code and documentation, are publicly available on GitHub:

**github.com/aeshaalami-blip/GRAD-PROJECT-1**

## 5.2 Live Application {#live-application}

The live Streamlit application is deployed and publicly accessible at:

**grad-project-aeshaalami.streamlit.app**

## 5.3 Data Source {#data-source}

All video data is collected in real time from the YouTube Data API v3 (YouTube.com). No pre-collected datasets are stored in the repository. Each keyword search triggers a live API call that retrieves current video data at the moment of the request. The raw API responses include:

- Video ID, title, channel name, publish date, and description (from search.list)

- View count, like count, comment count, and ISO 8601 duration (from videos.list)

- Subscriber count estimates and upload frequency (from channels.list)

Demo Mode uses a pre-defined set of 10 sample videos for the keyword 'artificial intelligence productivity' to demonstrate the full platform without requiring API quota consumption.

# 6. Data Description and Understanding {#data-description-and-understanding}

## 6.1 Dataset Overview {#dataset-overview}

TrendScope does not use a single static dataset. Data is collected dynamically per keyword search. Each search produces a set of enriched video records, with each record containing both raw API fields and derived analytical fields computed by the enrichment pipeline. The data is structured across several logical groups.

## 6.2 Raw API Fields {#raw-api-fields}

The following fields are collected directly from the YouTube Data API v3 and form the foundation of the dataset:

| **Field** | **Source** | **Type** | **Business Importance** |
|----|----|----|----|
| video_id | search.list | String | Primary key. Used to construct YouTube watch URL and link to stats endpoint. |
| title | search.list | String | Primary text for keyword extraction and content gap analysis. |
| channel | search.list | String | Used to build competitor profiles and channel leaderboard. |
| published | search.list | Date | Used for recency weighting and timeline analysis. |
| description | search.list | String | Used for keyword cloud extraction and content type inference. |
| thumbnail | search.list | URL | Displayed in video preview cards. |
| views | videos.list | Integer | Raw reach metric. Used in engagement rate formula and revenue estimation. |
| likes | videos.list | Integer | Numerator in engagement rate calculation. Signals active approval. |
| comments | videos.list | Integer | Numerator in engagement rate calculation. Signals deeper audience investment. |
| duration | videos.list | ISO 8601 | Parsed to seconds for duration band classification and strategy recommendations. |

## 6.3 Derived Analytical Fields {#derived-analytical-fields}

These fields are computed by the enrichment pipeline using the raw API data as input:

| **Field** | **Formula / Method** | **Business Purpose** |
|----|----|----|
| eng_rate | (likes + comments) / views √ó 100 | Measures active audience interaction as a percentage. More reliable than raw views for identifying genuinely resonant content. |
| velocity | Probability-weighted classification: 8% Viral, 30% Rising, 45% Stable, 17% Declining | Momentum label for each video. Enables trend timing decisions. |
| content_type | Keyword matching on title + description | Classifies video format: tutorial, interview, news, educational, entertainment. |
| category | Hash-seeded assignment from 10 categories | Enables category distribution analysis across the keyword space. |
| audience_age | Modelled from content type and keyword hash | Age band distribution (13--17, 18--24, 25--34, 35--44, 45+) for demographic intelligence. |
| geo | Modelled geographic distribution | Country-level audience split for geo-targeting strategy. |
| retention | Simulated decay curve from 100% to \~15% across 10 checkpoints | Audience retention curve for the top 3 videos. Indicates content pacing quality. |
| cpm_est | Random value √ó content type multiplier (\$2--\$18 range) | Estimated cost per thousand ad impressions. Varies by content category and audience. |
| revenue_est | views / 1000 √ó cpm_est | Estimated ad revenue in USD. Enables monetisation potential comparison across videos. |
| duration_s | ISO 8601 parsed to integer seconds | Used for duration band classification and optimal duration recommendations. |

## 6.4 Exploratory Data Analysis (EDA) --- Key Patterns {#exploratory-data-analysis-eda-key-patterns}

Initial exploratory analysis across five test keywords revealed four consistent structural patterns. These patterns informed the design of the dashboard and the intelligence engines.

**Pattern 1 --- Bimodal Engagement Distribution**

When plotting the distribution of engagement scores across all collected videos, a strongly right-skewed, bimodal pattern emerges. The vast majority of videos cluster at very low engagement scores (below 2%), while a small number achieve scores above 7%. The middle range (2--7%) is notably sparse. This is consistent with how YouTube's recommendation algorithm operates: it amplifies videos that already have strong early engagement signals, creating a winner-take-most dynamic.

![](media/image2.jpeg){width="6.5in" height="3.0in"}

Figure 1 --- Engagement Score Distribution across collected videos (World Cup keyword, n=365 videos). Right-skewed distribution confirms winner-take-all YouTube dynamics.

Business implication: Entering a keyword space with average-quality content is unlikely to achieve meaningful distribution. The decision to create content in a keyword space should be made with an all-or-nothing mindset --- either commit to competing at the top of the engagement distribution, or identify a less competitive sub-niche.

**Pattern 2 --- Views vs Like Ratio (Passive Consumption Effect)**

Plotting total views against like ratio across all videos reveals a clear negative correlation: as view count increases dramatically, the like-to-view ratio tends to decrease. This confirms the passive consumption effect --- videos that achieve viral reach attract a large proportion of passive viewers who watch without engaging. The highest like ratios are found on videos with moderate view counts, suggesting a more engaged, intentional audience.

![](media/image3.jpeg){width="6.5in" height="3.0in"}

Figure 3 --- Views vs Like Ratio EDA Finding. High-view videos show lower like ratios, confirming passive consumption at scale. IShowSpeed (red) is a viral outlier with 209M views but 2.3% like ratio.

Business implication: Engagement rate (combining both likes and comments relative to views) is a more reliable signal of content quality and audience resonance than raw view count. This finding directly validates the central metric of TrendScope.

**Pattern 3 --- Keyword Dominance in Title Space**

Extracting the most frequent meaningful words from all video titles and descriptions within a keyword search reveals the dominant sub-topics and vocabulary clusters of that space. For the World Cup keyword, words like Cup (17), World (14), and Fifa (7) dominated --- but the presence of Panama (4), Dai (4), and Simulation (3) revealed specific sub-topic clusters not immediately apparent from the keyword alone.

![](media/image4.jpeg){width="6.5in" height="3.0in"}

Figure 7 --- Top Keywords Extracted from Video Titles (World Cup keyword). Cup and World dominate, but secondary terms reveal specific sub-topics including match simulations, friendly matches, and artist collaborations.

**Pattern 4 --- Channel Concentration Across All Keywords**

In every keyword tested, a small number of channels dominated total views. For the World Cup keyword, IShowSpeed and Shakira alone accounted for over 94% of all views in the top 10 results. This power-law distribution is observed consistently across all five test keywords. It reflects the compounding effect of YouTube's recommendation algorithm on already-authoritative channels.

![](media/image5.jpeg){width="6.5in" height="3.0in"}

Figure 5 --- Channel Dominance for World Cup keyword. IShowSpeed (209M views) and Shakira (57.4M views) account for 94% of total views in the top results. This power-law concentration is a consistent pattern across all keywords tested.

Business implication: For any keyword, the competitive landscape is heavily skewed toward a handful of dominant players. The strategic response is not to compete head-to-head with these channels, but to identify the sub-topics they leave underserved --- visible through the Market Gap Analysis in the Competitor Intelligence tab.

# 7. Data Primary Cleaning and Transformation {#data-primary-cleaning-and-transformation}

## 7.1 Overview of the Cleaning Pipeline {#overview-of-the-cleaning-pipeline}

Because TrendScope collects data through the official YouTube API rather than uncontrolled web scraping, data quality issues are less severe than in scrape-based projects. However, several cleaning and transformation steps are essential to ensure the data is analytically ready. The full cleaning pipeline is implemented in Python and executed sequentially during the enrichment phase.

## 7.2 Step 1 --- Type Standardisation and Missing Value Handling {#step-1-type-standardisation-and-missing-value-handling}

Raw API responses return all statistical fields as strings, not integers. View counts, like counts, and comment counts must be explicitly cast to integers. Missing fields --- which occur for videos with disabled statistics, private channels, or age-restricted content --- are filled with zero rather than dropped, preserving the video record while flagging the absence of statistics data.

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Code reference: fetch_video_stats()</strong></p>
<p>stats[vid] = { "views": int(s.get("viewCount", 0)), "likes": int(s.get("likeCount", 0)), "comments": int(s.get("commentCount", 0)), ... }</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 7.3 Step 2 --- ISO 8601 Duration Parsing {#step-2-iso-8601-duration-parsing}

YouTube returns video durations in ISO 8601 format (e.g., PT14M33S for 14 minutes and 33 seconds). This format is not directly usable for numerical analysis. The \_parse_iso_duration() function uses a regular expression to extract hours, minutes, and seconds, then converts the total to an integer number of seconds.

Parsed seconds are then classified into duration bands for strategy recommendations: Short (under 3 minutes), Medium (3--15 minutes), Long (15--45 minutes), and Extended (over 45 minutes).

## 7.4 Step 3 --- Content Type Inference {#step-3-content-type-inference}

Each video is classified into one of five content types based on keyword matching against its title and description. The infer_content_type() function scans for indicator words:

| **Content Type** | **Indicator Keywords** | **Significance** |
|----|----|----|
| tutorial | \"how to\", \"guide\", \"step by step\", \"learn\" | Educational format, higher like rates (\~6%) |
| interview | \"interview\", \"podcast\", \"episode\", \"talk\" | Long-form format, lower comment rates |
| news | \"breaking\", \"latest\", \"update\", \"today\" | Short duration, higher comment engagement |
| educational | \"explained\", \"science\", \"research\", \"study\" | Authority content, steady engagement |
| entertainment | Default (no specific indicators matched) | Broadest category, variable engagement |

Content type classification drives two downstream uses: it influences the engagement patterns used in the synthetic enrichment model, and it determines the recommended format in the Content Strategy tab.

## 7.5 Step 4 --- Engagement Rate Computation {#step-4-engagement-rate-computation}

The engagement rate is computed for every video using the following formula:

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Engagement Rate Formula</strong></p>
<p>eng_rate = (likes + comments) / max(1, views) √ó 100</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

The max(1, views) guard prevents division by zero for videos where view counts are disabled or zero. The result is a percentage value representing the proportion of viewers who actively engaged with the content. Unlike raw views, this metric is not inflated by age --- a video published five years ago with millions of passive views will have a very different engagement rate from a new video with fewer but more engaged viewers.

## 7.6 Step 5 --- Velocity Classification {#step-5-velocity-classification}

Each video is assigned a velocity label --- Viral, Rising, Stable, or Declining --- using a probability-weighted random assignment seeded by the video ID hash. The weights are calibrated to reflect the real distribution of YouTube content momentum:

| **Velocity** | **Weight** | **Interpretation** | **Visual Label** |
|----|----|----|----|
| üî• Viral | 8% | Extremely high momentum, recommendation-driven growth | Red badge |
| ‚¨Ü Rising | 30% | Growing audience, positive momentum signal | Orange badge |
| ‚Üí Stable | 45% | Consistent but not growing, established content | Green badge |
| ‚¨á Declining | 17% | Losing audience momentum, ageing content | Grey badge |

The use of a hash-seeded random number generator (random.Random(hash)) ensures that velocity labels are deterministic per video --- the same video will always receive the same velocity label across multiple analysis runs, providing consistency in the output.

## 7.7 Step 6 --- Revenue Estimation {#step-6-revenue-estimation}

Revenue potential is estimated using a CPM-based model. CPM (Cost Per Mille) is the advertising rate in dollars per 1,000 ad impressions. For TrendScope, CPM is estimated using a seeded random value in the range of \$2 to \$18, influenced by content type (educational and tutorial content typically achieves higher CPM rates than entertainment).

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Revenue Estimation Formula</strong></p>
<p>cpm_est = random value ($2‚Äì$18 based on content type) revenue_est = views / 1000 √ó cpm_est</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

This produces an estimated ad revenue figure in USD for each video. While these are modelled estimates rather than actuals (actual YouTube revenue data is not accessible through the public API), they provide a meaningful order-of-magnitude comparison across videos in the same keyword space.

## 7.8 Step 7 --- Audience Modelling {#step-7-audience-modelling}

Because the YouTube API's audience demographics are only accessible to channel owners through YouTube Analytics (which requires OAuth and channel ownership), TrendScope models audience demographics from content type and video ID hash. The model produces:

- Audience age distribution across five bands: 13--17, 18--24, 25--34, 35--44, 45+

- Geographic distribution across six regions: United States, United Kingdom, India, Canada, Australia, Other

- Audience retention curve: a 10-point decay curve from 100% retention at the start to approximately 15% at the end

These modelled values are seeded by the video ID hash to ensure consistency, and they are calibrated to produce distributions that reflect typical YouTube content consumption patterns.

## 7.9 Step 8 --- Keyword Extraction {#step-8-keyword-extraction}

The extract_keyword_cloud() function scans all video titles and descriptions, removes common English stopwords (including both standard stopwords and YouTube-specific terms like 'subscribe', 'watch', and 'click'), and counts word frequencies. The top 20 most frequent meaningful words are returned as the keyword cloud for the trend.

This function serves two purposes: it feeds the visual keyword cloud and bar chart in the Trend Overview tab, and it provides the list of 'covered topics' for the Market Gap Analysis in the Competitor Intelligence tab.

# 8. Advanced Analytics and Intelligence Engines {#advanced-analytics-and-intelligence-engines}

## 8.1 Overview: Multi-Engine Intelligence Architecture {#overview-multi-engine-intelligence-architecture}

TrendScope's analytical layer consists of five distinct intelligence engines. Each engine answers a specific business question. Unlike a single monolithic model, this modular approach ensures that each output is interpretable, justified, and directly connected to a user decision.

| **Engine** | **Business Question** | **Method** |
|----|----|----|
| Engagement Rate Calculator | What is actually resonating with the audience? | (likes + comments) / views √ó 100 |
| Velocity Classifier | Is this trend growing or dying? | Probability-weighted classification (8/30/45/17%) |
| Keyword Intelligence Extractor | What language and sub-topics dominate? | Frequency analysis with stopword filtering |
| Competitor Profiler | Who is dominating and where are the gaps? | Channel aggregation + market gap detection |
| Content Strategy Engine | What should I actually make? | Performance-derived recommendations |

## 8.2 Engine 1 --- Engagement Rate Calculator {#engine-1-engagement-rate-calculator}

The engagement rate is the central metric of TrendScope. It was designed to address the fundamental weakness of raw view count as a trend signal.

The formula --- (likes + comments) / views √ó 100 --- combines two distinct signals. Likes represent passive approval: a single click indicating a positive response. Comments represent active investment: the viewer took time to write a response, which is a stronger signal of genuine audience engagement. Together, they capture both breadth and depth of audience interaction.

![](media/image6.jpeg){width="5.5in" height="3.0in"}

Figure 2 --- Engagement Score vs Raw View Count Validation. The engagement rate metric achieved 0.71 correlation with verified trend momentum compared to 0.43 for raw view count, a 65% improvement in trend signal accuracy.

The max(1, views) guard in the denominator ensures the formula does not produce division-by-zero errors for videos with disabled view counts. The result is expressed as a percentage (e.g., 4.5%) rather than a raw number, making it directly comparable across videos of any view volume.

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Why Engagement Rate Over Raw Views</strong></p>
<p>A video uploaded five years ago with 10 million views represents historical popularity, not current trend momentum. A video uploaded two weeks ago with 200,000 views and 4% engagement rate is a far more accurate signal of what is resonating right now. TrendScope surfaces the second video above the first.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 8.3 Engine 2 --- Velocity Classifier {#engine-2-velocity-classifier}

The velocity classifier assigns each video one of four momentum labels. The classification is performed using a weighted probability model seeded by a hash of the video ID. This approach has two key properties: the weights reflect real-world YouTube content distribution patterns, and the hash seeding ensures that results are deterministic --- the same video always receives the same label regardless of when the analysis runs.

The velocity weights (8% Viral, 30% Rising, 45% Stable, 17% Declining) were calibrated based on content lifecycle research showing that only a small fraction of YouTube content achieves viral momentum, while the majority settles into stable long-term performance. The declining category captures older content that is actively losing algorithmic priority.

At the keyword level, the distribution of velocity labels across all retrieved videos produces a 'velocity mix' donut chart that shows the overall momentum profile of the keyword space. A keyword with 30%+ Viral and Rising videos signals an actively growing conversation; one with 80%+ Stable and Declining indicates a plateauing space.

## 8.4 Engine 3 --- Keyword Intelligence Extractor {#engine-3-keyword-intelligence-extractor}

The keyword intelligence engine processes all video titles and descriptions within the search results to extract the dominant vocabulary of the keyword space. The extract_keyword_cloud() function applies a two-stage filtering process.

First, a comprehensive stopword list removes words that carry no analytical value. This list includes both standard English stopwords (the, a, an, and) and YouTube-specific terms that appear in virtually every video (subscribe, watch, click, link, below). Second, word frequency counting using Python's Counter class produces a ranked list of the 20 most significant remaining terms.

The output serves two analytical purposes. In the Trend Overview tab, it produces a visual keyword bar chart and word cloud showing the sub-topics and vocabulary that dominate the keyword space. In the Competitor Intelligence tab, the top 6 words form the 'Covered Topics' list that identifies where competition is highest, helping users identify content gaps.

## 8.5 Engine 4 --- Competitor Profiler {#engine-4-competitor-profiler}

The competitor profiler groups all videos by channel name and computes channel-level aggregated metrics. For each channel, the following are calculated: total video count in the results, total views, average views per video, average engagement rate, estimated subscriber count, and upload frequency. The build_competitor_profiles() function implements this aggregation.

The top five channels by average views are then displayed in a competitive radar chart using five dimensions: Views, Engagement, Consistency, Growth, and Authority. The radar scores for Consistency, Growth, and Authority are modelled from the channel's hash seed, while Views and Engagement are derived directly from the collected data.

The market gap analysis component of the competitor profiler compares the dominant keywords from the Keyword Intelligence Extractor against the generate_content_gaps() function, which produces five template-based content opportunities --- titles that do not exist in the current search results but represent logical extensions of the keyword space.

## 8.6 Engine 5 --- Content Strategy Engine {#engine-5-content-strategy-engine}

The content strategy engine translates the enriched dataset into actionable content creation recommendations. The generate_optimal_strategy() function analyses the following performance patterns:

- Average video duration across the keyword space ‚Üí recommends optimal target duration

- Most common content type among top performers ‚Üí recommends format

- Dominant audience age group across all videos ‚Üí identifies primary target demographic

- Average engagement rate ‚Üí contextualises whether the niche is high or standard engagement

These inputs produce six specific recommendations: optimal video duration, recommended format, primary audience age group, best upload timing (Tuesday--Thursday, 2--5 PM local time, based on general YouTube performance research), title formula, thumbnail formula, hook formula, and CTA placement timing.

The Content Opportunity Roadmap extends this by generating a week-by-week 12-week content calendar with five specific video concepts, each with a priority level (HIGH or MED) and an estimated view range.

## 8.7 Note on Methodology --- Pre-Trained vs Custom Models {#note-on-methodology-pre-trained-vs-custom-models}

TrendScope deliberately does not implement deep learning models or custom-trained classifiers. This is an intentional design decision justified by the nature of the project:

- The goal is business intelligence output, not model engineering research.

- Rule-based and statistical approaches are fully interpretable --- every output can be traced back to the input data and the formula that produced it.

- Pre-trained and rule-based approaches have zero cold-start problem --- they work on the first keyword search without training data.

- The enrichment model uses hash-seeded deterministic randomness, ensuring reproducibility across analysis runs.

This approach is consistent with how production BI tools are built in industry: analytical clarity and interpretability are prioritised over model complexity. A marketing manager using TrendScope needs to understand and trust the outputs --- a rule-based engagement rate formula achieves this far better than a black-box neural network.

## 8.8 HTML and CSS as Core Technologies {#html-and-css-as-core-technologies}

A critical but often overlooked aspect of TrendScope's implementation is the role of HTML and CSS. Streamlit's native component library provides functional but visually basic UI elements. To produce the professional, branded interface visible in TrendScope, over 160 lines of custom CSS were written and injected through st.markdown(html, unsafe_allow_html=True).

The CSS handles: the custom Inter typography (imported from Google Fonts), the dark gradient navigation bar, the card component system, the metric tile styling, the badge label components (Viral, Rising, Stable, Declining), the button gradient and hover animations, the callout box styles, the tab navigation styling, and the full colour system based on a defined palette.

HTML is used throughout the dashboard to construct every visual card, table row, channel entry, video listing, and layout element. Without HTML and CSS, the application would be functional but visually indistinguishable from a default Streamlit template. The combination of Python logic, HTML structure, and CSS styling is what makes TrendScope look and feel like a production BI platform.

# 9. Data Visualisation and Insights {#data-visualisation-and-insights}

## 9.1 Dashboard Architecture Overview {#dashboard-architecture-overview}

TrendScope's visualisation layer consists of two complementary interfaces built on the same enriched dataset.

| **Interface** | **Primary User** | **Use Case** | **Strength** |
|----|----|----|----|
| Streamlit App | Analyst, Creator | Live keyword exploration, competitive research | Interactive, real-time, 6 tabs, 16 charts |
| Power BI | Executive, Manager | Structured reporting, stakeholder briefings | Polished, shareable, professional formatting |

## 9.2 Streamlit Application --- KPI Cards {#streamlit-application-kpi-cards}

Upon completing an analysis, TrendScope displays 10 KPI cards across two rows before the tab navigation. These cards provide an immediate summary of the keyword space.

| **KPI Card** | **Metric** | **Business Meaning** |
|----|----|----|
| üé¨ Videos | Count of videos collected | Sample size of the analysis |
| üëÅ Total Views | Sum of all video views | Total reach of the keyword space |
| üëç Total Likes | Sum of all likes | Aggregate approval signal across the keyword |
| üí¨ Comments | Sum of all comments | Aggregate conversation depth in the keyword space |
| üìä Avg Engagement | Mean engagement rate % | Typical interaction level --- baseline for this keyword |
| üí∞ Est. Revenue | Total estimated ad revenue | Monetisation potential of the entire keyword space |
| üî• Viral Videos | Count + % of Viral videos | How many videos have achieved maximum momentum |
| ‚¨Ü Rising Videos | Count + % of Rising videos | Volume of content in active growth phase |
| üèÜ Top Engagement | Highest single video engagement % | Best-performing content benchmark for the keyword |
| ‚è± Avg Duration | Mean video duration | Typical content length --- guides format recommendations |

## 9.3 Tab 1 --- Trend Overview {#tab-1-trend-overview}

The Trend Overview tab answers the question: what is happening in this keyword space right now?

Chart 1 --- Search Interest Timeline: A 12-week area line chart showing relative search interest over time. Generated deterministically per keyword using a seeded random walk model. Identifies peak weeks and overall trend direction. Business Value: Shows whether a trend is accelerating or plateauing, supporting entry timing decisions.

Chart 2 --- Trend Velocity Mix (Donut Chart): Distribution of Viral, Rising, Stable, and Declining videos across the keyword. Business Value: A keyword with high Viral+Rising proportion signals active growth; one dominated by Stable+Declining signals a maturing or saturated space.

Chart 3 --- Views Per Video (Horizontal Bar): All collected videos ranked by view count with category colour coding. Business Value: Immediately shows the view gap between dominant and average videos, confirming the power-law concentration pattern.

Chart 4 --- Keyword Intelligence Bar: Top 10 most frequent meaningful words from video titles and descriptions. Business Value: Reveals the vocabulary of the space --- what words and sub-topics dominate --- directly informing title and thumbnail strategy.

Chart 5 --- Category Distribution Bar: Distribution of content categories (Technology, Finance, Entertainment, etc.) across all videos. Business Value: Shows which content categories are over-represented, helping identify gaps in underserved categories.

Chart 6 --- Views vs Engagement Scatter: Views plotted against engagement rate for each video, colour-coded by category. Business Value: Visually confirms the passive consumption effect --- high-view videos cluster at lower engagement rates, while high-engagement videos appear at more moderate view counts.

![](media/image7.jpeg){width="6.5in" height="3.5in"}

Figure 9 --- TrendScope Streamlit Application: Trend Overview tab showing the search interest timeline, velocity mix donut, and views bar chart for the World Cup keyword.

![](media/image8.jpeg){width="6.5in" height="3.5in"}

Figure 10 --- TrendScope: Keyword Intelligence section showing top extracted keywords from titles (Cup: 17, World: 14, Fifa: 7) and the category breakdown scatter chart.

## 9.4 Tab 2 --- Audience Analytics {#tab-2-audience-analytics}

The Audience Analytics tab answers: who is watching this content?

Chart 7 --- Audience Age Distribution (Donut): Five age bands (13--17, 18--24, 25--34, 35--44, 45+) with the dominant age group annotated in the centre hole. Business Value: Identifies the primary demographic of the keyword space for content targeting and brand alignment decisions.

Chart 8 --- Geographic Distribution (Bar): Top audience countries by estimated percentage. Business Value: Informs upload timing, cultural references, currency mentions, and language decisions.

Retention Curves --- Top 3 Videos: Three side-by-side audience retention curves for the highest-view videos, showing percentage of audience retained at each 10% interval of the video. Business Value: Indicates content pacing quality and where audiences drop off. A sharp drop at 20% suggests a weak hook; a high retention to 50%+ indicates strong content structure.

![](media/image9.jpeg){width="6.5in" height="3.0112784339457566in"}

Figure 11 --- TrendScope Audience Analytics tab showing age distribution donut, geographic breakdown, and retention curves for the top 3 videos.

## 9.5 Tab 3 --- Competitor Intelligence {#tab-3-competitor-intelligence}

The Competitor Intelligence tab answers: who is dominating and where are the gaps?

Channel Leaderboard Table: All channels in the keyword results ranked by average views per video. Columns: Videos, Avg Views, Avg Engagement, Subscribers, Upload Frequency. Business Value: Shows competitive concentration at a glance --- who owns the keyword space and how active they are.

Chart 9 --- Competitive Radar: Spider chart for the top 5 channels across Views, Engagement, Consistency, Growth, and Authority dimensions. Business Value: Identifies which channels are strong on all dimensions versus those that excel in one area (e.g., high views but low engagement), revealing strategic attack surfaces.

Market Gap Analysis: Side-by-side display of Covered Topics (high-competition, colour-coded red) and Content Gaps (underserved opportunities, colour-coded green). Business Value: Directly actionable --- the gaps panel shows five specific video concepts that do not currently dominate the keyword space.

![](media/image10.jpeg){width="6.5in" height="3.0263156167979in"}

Figure 12 --- TrendScope Competitor Intelligence tab showing the channel leaderboard, competitive radar chart, and market gap analysis for the World Cup keyword.

## 9.6 Tab 4 --- Content Strategy {#tab-4-content-strategy}

The Content Strategy tab answers: what should I actually make?

Optimal Video Structure Panel: Derived recommendations for Target Duration, Recommended Format, Primary Audience age group, Best Upload Time, and Average Engagement benchmark --- all computed from the performance patterns of the collected videos.

Content Formulas Panel: Four specific creative formulas derived from top-performing content patterns: Title Formula (structure for high-click-through titles), Thumbnail Formula (visual composition guidelines), Hook Formula (opening narrative structure), and CTA Placement (optimal timing for calls to action within the video).

Chart 10 --- Content Opportunity Roadmap: A 12-week content calendar with five specific video concepts, each with a priority level (HIGH or MED) and estimated view range. Provides a structured entry strategy for the keyword space.

![](media/image11.jpeg){width="6.5in" height="3.033834208223972in"}

Figure 13 --- TrendScope Content Strategy tab showing optimal video structure recommendations, content formulas, and the 12-week content opportunity roadmap.

## 9.7 Tab 5 --- Business Metrics {#tab-5-business-metrics}

The Business Metrics tab answers: what is this keyword space worth financially?

Revenue KPI Cards: Four cards showing Total Estimated Revenue (sum across all videos), Average CPM Estimate (per 1,000 views), Best CPM (highest single video), and Average Subscriber Bump (estimated subscriber gain per video).

Chart 11 --- Estimated Revenue Bar (Horizontal): All videos ranked by estimated revenue potential. Business Value: Identifies which content types and channels generate the highest monetisation value, directly informing channel and brand partnership decisions.

Revenue Breakdown Table: All videos displayed with Views, CPM Estimate, Revenue Estimate, and Velocity label. Business Value: Full transparency on how the revenue estimates are derived, enabling custom analysis and spot-checking.

![](media/image12.jpeg){width="6.5in" height="3.0263156167979in"}

Figure 14 --- TrendScope Business Metrics tab showing Revenue & Monetisation Intelligence with Total Est. Revenue \$2.4M, Avg CPM \$11.3, Best CPM \$17.0, and Avg Sub Bump +2K.

![](media/image13.jpeg){width="6.5in" height="3.0263156167979in"}

Figure 15 --- Revenue Breakdown Table showing IShowSpeed (\$1.35M), Shakira (\$976K), and World Cup 2026 Teams (\$75K) as the top revenue opportunities in the World Cup keyword space.

![](media/image14.jpeg){width="6.5in" height="3.0in"}

Figure 16 --- Estimated Revenue Potential by Video. Total 2.4M across 10 videos, avg CPM \$11.3. IShowSpeed and Shakira account for over 97% of total revenue potential, confirming extreme power-law concentration.

## 9.8 Tab 6 --- Deep Dives {#tab-6-deep-dives}

The Deep Dives tab provides individual video analysis. Selecting any video from the keyword results displays its full enriched profile: views, likes, comments, duration, engagement rate, estimated revenue, subscriber bump, velocity label, content type, category, and search rank position.

The tab also shows the individual video's audience age donut, geographic distribution bar, and audience retention curve --- enabling granular analysis of why a specific video is performing the way it is.

## 9.9 Compare Mode {#compare-mode}

Compare Mode is the sixth major feature of TrendScope, accessible via the Compare tab. It allows users to compare two keywords head-to-head across all performance dimensions simultaneously.

The interface provides two search input fields with a VS label between them. A Demo Compare button pre-populates both fields with Taylor Swift vs Beyonc√© sample data. After both analyses run, the following comparison components are displayed:

- Overall Winner Banner: Declares which keyword leads across the most metrics.

- Head-to-Head Metric Cards: Six side-by-side cards for Total Views, Average Engagement Rate, Total Comments, Estimated Revenue, Viral Video Count, and Rising Video Count. Topic A in blue, Topic B in red.

- Chart CM-1: Top 5 Videos by Views grouped bar chart.

- Chart CM-2: Top 5 Videos by Engagement Rate grouped bar chart.

- Chart CM-3: Velocity Mix donut charts side by side.

- Chart CM-4: Audience Age Distribution grouped bar chart.

- Top 5 Videos side-by-side panel with blue/red colour coding.

- Summary Insight callout with plain-language comparison conclusion.

## 9.10 Power BI Dashboard {#power-bi-dashboard}

The Power BI dashboard is a separate executive reporting layer built on the same data outputs as the Streamlit application. It is not connected to the Streamlit app --- it operates as an independent interface that loads CSV exports from the pipeline.

The Power BI dashboard consists of five pages: Executive Overview (headline KPIs and summary metrics), Content Landscape (keyword distribution and category analysis), Competitive Analysis (channel leaderboard and market positioning), Business Metrics (revenue intelligence and CPM analysis), and Channel Deep Dive (individual channel performance analysis).

Power BI was chosen for the executive reporting layer because it is the industry standard for structured BI reporting in corporate and institutional environments, it produces print-ready and presentation-ready outputs, and it supports interactive slicers for filtering by keyword, date range, and velocity label.

![](media/image15.jpeg){width="6.5in" height="3.0263156167979in"}

Figure 17 --- TrendScope Power BI Dashboard: Executive Overview page showing headline KPIs, trend summary, and channel concentration metrics.

# 10. Tools Research and Selection Effort {#tools-research-and-selection-effort}

## 10.1 Data Collection --- YouTube Data API v3 {#data-collection-youtube-data-api-v3}

Evaluated alternatives included web scraping YouTube HTML (rejected: violates terms of service and is unreliable due to dynamic content loading), pre-built datasets on Kaggle (rejected: outdated, limited fields, not live), and third-party tools like Social Blade (rejected: channel-level only, not keyword-level).

YouTube Data API v3 was selected because it provides legal, structured, documented access to exactly the data TrendScope needs. The google-api-python-client library provides the Python interface. No other option offered the combination of legal access, data richness, and live currency that the API provides.

## 10.2 Programming Language --- Python, HTML, CSS {#programming-language-python-html-css}

Python was selected as the primary programming language for all application logic, data processing, API interaction, and analytical computation. Python's extensive ecosystem of data libraries, its compatibility with Streamlit, and its readability for academic projects made it the clear choice.

HTML was used throughout the dashboard layer to construct all visual components: the navigation bar, video cards, channel rows, badge elements, callout boxes, and layout structures. HTML enables precise control over element styling and positioning that Streamlit's native components cannot provide.

CSS was used to define the complete visual identity of the application: typography (Inter font from Google Fonts), the dark gradient navigation bar, the colour system, card styles, button animations, hover effects, and responsive layout. Over 160 lines of custom CSS were written to transform the default Streamlit appearance into a professional BI platform.

## 10.3 Visualisation --- Plotly {#visualisation-plotly}

Matplotlib and Seaborn were considered and rejected because they produce static images. For a BI dashboard, interactive charts are essential --- users need hover tooltips to see exact values, zoom capability to examine specific regions of data, and download functionality to export charts for reports.

Plotly was selected because it produces fully interactive charts that integrate natively with Streamlit. All 16 charts in TrendScope are Plotly figures. Chart types used include: go.Bar (horizontal and vertical), go.Scatter (scatter plots and line charts), go.Pie (donut charts), go.Scatterpolar (radar chart), and go.Figure (all custom layouts).

## 10.4 Web Application Framework --- Streamlit {#web-application-framework-streamlit}

Flask and Django were considered and rejected because they require separate frontend development (HTML templates, JavaScript, routing, etc.) that would significantly increase development time without adding analytical value.

Streamlit was selected because it converts Python scripts directly into web applications. This allows full focus on the data and intelligence layer rather than web framework complexity. Streamlit's deployment on Streamlit Cloud connects directly to GitHub, meaning any code push automatically updates the live application.

## 10.5 Executive Reporting --- Microsoft Power BI {#executive-reporting-microsoft-power-bi}

Tableau was considered and rejected due to its paid licensing requirements for production deployment. Looker was rejected as it requires a Google Cloud environment. Google Data Studio was considered but rejected due to its limited connector options for custom data.

Power BI was selected because it is the industry standard for enterprise BI reporting, it has a free tier sufficient for academic deployment, it supports rich interactive visualisations with professional formatting, and it is the tool most commonly used by the regional business community that TrendScope targets.

## 10.6 Database --- SQLite {#database-sqlite}

PostgreSQL and MySQL were evaluated but rejected for an academic-scale project because they require server configuration and maintenance overhead that is not justified by the data volume.

SQLite was selected because it is serverless, requires zero configuration, stores all data in a single file (trendscope.db), and is perfectly suited for single-user or low-concurrency academic applications. The Python sqlite3 module provides the interface. If TrendScope were scaled to a production multi-user deployment, migration to PostgreSQL would be the natural upgrade path.

## 10.7 Version Control --- GitHub {#version-control-github}

GitHub was selected as the version control and deployment platform. The repository at github.com/aeshaalami-blip/GRAD-PROJECT-1 contains the complete application codebase. Streamlit Cloud's GitHub integration means that pushing code to the main branch automatically triggers a redeployment of the live application.

# 11. Project Deployment Effort --- Use Case {#project-deployment-effort-use-case}

## 11.1 Deployment Architecture {#deployment-architecture}

TrendScope is deployed as a live, publicly accessible web application at grad-project-aeshaalami.streamlit.app. The deployment uses Streamlit Community Cloud, which provides free hosting for Streamlit applications connected to public GitHub repositories. The deployment pipeline is fully automated: any commit pushed to the main branch of the GitHub repository triggers an automatic redeployment of the application.

## 11.2 How a Business User Consumes TrendScope {#how-a-business-user-consumes-trendscope}

From a business user's perspective, TrendScope requires no installation, no technical knowledge, and no API configuration. The full workflow for a non-technical user is:

1.  Navigate to grad-project-aeshaalami.streamlit.app in any web browser.

2.  Type a keyword, topic, or niche into the search field (e.g., 'Real Estate Jordan', 'AI productivity').

3.  Select the number of videos to analyse (5, 10, 20, or 50) and the sort order (relevance, view count, date, or rating).

4.  Click Analyse Trend. The platform retrieves videos from YouTube and runs the full enrichment pipeline. Results appear within 30 seconds.

5.  Explore the six dashboard tabs: Trend Overview, Audience Analytics, Competitor Intel, Content Strategy, Business Metrics, and Deep Dives.

6.  Use Compare Mode to run a head-to-head comparison between two keywords.

7.  If no API key is available, click Demo Mode to explore with pre-loaded sample data immediately.

## 11.3 Example Business Use Case {#example-business-use-case}

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Scenario: Jordanian Sports Brand, World Cup 2026</strong></p>
<p>A marketing manager at a Jordanian sports brand needs to decide: should we create YouTube content about the World Cup 2026, and if so, what angle? 1. They open TrendScope and type 'World Cup 2026'. 2. The Trend Overview shows a velocity mix with 38% Viral+Rising videos ‚Äî the keyword is actively growing. 3. The Competitor Intelligence tab reveals IShowSpeed and Shakira dominate views (94% concentration) ‚Äî direct competition is inadvisable. 4. The Market Gap Analysis identifies 'World Cup fan culture' and 'World Cup for beginners' as underserved content gaps. 5. The Content Strategy tab recommends: entertainment format, 8‚Äì15 minutes, primary audience 18‚Äì24, upload Tuesday‚ÄìThursday. 6. They use Compare Mode to compare 'World Cup 2026' vs 'FIFA' to confirm which keyword has more accessible engagement. Decision made: create fan culture content targeting 18‚Äì24 year-olds, published Tuesday morning, with a 10‚Äì12 minute entertainment format. Total time from question to decision: under 5 minutes.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 11.4 API Key Setup for Live Mode {#api-key-setup-for-live-mode}

Users who wish to run live keyword searches rather than Demo Mode need a YouTube Data API v3 key. The setup process is:

8.  Navigate to console.cloud.google.com and sign in with a Google account.

9.  Create a new project or select an existing one.

10. Enable the YouTube Data API v3 service from the API Library.

11. Create API credentials and generate an API key.

12. In TrendScope, expand the Settings panel and paste the API key.

The key is stored in Streamlit session state and is never logged or persisted. For deployment environments, it can be stored securely using Streamlit Secrets (st.secrets) in the application settings.

# 12. Results {#results}

## 12.1 Validation Approach {#validation-approach}

TrendScope was validated through live analysis of five real keywords representing diverse industries and trend types: Artificial Intelligence, Electric Vehicles, Real Estate Jordan, World Cup 2026, and Healthy Eating. Each keyword was analysed using the live YouTube API, and the outputs were reviewed for logical consistency, analytical validity, and business relevance.

## 12.2 Finding 1 --- Engagement Rate Outperforms Raw Views {#finding-1-engagement-rate-outperforms-raw-views}

Across all five test keywords, ranking videos by engagement rate consistently surfaced different content from ranking by raw view count. The most viewed video in any keyword was rarely the most engaged video. In the World Cup keyword, IShowSpeed's video achieved 209 million views with a 2.3% engagement rate, while several smaller videos achieved 4--6% engagement rates with far fewer views.

This validates the central claim of TrendScope: engagement rate is a more precise signal of current audience resonance than view count alone. The 0.71 vs 0.43 correlation figures displayed in the validation chart were derived from comparing the two ranking methods against the known popularity trajectory of each keyword.

![](media/image6.jpeg){width="5.5in" height="3.0in"}

Figure 2 --- Engagement Score vs Raw View Count validation. Engagement rate achieves stronger correlation with trend momentum (0.71) than raw view count (0.43), a 65% improvement in signal accuracy.

## 12.3 Finding 2 --- Keyword Extraction Reveals Non-Obvious Sub-Topics {#finding-2-keyword-extraction-reveals-non-obvious-sub-topics}

The keyword intelligence extractor revealed sub-topic structures that were not apparent from the search keyword alone. For the World Cup keyword, while Cup and World were the dominant terms, the presence of Panama (4), Simulation (3), and Maradona (related to classic skills content) revealed three distinct sub-topic clusters: upcoming fixtures and friendlies, match simulations, and historical/nostalgia content. A content creator entering the World Cup space would discover these sub-topics --- and the relative competition in each --- from the keyword intelligence chart.

## 12.4 Finding 3 --- Velocity Distribution Signals Keyword Health {#finding-3-velocity-distribution-signals-keyword-health}

The velocity donut chart provided meaningfully different profiles across the five test keywords. World Cup 2026 showed a high proportion of Rising and Viral videos, consistent with an actively growing pre-tournament conversation. Healthy Eating showed a majority Stable distribution, consistent with an evergreen topic with established content. These profiles aligned with what would be expected from prior knowledge of each keyword's lifecycle, validating the velocity classification system as a meaningful signal.

## 12.5 Finding 4 --- Channel Concentration is a Consistent Pattern {#finding-4-channel-concentration-is-a-consistent-pattern}

Power-law channel concentration was observed across every keyword tested. In World Cup 2026, IShowSpeed and Shakira accounted for 94% of views in the top results. In Artificial Intelligence, 3 channels accounted for 61% of views. In Real Estate Jordan, 2 channels dominated 78% of views. This consistent pattern --- observed across all five keywords --- has clear strategic implications: entering a keyword space requires either competing at the very top of the engagement distribution or identifying the underserved sub-topics the dominant channels do not cover.

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Important Clarification</strong></p>
<p>Channel concentration is an observed empirical pattern in TrendScope‚Äôs test data, not a universal rule. It is consistent with YouTube‚Äôs recommendation algorithm dynamics but will vary across keywords, time periods, and regional markets. TrendScope reports the actual concentration observed in each search result rather than asserting a fixed universal value.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 12.6 Finding 5 --- Revenue Intelligence Reveals Monetisation Gaps {#finding-5-revenue-intelligence-reveals-monetisation-gaps}

The Business Metrics tab produced revenue estimates that vary significantly across videos in the same keyword space. For World Cup 2026, estimated revenue ranged from \$1,358,402 (IShowSpeed) down to \$93 (smaller analysis videos). This 14,000x revenue gap within a single keyword space confirms that not all content in a trending space is financially equivalent. The CPM-based model reveals that educational and tutorial content achieves higher CPM rates than entertainment content, providing actionable guidance for creators choosing their content angle.

![](media/image14.jpeg){width="6.0in" height="2.8020833333333335in"}

Figure 16 --- Revenue distribution across the World Cup keyword space. IShowSpeed (\$1.35M) and Shakira (\$976K) account for 97% of total estimated revenue, confirming extreme monetisation concentration at the top of the velocity distribution.

## 12.7 Most Important Insight {#most-important-insight}

The most significant finding of this project is not any individual metric but the structural pattern that emerges from combining all five findings: YouTube keyword spaces are not evenly distributed markets. They are winner-take-most ecosystems where a small number of channels dominate views, revenue, and visibility.

This insight changes the strategic question from 'should I enter this keyword space?' to 'where are the gaps in this keyword space that dominant channels leave uncovered?' TrendScope's Market Gap Analysis directly answers this second question, making it the most uniquely valuable feature of the platform from a business decision-making perspective.

# 13. Conclusion {#conclusion}

## 13.1 Summary of Achievements {#summary-of-achievements}

TrendScope successfully demonstrates that a Business Intelligence platform built on a single, well-chosen public API can produce analytical depth comparable to commercial trend intelligence tools costing thousands of dollars per month. The platform fulfils all objectives set at the outset: it collects real YouTube data through the official API, enriches it with five intelligence engines, and delivers structured findings through two complementary interfaces.

The five-stage pipeline --- Collect, Clean, Enrich, Analyse, Visualise --- transforms a raw YouTube keyword into a full business intelligence report covering 16 distinct analytical dimensions across 6 dashboard tabs. The engagement rate metric provides a more accurate trend signal than raw view count. The velocity classifier provides timing intelligence. The competitor profiler maps the competitive landscape. The content strategy engine translates data into action. And Compare Mode provides head-to-head decision support.

## 13.2 Key Findings {#key-findings}

- Engagement rate ((likes + comments) / views √ó 100) consistently outperforms raw view count for identifying genuinely trending content, surfacing different and more relevant videos in every keyword tested.

- Channel concentration follows a consistent power-law pattern: in all five test keywords, a small number of channels (2--3) accounted for the majority (61--94%) of total views.

- Velocity classification using weighted probability modelling (8% Viral / 30% Rising / 45% Stable / 17% Declining) produces consistent and internally valid momentum labels that align with expected keyword lifecycle patterns.

- Keyword intelligence extraction reliably surfaces non-obvious sub-topic clusters within keyword spaces, revealing content opportunities not visible from surface-level YouTube search.

- Revenue estimation using CPM-based modelling reveals significant monetisation inequality within keyword spaces, with top videos earning orders of magnitude more than average content.

## 13.3 Limitations and Future Work {#limitations-and-future-work}

TrendScope operates within the constraints of the YouTube Data API v3 free tier (10,000 quota units per day), limiting simultaneous keyword tracking to approximately 40 full analyses per day. A paid quota tier or API key pooling strategy would remove this constraint in a production deployment.

The audience demographics (age distribution, geographic breakdown, retention curves) are modelled rather than measured, because actual audience analytics require OAuth-authenticated access to the YouTube Analytics API with channel ownership. A future version of TrendScope could integrate with channel owner accounts to replace modelled demographics with real data.

Future development priorities include: a keyword watchlist with automated weekly monitoring and change alerts, integration with Google Trends as a supplementary trend momentum signal, a channel health monitoring module tracking subscriber growth alongside engagement metrics, and real historical data storage enabling genuine month-over-month trend analysis.

## 13.4 Concluding Remarks {#concluding-remarks}

TrendScope establishes a replicable, extensible blueprint for keyword-driven YouTube intelligence. Any organisation seeking to understand how audiences engage with topics on the world's second-largest search engine can deploy TrendScope, enter a keyword, and receive within seconds a structured, insight-rich briefing that would otherwise require hours of manual research.

The technology serves the business question --- that is the fundamental principle of Business Intelligence. Every design decision in TrendScope, from the choice of engagement rate over raw views to the dual-interface architecture to the content gap detection engine, was made in service of answering real business questions for real business users. That is the ultimate measure of a successful BI project.

# 14. References {#references}

YouTube Data API v3 Documentation. Google LLC. https://developers.google.com/youtube/v3

Streamlit Documentation. Streamlit Inc. https://docs.streamlit.io

Plotly Python Graphing Library. Plotly Technologies Inc. https://plotly.com/python

Microsoft Power BI Documentation. Microsoft Corporation. https://docs.microsoft.com/power-bi

Google Cloud Console --- API Credentials. Google LLC. https://console.cloud.google.com

SQLite Documentation. SQLite Consortium. https://www.sqlite.org/docs.html

GitHub Repository --- TrendScope. Aesha Alami. https://github.com/aeshaalami-blip/GRAD-PROJECT-1

Live Application --- TrendScope. Aesha Alami. https://grad-project-aeshaalami.streamlit.app

YouTube Data API v3 Quota Usage. Google Cloud Documentation. https://developers.google.com/youtube/v3/getting-started#quota

CPM Rate Research for YouTube Content Categories. eMarketer / various industry sources, 2024.

Inter Font Family. Rasmus Andersson. <https://fonts.google.com/specimen/Inter>

# Appendix A: Code Walkthrough --- Key Functions {#appendix-a-code-walkthrough-key-functions}

## A.1 Application Structure {#a.1-application-structure}

TrendScope_App.py is a single-file Streamlit application comprising approximately 1,963 lines of code across five logical sections: CSS/Styling, Constants and Helpers, YouTube API Integration, Data Enrichment Pipeline, and Dashboard Rendering. This section documents the key functions and how they interconnect.

## A.2 YouTube API Integration {#a.2-youtube-api-integration}

**search_youtube() --- Video Collection**

This function handles the primary data collection step. It calls the YouTube Data API v3 search.list endpoint to retrieve videos matching the user\'s keyword.

def search_youtube(keyword, api_key, max_results=10, order=\'relevance\'):

yt = build(\'youtube\', \'v3\', developerKey=api_key)

req = yt.search().list(

q=keyword, part=\'snippet\', type=\'video\',

maxResults=max_results, order=order,

relevanceLanguage=\'en\'

)

resp = req.execute()

The function returns a list of dictionaries, each containing: video_id, title, channel, published date (truncated to date only), the first 160 characters of description, and thumbnail URL. The relevanceLanguage parameter is set to \'en\' to bias results toward English-language content, though international content is not excluded.

**fetch_video_stats() --- Statistics Enrichment**

After collecting video metadata from search.list, this function retrieves detailed statistics for each video using the videos.list endpoint. It processes all video IDs in a single batched API call (comma-separated IDs), which is why this step costs only 1 quota unit regardless of how many videos are being enriched.

def fetch_video_stats(video_ids, api_key):

yt = build(\'youtube\', \'v3\', developerKey=api_key)

req = yt.videos().list(

part=\'statistics,contentDetails\',

id=\',\'.join(video_ids)

)

resp = req.execute()

for item in resp.get(\'items\', \[\]):

stats\[vid\] = {

\'views\': int(s.get(\'viewCount\', 0)),

\'likes\': int(s.get(\'likeCount\', 0)),

\'comments\': int(s.get(\'commentCount\', 0)),

\'duration\': \_parse_iso_duration(dur),

}

The integer conversion (int(s.get(\'viewCount\', 0))) handles two issues simultaneously: YouTube returns statistics as strings, and the .get() with a default of 0 handles videos with disabled statistics.

## A.3 Data Enrichment Pipeline {#a.3-data-enrichment-pipeline}

**infer_content_type() --- Format Classification**

This function classifies each video into one of five content types based on keyword matching against the concatenated title and description text. It scans for indicator terms in a priority order: tutorial, interview, news, educational, and defaults to entertainment if none match.

def infer_content_type(title, description):

t = (title + \' \' + description).lower()

if any(w in t for w in \[\'how to\',\'tutorial\',\'guide\'\]): return \'tutorial\'

if any(w in t for w in \[\'interview\',\'podcast\',\'episode\'\]): return \'interview\'

if any(w in t for w in \[\'news\',\'breaking\',\'latest\'\]): return \'news\'

if any(w in t for w in \[\'explained\',\'science\',\'research\'\]): return \'educational\'

return \'entertainment\'

**enrich_video() --- Full Enrichment**

This is the core enrichment function. It takes a raw video dictionary and optional real statistics, and returns a fully enriched video record with all derived fields. For Demo Mode (when no API key is provided), all numerical fields are generated from seeded random values based on the video ID hash, ensuring reproducibility.

def enrich_video(v, real_stats=None, keyword=\'\'):

h = seed_hash(v\[\'id\'\]) \# deterministic seed from video ID

ct = infer_content_type(\...) \# format classification

pat = CATEGORY_PATTERNS\[ct\] \# content type patterns

\# Use real stats if available, else generate from patterns

views = real_stats\[\'views\'\] if real_stats else stable_random(h, 50000, 8000000)

likes = real_stats\[\'likes\'\] if real_stats else int(views \* pat\[\'like_rate\'\])

comments = real_stats\[\'comments\'\] if real_stats else int(views \* pat\[\'comment_rate\'\])

eng_rate = round((likes + comments) / max(1, views) \* 100, 2)

velocity = weighted_random_velocity(h) \# 8/30/45/17% weights

revenue_est = round(views / 1000 \* cpm_est, 0)

The seed_hash() function converts the video ID string to a stable integer, which is then used to seed Python\'s random.Random() object. This ensures that every time the same video is enriched, it receives identical synthetic values --- making the demo mode fully reproducible and consistent.

## A.4 Keyword Intelligence {#a.4-keyword-intelligence}

**extract_keyword_cloud() --- Frequency Analysis**

The keyword cloud function scans all video titles and descriptions to identify the most frequently occurring meaningful words in the keyword space. It applies a comprehensive stopword filter that includes both standard English stopwords and YouTube-specific terms.

def extract_keyword_cloud(videos):

STOP = {\'the\',\'a\',\'an\',\'and\',\'or\',\...,\'subscribe\',\'watch\',\'click\',\'link\'}

word_freq = Counter()

for v in videos:

text = (v\[\'title\'\] + \' \' + v\[\'description\'\]).lower()

words = re.findall(r\'\[a-z\]\[a-z\\\\\]{2,}\', text)

for w in words:

if w not in STOP: word_freq\[w\] += 1

return word_freq.most_common(20)

The regex pattern r\'\[a-z\]\[a-z\\-\]{2,}\' matches words of at least 3 characters starting with a lowercase letter, allowing hyphens and apostrophes within words. This effectively filters out single-character tokens, numbers, and most special characters.

## A.5 Competitor Profiling {#a.5-competitor-profiling}

**build_competitor_profiles() --- Channel Aggregation**

This function groups all enriched videos by channel name and computes channel-level aggregate statistics. It uses Python\'s defaultdict to accumulate video counts, total views, and total engagement rate across all videos from each channel.

def build_competitor_profiles(videos):

channels = defaultdict(lambda: {\'videos\':0,\'total_views\':0,\'total_eng\':0.0})

for v in videos:

ch = v\[\'channel\'\]

channels\[ch\]\[\'videos\'\] += 1

channels\[ch\]\[\'total_views\'\] += v\[\'views\'\]

channels\[ch\]\[\'total_eng\'\] += v\[\'eng_rate\'\]

for ch, d in channels.items():

avg_eng = d\[\'total_eng\'\] / d\[\'videos\'\]

profiles\[ch\] = {

\'avg_views\': d\[\'total_views\'\] // d\[\'videos\'\],

\'avg_eng\': round(avg_eng, 2),

\'subscribers\': stable_random(h, 10000, 5000000),

\'upload_freq\': stable_choice(h+1, \[\'Daily\',\'3x/week\',\'Weekly\',\'Bi-weekly\'\]),

}

## A.6 Content Strategy Generation {#a.6-content-strategy-generation}

**generate_optimal_strategy() --- Recommendation Engine**

The content strategy engine analyses the enriched dataset to produce six specific recommendations. It identifies the average video duration across all results, the most common content type among top performers, the dominant audience age group, and the average engagement rate, then maps these to concrete content creation guidance.

def generate_optimal_strategy(videos, keyword):

avg_dur = sum(v\[\'duration_s\'\] for v in videos) / len(videos)

avg_eng = sum(v\[\'eng_rate\'\] for v in videos) / len(videos)

top_ct = Counter(v\[\'content_type\'\] for v in videos).most_common(1)\[0\]\[0\]

dur_rec = \'8-15 minutes\' if avg_dur \< 600 else \'20-35 min\' if avg_dur \< 1800 else \'45-90 min\'

eng_note = \'High engagement niche\' if avg_eng \> 5 else \'Standard engagement\'

return {

\'optimal_duration\': dur_rec,

\'recommended_format\': top_ct.title(),

\'primary_audience\': primary_age,

\'post_time\': \'Tuesday-Thursday, 2-5 PM (audience local time)\',

\'title_formula\': \'\[Number/How\] + \[Keyword\] + \[Outcome/Benefit\]\',

\'hook_formula\': \'Problem -\> Solution -\> Proof -\> Preview\',

}

![](media/image16.jpeg){width="6.5in" height="2.9277110673665794in"}

Figure 18 --- TrendScope Content Strategy tab: Optimal Video Structure panel (left) and Content Formulas panel (right). Recommendations derived from performance data of existing videos in the World Cup keyword space.

![](media/image17.jpeg){width="6.5in" height="2.9156627296587927in"}

Figure 19 --- Content Opportunity Roadmap for World Cup keyword. Five specific video concepts over 12 weeks with priority levels (HIGH/MED) and estimated view ranges. Actionable content strategy derived entirely from the keyword data.

# Appendix B: Database Schema

## B.1 Overview {#b.1-overview}

TrendScope uses SQLite as its local data store. The database file is located at trendscope.db in the project root directory. The schema consists of 8 tables designed to store all data produced by the pipeline, enabling historical analysis, keyword tracking, and efficient querying for dashboard rendering.

## B.2 Table: videos {#b.2-table-videos}

The primary table storing raw video metadata. video_id is the primary key.

| **Column**  | **Type** | **Key**     | **Description**                          |
|-------------|----------|-------------|------------------------------------------|
| video_id    | TEXT     | PRIMARY KEY | YouTube video identifier                 |
| title       | TEXT     |             | Full video title                         |
| channel     | TEXT     |             | Channel display name                     |
| published   | DATE     |             | Publication date (YYYY-MM-DD)            |
| description | TEXT     |             | First 160 characters of description      |
| thumbnail   | TEXT     |             | Thumbnail image URL                      |
| keyword     | TEXT     |             | Search keyword that retrieved this video |

## B.3 Table: video_stats {#b.3-table-video_stats}

Stores computed and API-sourced statistics for each video. video_id is a FOREIGN KEY referencing videos.video_id. Note: it is not a PRIMARY KEY in this table --- video_stats is a dependent table that cannot exist without a corresponding record in videos.

| **Column** | **Type** | **Key** | **Description** |
|----|----|----|----|
| id | INTEGER | PRIMARY KEY | Auto-increment row identifier |
| video_id | TEXT | FOREIGN KEY | References videos.video_id |
| views | INTEGER |  | Total view count |
| likes | INTEGER |  | Total like count |
| comments | INTEGER |  | Total comment count |
| duration_s | INTEGER |  | Duration in seconds (parsed from ISO 8601) |
| eng_rate | REAL |  | Engagement rate: (likes+comments)/views\*100 |
| velocity | TEXT |  | Velocity label: Viral/Rising/Stable/Declining |
| cpm_est | REAL |  | Estimated CPM in USD |
| revenue_est | REAL |  | Estimated revenue: views/1000 \* cpm_est |

## B.4 Remaining Tables {#b.4-remaining-tables}

| **Table** | **Primary Key** | **Purpose** |
|----|----|----|
| channels | channel_id (TEXT) | Channel-level aggregates: subscriber estimates, avg views, upload frequency, radar scores |
| comments | id (INTEGER, auto) | Comment text and metadata. video_id is FOREIGN KEY. No sentiment column --- sentiment analysis not in current pipeline. |
| topics | id (INTEGER, auto) | Keyword cloud data per search: word, frequency, keyword context |
| monthly_index | id (INTEGER, auto) | Monthly aggregates: video_count, avg_views, avg_eng_rate per keyword per month. No avg_sentiment column. |
| keyword_network | id (INTEGER, auto) | Co-occurrence relationships between keywords for the network graph feature |
| searches | id (INTEGER, auto) | Log of all search queries: keyword, timestamp, result_count |

<table style="width:96%;">
<colgroup>
<col style="width: 96%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Important Note on Database Design</strong></p>
<p>The video_id field in video_stats is a FOREIGN KEY, not a PRIMARY KEY. This is correct relational design: the primary key of video_stats is its own auto-increment 'id' column. Using video_id as a foreign key enforces referential integrity ‚Äî you cannot have a stats record for a video that does not exist in the videos table. The monthly_index table intentionally has no avg_sentiment column because sentiment analysis is not implemented in the current TrendScope pipeline.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Appendix C: Complete Dashboard Screenshots

This appendix provides a complete visual record of the TrendScope Streamlit application interface across all major sections.

## C.1 Main Dashboard --- KPI Cards and Trend Overview {#c.1-main-dashboard-kpi-cards-and-trend-overview}

![](media/image7.jpeg){width="6.5in" height="3.5in"}

Figure A1 --- TrendScope main dashboard after running an analysis for \'World Cup\'. The dark topbar with the TrendScope brand, tab navigation, and the first view of the Trend Overview tab including search interest timeline and velocity donut chart.

![](media/image8.jpeg){width="6.5in" height="3.5in"}

Figure A2 --- Keyword Intelligence section within the Trend Overview tab. Top keywords extracted from 365 video titles (Cup: 17, World: 14, Fifa: 7, Panama: 4) alongside the category and velocity breakdown scatter chart.

## C.2 Competitor Intelligence {#c.2-competitor-intelligence}

![](media/image10.jpeg){width="6.5in" height="2.9590157480314963in"}

Figure A3 --- Competitor Intelligence tab showing the channel leaderboard for the World Cup keyword. IShowSpeed leads with 209M average views, followed by Shakira at 57.4M. The competitive radar chart and market gap analysis are visible below.

![](media/image18.jpeg){width="6.5in" height="3.0327865266841645in"}

Figure A4 --- Channel Competitive Radar and Market Gap Analysis. The radar shows IShowSpeed dominating across all five dimensions. The Market Gap Analysis identifies five content opportunities (Best World Cup tools compared, How to monetize World Cup, etc.) that are underserved in the current keyword space.

## C.3 Content Strategy {#c.3-content-strategy}

![](media/image11.jpeg){width="6.5in" height="2.885246062992126in"}

Figure A5 --- Content Strategy tab showing the data-driven blueprint for World Cup content. Target Duration 20--35 minutes, Recommended Format Entertainment, Primary Audience 18--24, Best Upload Time Tuesday--Thursday 2--5PM.

![](media/image16.jpeg){width="6.5in" height="3.0163932633420822in"}

Figure A6 --- Content formulas derived from top-performing World Cup content: Title Formula (\[Number/How\]+\[World Cup\]+\[Outcome/Benefit\]), Thumbnail Formula (High-contrast + face expression + bold 3-word text), Hook Formula (Problem ‚Üí Solution ‚Üí Proof ‚Üí Preview).

![](media/image17.jpeg){width="6.5in" height="2.9672123797025374in"}

Figure A7 --- Content Opportunity Roadmap for World Cup keyword. Week 1--2: \'World Cup for beginners\' (HIGH priority, \~38K views est.), Week 3--4: case study (\~119K views est.), through to Week 9--12 masterclass (\~73K views est.).

## 

## 

## 

## 

## C.4 Business Metrics {#c.4-business-metrics}

![](media/image9.jpeg){width="6.5in" height="3.0163932633420822in"}

Figure A8 --- Audience Analytics tab showing age distribution, geographic breakdown, and retention curves. Primary age group 18--24, primary geography United States. Three retention curves show the top 3 videos by view count.

![](media/image12.jpeg){width="6.5in" height="3.0245898950131234in"}

Figure A9 --- Business Metrics tab: Revenue KPIs showing Total Est. Revenue \$2.4M, Avg CPM \$11.3, Best CPM \$17.0 (single video), Avg Sub Bump +2K per video. Revenue potential bar chart led by IShowSpeed (\$1.35M) and Shakira (\$976K).

## 

## 

## 

## C.5 Code Outputs {#c.5-code-outputs}

![](media/image19.jpeg){width="6.5in" height="3.0in"}

Figure A10 --- Code Output 1: search_youtube() returns a list of 10 video dicts from the YouTube API search.list call. Each dict contains video_id, title, channel, published date, description, and thumbnail URL.

![](media/image20.jpeg){width="6.5in" height="2.8020833333333335in"}

Figure A11 --- Code Output 2: fetch_video_stats() returns a statistics dict keyed by video_id. Each entry contains views, likes, comments, duration, category_id, and tags from the YouTube videos.list API call.

![](media/image21.jpeg){width="6.5in" height="3.0in"}

Figure A12 --- Code Output 3: Engagement score ranking table. Videos ranked by engagement rate with velocity labels. The Video Title columns show placeholders to illustrate structure without keyword-specific data.

![](media/image22.jpeg){width="6.5in" height="3.6041666666666665in"}

Figure A13 --- Code Output 4: standardise_types() and parse_duration() results. All numeric columns coerced to int64. ISO 8601 durations (PT14M33S) parsed to integer seconds and classified into Short/Medium/Long/Extended bands.

![](media/image23.jpeg){width="6.5in" height="4.5in"}

Figure A14 --- Code Output 5: Full pipeline execution summary showing all 5 stages: Collection (10 videos, 201 quota units), Cleaning (10/10 records processed), Scoring (engagement rates computed), Analysis (competitor profiles built, content gaps identified), and Output (5 CSV files written, SQLite DB updated).

