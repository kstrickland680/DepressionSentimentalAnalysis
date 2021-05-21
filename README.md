# Depression Sentiment Analysis

## Overview

This project analyzes twitter data that has been labeled according to whether it was written by a clinically depressed individual or not.  The project explores frequently used words, conducts a topic analysis, performs sentiment analysis, and creates a model to predict whether an individual is likely to be depressed based on their social media precense on Twitter. 

## Business Problem  

A nonprofit agency focused on mental health and depression wants a way to analyze Twitter data to assess for depression in individuals. Doing so can bolster prevention efforts to help individuals with depression.  

According to the Anxiety and Depression Association of America, Major Depressive Disorder (MDD) is the leading cause of disability for adults in the US aged 15-44. Over 16.1 million adults in America are affected by it each year.  Only 61% of adults with MDD receive treatment.  The US Department of Health & Human Services estimates that 60% of individuals who commit suicide had a mood disorder, such as MDD or bipolar.  

## Data

The dataset consists of an index number, the tweet, and a classification as depressed/not depressed.  22.4% of the dataset is classified as written by a clinically depressed individual. 

I create a word cloud for tweets written by clinically depressed individuals, which features words including depression, worthless, anti, anxiety, and functioning.  I apply topic modeling over the depressed tweets. Most tweets relate to the experience of depression (1741). Smaller topics included those with lots of emojis, talk about preventing depression, or things that were related to depression. 

![picture](https://github.com/kstrickland680/DepressionSentimentalAnalysis/blob/main/images/depressionwordcloud.JPG)


## Sentiment Analysis 

Clinically depressed indviduals posted more negative tweets, less positive tweets, and slightly less neutral tweets than non-depressed individuals. 

![picture](https://github.com/kstrickland680/DepressionSentimentalAnalysis/blob/main/images/SentimentAnalysis.JPG)


## Model

The model has high accuracy, precsion, recall, and f1 scores for test data.  There is not a large difference beween test and train data for accuracy.  

I import data from Twitter to test the model against. I import the most recent 200 tweets each for #depression, #depressed, depression, and depressed. I also import 200 random tweets that do not mention depression.

I select a random amount of the tweets to look at, and look at the totals for those classified as depressed or not depressed. The model classifies most data with the word 'depressed' or 'depression' in it as from a clinically depressed individual. It struggles to recognize informational or positive posts as well as exaggeration.

### Model Refinement 

Given that the model did not perform as well as I'd like on newly sourced data, I refine the model again. I create a new class that stands for "not enough information". I do this by scrambling the order of words in the depressed tweets, to teach the model that the word 'depression' alone is not enough for a tweet to be classified as depressed.

I create 3 more versions of the model. I explore early stopping, adding dropout layers, class weights, and changing various paramaters in order to avoid overfitting and better train the model. I decide on Model 3 as the final model due to it's high recall and f1 score for depressed data, even though it does not identify any tweets as "not enough information". I want the model to catch as many depressed cases as possible. Even though this model does not classify any tweets as "not enough information", it overfits less than the orginal model does. I then apply this model and another model to the data sourced from twitter. It performs better than the first model, but does continue to struggle to correctly classify informational, positive, and exagerrated tweets.


## Conclusions

Analyzing social media data could help identify individuals who are unable or not willing to talk to professionals about their emotions. Many individuals share their emotions on social media regarding depression.  

### Business Recommendations

*   Pay attention to tweets that talk about feeling depressed -- People who say they're feeling depressed likely are.  
*   Increase social media presence.  Make informational or postive posts about depression.  
*   Pay attention to tweets talking about feeling worthless or hurting. 
*   Use how individuals talk about their experiences on social media to inform how you talk to people about depression. 

### Future Work

- create a model that codes tweets for depression criteria
- a model that does better at seeing the difference between informational tweets about depression and depressed tweets - perhaps by classifying tweets 3 ways, depressed, not depressed, information about depression.
- possibly creating a bot that could reach out to individuals seen as at-risk of depression 
- a model that flags suicidal comments or classifies risk 
