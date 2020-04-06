# Capstone Project: Social media sentiment analysis [Case study: Samsung, Apple and Huawei]

## Problem Statement
Today's marketers are obsessed with sales figures. It is easy to overlook customers' feelings and emotions, which can be hard to quantify. However, consider that emotions are the number one factor in making purchasing decisions. With so many consumers sharing their thoughts and feelings on social media, it quite literally pays for brands to have a pulse on how their products make people feel.

Sentiment analysis is the process of retrieving information about a consumer’s perception of a product, service or brand. We wish to distribute the real-time sentiment data to internal marketing and strategy departments for their further analysis and peruse of the data for strategy development. 

In this project, the social media sentiment analysis is performed on three brands - Samsung, Apple and Huawei. We will be monitoring the comments made on these brands on several platforms such as Twitter, YouTube and Reddit.

## VADER Sentiment Analysis
VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media.

VADER has been found to be quite successful when dealing with social media texts, NY Times editorials, movie reviews, and product reviews. This is because VADER not only tells about the Positivity and Negativity score but also tells us about how positive or negative a sentiment is.

VADER analyses sentiments primarily based on certain key points:
- Punctuation: The use of an exclamation mark(!), increases the magnitude of the intensity without modifying the semantic orientation. For example, “The food here is good!” is more intense than “The food here is good.” and an increase in the number of (!), increases the magnitude accordingly.
- Capitalization: Using upper case letters to emphasize a sentiment-relevant word in the presence of other non-capitalized words, increases the magnitude of the sentiment intensity. For example, “The food here is GREAT!” conveys more intensity than “The food here is great!”
- Degree modifiers: Also called intensifiers, they impact the sentiment intensity by either increasing or decreasing the intensity. For example, “The service here is extremely good” is more intense than “The service here is good”, whereas “The service here is marginally good” reduces the intensity.
- Conjunctions: Use of conjunctions like “but” signals a shift in sentiment polarity, with the sentiment of the text following the conjunction being dominant. “The food here is great, but the service is horrible” has mixed sentiment, with the latter half dictating the overall rating.
- Preceding Tri-gram: By examining the tri-gram preceding a sentiment-laden lexical feature, we catch nearly 90% of cases where negation flips the polarity of the text. A negated sentence would be “The food here isn’t really all that great”.
- VADER performs very well with emojis, slangs, and acronyms in sentences.
[Reference: https://medium.com/analytics-vidhya/simplifying-social-media-sentiment-analysis-using-vader-in-python-f9e6ec6fc52f]

## Short Text Topic Modeling
To be investigated