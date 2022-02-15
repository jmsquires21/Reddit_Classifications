

# **Project 3: Distinguishing Between Data Science vs. Analytics Subreddits**
### By: Jamie Squires

# Executive Summary
## Background & Overview

In recent years, many career paths in data have risen in popularity. With buzzwords like "machine learning" and "big data", it can be difficult to understand the more nuanced differences between the areas of specialty, especially within analytics and data science. In fact, one google search on the contrast between analytics and data science will yield wildly different results. According to one [Harvard Business School blog post](https://online.hbs.edu/blog/post/data-analytics-vs-data-science), they describe the difference where "data analytics is primarily focused on understanding datasets and gleaning insights that can be turned into actions, data science is centered on building, cleaning, and organizing datasets." According to another [Medium Article](https://medium.com/@springboard_ind/data-science-vs-data-analytics-how-to-decide-which-one-is-right-for-you-41e7bdec080e ), data analytics focuses more on viewing the historical data while data science focuses more on machine learning and predictive modeling. While it's interesting to see that the internet is equally confused on this topic, it's an important distinction to understand when you're looking at job postings and trying to understand what an organization is looking for.




## Problem Statement
Given the amount of overlap between the two data-centric specialties of 'Data Science' vs 'Analytics', it would be intriguing to see if there's a tangible difference in the subject matter amongst topics in the Data Science and Analytics subreddit. For the purposes of this investigation, we'd like to answer the following question:

* Can we accurately categorize reddit posts from the Data Science or Analytics subreddit?


## Methodology

We will perform a variety of classification methods to predict which subreddit titles came from which subreddit (Data Science vs Analytics) using different NLP vectorizers to assess accuracy

#### Success Metrics:
* Optimize for the highest accuracy score





## Data Dictionary

**Data Sources**

| Column      | Type    | Dataset                 | Calculated Field | Description                                                                     |
|-------------|---------|-------------------------|------------------|---------------------------------------------------------------------------------|
| created_utc | integer | both_posts_step1_xl.csv |                  | Coordinated Universal Time when the submission was posted on Reddit             |
| selftext    | object  | both_posts_step1_xl.csv |                  | Body text under title of submission/post                                        |
| subreddit   | object  | both_posts_step1_xl.csv | 1                | Classifies which subreddit the post came from ('Analytics 'or 'Data   Science') |
| title       | object  | both_posts_step1_xl.csv |                  | Submission title of post                                                        |
| ds_ind      | integer | both_posts_step1_xl.csv | 1                | Binary indicator when subreddit='Datascience'                                   |

# Findings & Recommendations:


### Results
* I performed two passes of various classification models to assess which one would yield the highest accuracy score.
* Based on our results from my first pass of classification models, I saw that Logistic Regression, Random Forests, and Gradient Boost performed the best. I tuned these models using GridSearch as shown in the table below.

|    Vectorizer   |     Classifier     | Cross Val Score | Training Accuracy | Test Accuracy |
|:---------------:|:------------------:|:---------------:|:-----------------:|:-------------:|
| CountVectorizer | LogisticRegression | 0.8009          | 0.9094            | 0.8070        |
| TF-IDF          | LogisticRegression | 0.8022          | 0.8898            | 0.8064        |
| CountVectorizer | Gradient Boost     | 0.7898          | 0.8167            | 0.7946        |
| TF-IDF          | Naïve Bayes        | 0.7861          | 0.9382            | 0.7936        |
| TF-IDF          | RandomForests      | 0.7844          | 0.8822            | 0.7886        |
| TF-IDF          | Gradient Boost     | 0.7860          | 0.8260            | 0.7886        |
| TF-IDF          | Decision Trees     | 0.7590          | 0.8530            | 0.7538        |
| TF-IDF          | KNN                | 0.7500          | 0.7596            | 0.7451        |


### Findings:
* The Logistic Regression with a Count Vectorizer model performed the best, with a testing accuracy of 80.7%.
* In our dataset, 'Data Science' had a baseline accuracy of ~50%, thus we see that our model did better than the baseline (81% vs 50%).
* Most of the remaining models performed between 75%-79%.
* Based on these results, we can see that the two subreddits of Data Science and Analytics have a lot of overlap, with many terms in common. This may be one factor as to why our models hit a ceiling with the best accuracy at 80.7%.

### Recommendation:

* Use the Logistic Regression x CountVectorizer model to predict the analytics vs data science subreddit classification. This model got 80.7% of our predictions correct.












**Sources Cited:**

[Harvard Business School](https://online.hbs.edu/blog/post/data-analytics-vs-data-science)

[Medium Article](https://medium.com/@springboard_ind/data-science-vs-data-analytics-how-to-decide-which-one-is-right-for-you-41e7bdec080e )
