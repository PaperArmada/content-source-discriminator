# Project 3 - Web APIs & NLP


### Problem Statement

As a team at a small company, we are seeking to: 
    1. Establish a process to automatically recommend labels for written content by subject matter for the company's internal knowledge base

### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**author**|object|all|Reddit handle of the post's author|
|**title**|object|all|Reddit post title|
|**selftext**|object|all|Reddit post text content|
|**subreddit**|object|all|Name of the Subreddit from where the post was retrieved|
|**score**|int|all|Number of upvotes the post received at the time of retrieval|
|**created_utc**|int|all|Datetime value for when the post was created|

### Summary of Analysis

#### Objective
Specifically we were seeking to establish: 
    - Can we reliably recommend labels for bodies of text based on their contents

#### Data
Data was retrieved from Reddit.com using the Pushshift API. A minimum of 1,000 unique posts were retrieved from the r/TalesFromTechSupport, r/TalesFromRetail, and the r/ITCareerQuestions subreddits.

#### Methodology

##### Data Collection

##### Cleaning
1. Checked for Null values and unusual data types. 
2. Target variable binarized and post title and selftext cleaned of any html content.

##### Processing
1. Sample data separated into training data (for both title and selftext) and test data
2. A pipeline was created to count vectorize the text and then feed it through a logistic regression model
3. The model was then tuned and improved using multiple passes through GridSearchCV
4. Top performing parameters were used to evaluate the model relative to a third set of data

### Conclusions & Recommendations

#### Conclusions:
The model we produced does an excellent job of categorizing bodies of text according to our target content. With our original data set comparisons between r/TalesFromTechSupport and r/TalesFromRetail we saw categorization accuracy of 96.3% with 0.36% standard deviation, and with the follow on comparison between r/TalesFromTechSupport and r/ITCareerQuestions we saw an accuracy of 97% with 0.7% standard deviation.

#### Recommendations:
1. We have demonstrated the ability to effectively categorize written content relative to established target types. We now need to create models based on company content to capture categories of interest, and develop a system for passing the corpus of the company through the system for labeling.   