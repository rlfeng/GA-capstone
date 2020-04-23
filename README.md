# Capstone Project: Social media sentiment analysis 

## Summary

Problem Statement: Traditional metrics focus on quantity (number of likes, views, clicks, comments, shares, etc) which may not reflect what consumers truly think of the product. 

The project aims to gather consumers’ latest sentiments and feedback on Samsung based on Twitter and YouTube comments to guide marketing strategy.

Section 1: Sentiment analysis to gather marketing intel: (Parts 2 and 4 in Github jyupter nb)
- Brand (Samsung) vs competitors (Apple & Huawei)
- Advertisement (Samsung’s YouTube videos)

Section 2: Topic modeling to collect feedback and provide better customer support:(Parts 3a, b and c in Github jyupter nb)
- LatentDirichletAllocation (LDA)
- Gibbs Sampling Dirichlet Mixture Model (GSDMM) 
- Biterm Topic Modeling (BTM)

Additional:  Samsung’s stock price prediction based on sentiment analysis (Part 5 in Github jyupter nb)

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
Model: sklearn’s LatentDirichletAllocation (LDA) – most popular for unsupervised analysis of text
Performance metric: Perplexity (lower value is better), Likelihood (less negative value is better)
Preprocessing: Cleaning and CountVectorizer (compared with TFID vectorizer)
Optimised parameters (through gridsearch): Number of topics and learning decay
Human interpretation of topics may require domain expertise

Advantages:
- Proven model on traditional documents (news and academic papers)
- Well maintained model

Disadvantages:
- Not suitable for short text as LDA assumes that a text is a mixture of topics

### Gibbs Sampling Dirichlet Mixture Model (GSDMM)
Advantages:
- Modification from LDA that assumes 1 topic ↔️1 document

Disadvantages:
- Less used model, lacking performance metrics
- Loses flexibility to capture multiple topics in one document
- Overfitting

### Biterm Topic Modeling (BTM)
Advantages:
- Use aggregated document (entire corpus) to address sparsity issue in short text
- Incorporate context by using word-pair co-occurrence patterns (biterm)

Disadvantages:
- Less used model, uses coherence score as performance metrics

### Limitation in comparison
- Lack of common performance metrics for comparison. Most literature compare the models by editing source codes to include their desired metrics. So far, no paper has compared the performance of LDA, GSDMM and BTM on Tweets using python. A few good papers compared different short text topic modeling models using java. This can be part of future work.

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
- Based on the most negative tweets picked up by VADER, Samsung could improve on customer support by improving their battery lifespan, file transfer system, etc.
- Further research on well-received Samsung YouTube advertisement video could help guide marketing effort
- Topic modeling revealed Huawei’s relatively low sentiment score could be due to association to China’s political system and ongoing US-China trade war

Limitations:
- Lack of common performance metrics to compare different topic modeling models

Future work:
- Edit GSDMM and BTM’s source code to include performance metric – Perplexity and coherence metrics and explore other STTM models like Gensim FastText

