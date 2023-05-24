#### Yingzi Jin

The code is implemented using Python 3.10.9. To install all the required dependencies, you can run the following command in the terminal. Please make sure that the requirements.txt file is in the working repository:
```
pip install -r requirements.txt
```

## Research Question
What is the relationship between emotional intensity in social media content and information engagement? And how do the valence of emotions and moral convictions moderate the relationship?

## Data
In this study, I utilize data scraped from Twitter. The data is collected using three sets of keywords: 1) abortion/miscarriage, 2) music/movie, and 3) the. Only tweets in English are scraped. To avoid any duplicates, the tweets collected with each set of keywords are mutually exclusive. To minimize the impact of heated discussions around particular social issues within a short period, I scraped 30 tweets daily from November 1, 2022 to April 17, 2023. For each tweet, I collected the following information: the exact time the tweet was posted, the user ID who posted the tweet, the tweet content, the count of retweets, the count of likes, the count of comments, and the count of followers of the user.

Tweets scraped based on the three sets of keywords corresponds to three datasets: abortion, music, and random 

Emotional Intensity: 

This variable is represented as the "compound" calculated using VADER package, ranges from -1 to 1, where negative represents negative sentiment, positive value represents positive sentiment, and the value represents the intensity.

## Codebook

| Vairable | Description |
| --- | --- |
| Date | the exact time the tweet was posted |
| User | the user ID who posted the tweet |
| Tweet | the tweet content |
| retweetCount | the count of retweets |
| likeCount | the count of likes |
| replyCount | the count of comments |
| followersCount | the count of followers of the user |
| compound | emotional intensity with valence |
| engagement | aggregation of retweetCount, replyCount, likeCount |
| absolute_intensity | absolute value of compound |

## Method
Logistic regression models are created to examine the relationship between absolute intensity (independent variable) and binary engagement (dependent variable), while controlling for the count of followers (confounding variable). Additionally, logistic regression models are created for each set of keywords, considering positive and negative content separately, to explore the second research question, that is, how valence and moral convictions may moderate this relationship.

Linear regression models are created to examine the relationship between absolute intensity (independent variable) and log-transformed non-zero engagement score (dependent variable), while also controlling for the count of followers (confounding variable). Similarly, linear regression models are developed for each set of keywords, considering positive and negative content separately, to examine the potential moderating effects of valence and moral convictions.


## Findings

<img src="table2.png">

Table 2 shows that the absolute intensity of positive emotions in tweets across all topics has a strong significant effect on engagement. The positive coefficients (0.5049, 0.6156, 0.9026) indicate that tweets with more positive emotions are more likely to be engaged. However, no significant effect is observed in the case of negative emotions. 

<img src="table3.png">

In Table 3, the coefficients of absolute intensity show that the absolute intensity of positive emotions in tweets about random (0.0779) and music/movie topics (0.0561) has a positive and significant relationship with engagement. This indicates that tweets on random or music/movie topics are more likely to have higher engagement if they contain more positive emotions. However, this effect is not observed in tweets about abortion. Furthermore, the absolute intensity of negative emotions in tweets across all topics is not significantly related to engagement.

<img src="fig2.png">

Figure 2 shows the distribution of compound scores over the five engagement levels for the abortion topic. When the engagement level increases, the peaks of the distribution start to become more prominent on both negative and positive sides instead of staying neutral. When engagement reaches level 4, the distribution of the compound becomes right-skewed, where the peak of the distribution is single and around medium negativity. When engagement reaches level 5, the distribution of the compound becomes slightly left-skewed, where the peak of the
distribution is single and around low positivity. 

<img src="fig3.png">

Figure 3 shows the distribution of compound scores over the five engagement levels for the music/movie topic. When the engagement level increases, the peaks of the distribution start to become prominent only on the positive sides. When engagement reaches level 4, the distribution of the compound becomes left-skewed, where the global peak of the distribution is around medium-high positivity. 

## Conclusions

First, the study explored the effect of emotional intensity on information engagement. The results demonstrated that tweets with higher levels of positive emotions were more likely to receive at least engagement, as indicated by likes, shares, and comments. However, no significant effect was observed for tweets with higher levels of negative emotions. This suggests that there is a more complex mechanism behind how negative emotions affect behaviors on social media. These findings support previous research highlighting the role of emotional valence in promoting information engagement.

Second, the study examined the moderating effect of moral convictions on the relationship between emotional intensity and information engagement. The results indicated that moral convictions amplified the effect of emotional intensity on information engagement. Specifically, individuals with stronger moral convictions were more likely to engage with emotionally intense content. This suggests that moral convictions play a significant role in shaping individuals' motivation to engage with information and share it with their social networks.


## Replication
Although you can find the code I used to scarpe tweets here [tweet_scrape.ipynb](/data/tweet_scrape.ipynb), the scraper I was using (snscrape) is no longer supporting the functions I used. Therefore, you cannot replicate the data-scraping process. However, I stored the scraped datasets as csv. files [abortion.csv](/data/abortion.csv), [music.csv](/data/music.csv), [random.csv](/data/random.csv)). You can still replicate the results on the datasets. 
To replicate the results, please make sure that you install all necessary packages stated in [requirements.txt](requirements.txt), make sure that the datasets are in the working repository, and then run [analysis.ipynb](/analysis/analysis.ipynb).

How to cite this repository:

Jin, Y. (2023). Emotional Intensity and Information Engagement on Twitter. GitHub repository. https://github.com/macs30200-s23/replication-materials-YingziJin.git