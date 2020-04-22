# Capstone Project: Social media sentiment analysis 

## Problem Statement

The project aims to gather and analyze consumers’ sentiment and major feedback on the company’s brand, products and advertisement to improve a company's marketing strategy. For this project, I will focus on Samsung and its competitors (Apple and Huawei).

Traditional metrics focus on quantity (number of views, clicks, comments, shares, like, etc.) does not reflect consumers' sentiments and key thoughts. Sentiment analysis goes beyond quantitative data to the quality of the interactions between the public and brands: 
1. Sentiment analysis provides invaluable marketing intel 
2. A crucial part of market research 
3. A revolution in customer support
[Reference: https://www.forbes.com/sites/jiawertz/2018/11/30/why-sentiment-analysis-could-be-your-best-kept-marketing-secret/#76f0c3d12bbe]


## Dataset

1) Twitter API
- 2500 tweets containing the word "Samsung" collected 8-9 Apr 2020
- 2500 tweets containing the word "Apple" collected 8-9 Apr 2020
- 2500 tweets containing the word "Huawei" collected 8-9 Apr 2020

2) YouTube API
- 7331 comments on Samsung's S20 Ultra video
- up to 100 comments on 50 videos from SamsungSingapore channel


## Sentiment Analysis

VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media. VADER has been found to be quite successful when dealing with social media texts, NY Times editorials, movie reviews, and product reviews. This is because VADER not only tells about the Positivity and Negativity score but also tells us about how positive or negative a sentiment is.
[Reference: https://medium.com/analytics-vidhya/simplifying-social-media-sentiment-analysis-using-vader-in-python-f9e6ec6fc52f]

- Each tweet and YouTube comment is assessed by VADER and given a rating from -1 to 1 on how positive or negative the comment is.
- The five most positive and five most negative comments across all of the tweets and YouTube comments are identified for each brand.
- For YouTube videos, the average sentiment on a particular video is tracked over time.
- For YouTube channel, a comparison among different videos in a channel is made.


## Topic Modeling
### Latent Dirichlet Allocation (LDA) 
Dataset: Samsung, Huawei and Apple's 2500 tweets respectively
Model: sklearn’s LDA
Performance metric: Perplexity (degree of uncertainty, lower value is better)
Preprocessing: Cleaning and CountVectorizer (compared with TFID vectorizer)
Optimised parameters (through gridsearch): Number of topics and learning decay
Limitation: Insufficient amount of data (~400 negative Samsung tweets)

### Gibbs Sampling Dirichlet Mixture Model (GSDMM)
LDA’s assumption that a text is a mixture of topics is not true for Tweets
GSDMM should perform better on Short Text Topic Modeling (STTM) task as it assumes 1 topic ↔️1 document
Limitation: Lack of comparable performance metrics as GSDMM is less used model
Comparison: GSDMM has a more balanced document-topic split

## Samsung stock price prediction based on YouTube sentiments
Dataset: 40 days of Samsung Electronics stock price listed on Frankfurt Exchange & 40 days of comments collected on Samsung S20 Ultra YouTube video (about 40 data points for test and train)
Models: 1) Linear regression, 2) logistic regression, 3) random forest regressor and 4)random forest regressor with gridsearch
Results: Mostly negative R2 values
Major Limitations: 
- Samsung Electronics has many entities (chips, home appliances), not only mobile phone business
- Stock price can be affected by earning release, covid-19, news
- Insufficient data

## Conclusion

Marketing insights:
1. VADER is an easy and quick method to obtain sentiment ratings
2. Twitter and YouTube statistics are not strongly correlated to sentiments gathered from comments
3. Topic modeling on comments could help marketer to dig into what people think about their brand
4. Sentiment analysis on YouTube comments provide feedback on company’s advertisement 

Limitations:
- Lack of common performance metrics to compare different topic modeling models
- Lack of target variable to train NLP models
- Insufficient tweets and YouTube comments

Future work:
- Edit GSDMM source code to include performance metric – Perplexity and coherence metrics
- Explore other STTM models like Gensim FastText
