#### Yingzi Jin
RQ: what is the relationship between emotional intensity in social media content and information engagement? And how do the valence of emotions and moral convictions moderate the relationship?

Data: 

In this study, I utilize data scraped from Twitter. The data is collected using three sets of keywords: 1) abortion/miscarriage, 2) music/movie, and 3) the. Only tweets in English are scraped. To avoid any duplicates, the tweets collected with each set of keywords are mutually exclusive. Tweets collected were posted from November 2022 to the present. To minimize the impact of heated discussions around particular social issues within a short period, I scraped 2000 tweets from each month from Nov 2022. Each month is segmented into four periods, where 500 tweets are collected from each period. For each tweet, we collected the following information: the exact time the tweet was posted, the user ID who posted the tweet, the tweet content, the count of retweets, the count of likes, the count of comments, and the count of followers of the user.

Tweets scraped based on the three sets of keywords corresponds to three datasets: abortion, music, and random 

Emotional Intensity: 

This variable is represented as the "compound" calculated using VADER package, ranges from -1 to 1, where negative represents negative sentiment, positive value represents positive sentiment, and the value represents the intensity.

Codebook:

Date: the exact time the tweet was posted

User: the user ID who posted the tweet

Tweet: the tweet content

retweetCount: the count of retweets

likeCount: the count of likes

replyCount: the count of comments

followersCount: 

compound: emotional intensity with valence

engagement: aggregation of retweetCount, replyCount, likeCount

absolute_intensity: absolute value of compound

engage_binary: 0 if engagement is 0, else 1

Initial Finding:

[table](EDA/random_logit_results.png)
I created a binary logistic regression model to predict engage_binary using absolute_intensity as the independent variable and followersCount as the confounder. The results indicate that there is a significant positive relationship between absolute_intensity and engage_binary, with a coefficient of 0.2135 (p-value=0.026). The intercept coefficient is 0.5246, and the coefficient for the confounder (followersCount) is 7.951e-06 (p-value=0.010).

Based on these findings, there is evidence to support a positive relationship between emotional intensity in social media content (as measured by the variable absolute_intensity) and information engagement (as measured by the binary outcome variable engage_binary). This means that as emotional intensity in social media content increases, there is a corresponding increase in the likelihood of information engagement.

To replicate the results, please make sure that you install all necessary packages stated in [requirements.txt](requirements.txt) and then run [EDA.ipynb](/EDA/EDA.ipynb).

How to cite this repository:

Jin, Y. (2023). Emotional Intensity and Information Engagement on Twitter. GitHub repository. https://github.com/macs30200-s23/replication-materials-YingziJin.git