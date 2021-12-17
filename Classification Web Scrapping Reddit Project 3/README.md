# Project 3: Classification of 'jobs' and 'forhire' subreddits

## Problem Statement 
The goal of this project is to build a binary classification model to predict if a post on reddit belongs to the "jobs" or "forhire" subreddit. The model will be considered successful if both the F1 score and sensitivity are above 90%.

Additionally, the project aims to provide insights on the key words and phrases that people use when discussing jobs on reddit, with the stakeholders being data science peers, job seekers and job posters

## Executive Summary
Reddit is a popular social news, content, and discussions website where posts are organised according to subject into user-created 'subreddits'. Members submit content (such as images, texts, and links) to subreddits, which can then be voted on and commented by other members, creating an internet community of sorts around specific themes. In this project, I examined posts from two subreddits - [**r/jobs**](https://www.reddit.com/r/jobs/) and [**r/forhire**](https://www.reddit.com/r/forhire/).

<img src='datasets/rjobsCapture.jpg' width = 700 align = center>
<center><font size=2 color='grey'>(Fig 1. The frontpage of r/jobs as of 9pm, 22 Sep 2021.)</font></center>


<img src='datasets/rforhireCapture.jpg' width = 700 align = center>
<center><font size=2 color='grey'>(Fig 2. The frontpage of r/forhire as of 9pm, 22 Sep 2021.)</font></center>

As both subreddits are related to employment, there is potential for misclassification with both groups created around a year apart. 

The differences in r/jobs vs r/forhire include the size of the communities (r/jobs is more than twice the size of r/forhire at 577k vs 246k) with the nature of the posts on r/jobs appear mostly related to queries for career advice. In contrast, most posts on r/forhire are related to jobs posting by either job seekers or job providers.

The objective of this project is to create the best classification model to identify Reddit posts, with the goals as stated in the problem statement. For this project, the data has to be gathered manually using the Pushshift API.

For the training data set, a total of 1,000 posts were each gathered from the r/jobs subreddit and r/forhire subreddit. As usable language data can both be found in the post title and post content, they were merged to create new variable. For the purpose of this project, models comprising of combinations of the following are considered:

    - Pre-processing: 1) Tokenizer        2) Lemmatization
    - Transformer:    1) Bigrams          2) Sentiment Analysis
    - Model:          1) Random Forest    2) Voting classifier

After assessing both models, the final model is a voting classifier that uses a random forest classifier, multinomial naive Bayes, and support vector classifier to predict the subreddit based on the text in a given post. This model has an F1 score of 96% and a recall score of 97%, and would therefore be considered successful. 

Recommendations to further improve the model include:
    
- Expand our model to other subreddits that concern employment such as r/careeradvice to increase the corpus of words
- Get more data from other employment resources (e.g. LinkedIn, JobStreet etc.)

## Findings

The final model is a voting classifier that uses a random forest classifier, multinomial naive Bayes, and support vector classifier to predict the subreddit based on the text in a given post. This model has an F1 score of 96% and a recall score of 97%, and would therefore be considered successful.

<img src='datasets/ModelScoreCapture.jpg' width = 700 align = center>
<center><font size=2 color='grey'>(Fig 1. The frontpage of r/jobs as of 9pm, 22 Sep 2021.)</font></center>

## Conclusion & Recommendations

The goal of this project was to build a binary classification model that could be used to predict if a post on reddit belongs to r/jobs or r/forhire which was achived based on the voting classifier listed above.

However, these scores are similar to those of the default Random Forest model with countvectorizer and no hyperparameter with both models having a high tendency to overfit the train data from the train_test_split. Though we have selected the model with the least drop in score when testing it on test data, the drop is still rather significant. Thus, the hyperparameter optimisation which was time-consuming only achieved very modest gains in the scores.

One reason for this could be that the moderators of the r/forhire do review posts that do not meet the specifics set in the Rules & Guidelines for r/forhire which would result in posts that are not related to job postings being removed regularly and thus resulting in the r/forhire posts being specific to job postings only.

Thus, the work done by the moderators might have resulted in the default Random Forest model being able to predict accurately if a post on reddit belongs to r/jobs or r/forhire.