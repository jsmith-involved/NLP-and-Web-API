# Project 3: Optimizing Qdoba's Marketing Strategies with Reddit API-driven Sentiment Analysis

### Problem Statement

As a data scientist, my firm, QWIK Restaurant Consulting, was hired by Qdoba to analyze their customer-run subreddit to gain valuable insights into their customer base and behaviors, particularly in comparison to their competitor, Chipotle. Our goal is to uncover key factors such as preferred menu items and sentiments expressed by customers. By doing so, this project aims to inform Qdoba on marketing strategies and deepen their understanding of their target audience.

### Data Dictionary 
| Feature | Type | Dataset | Description |
| --- | --- | --- | --- |
| created_utc | object | merged_dfs.csv | Time the subreddit post was created, represented in Unix Time |
| title | object | merged_dfs.csv | The title of the subreddit post |
| self_text | object | merged_dfs.csv | The text content of the subreddit post |
| subreddit | int | merged_dfs.csv | Subreddit each post belongs to. `0` for Chipotle; `1` for Qdoba |
| sort | object | merged_dfs.csv | Subreddit sort classification used to extract each post |

# Executive Summary

##### Background: 
I'm the creator of QWIK Restaurant Consulting, a firm comprising of data scientists specializing in analyzing customer sentiment through web API and natural language processing. Our current project involves providing guidance to Qdoba, leveraging our expertise in understanding customer feedback. Specifically, we're tasked with predicting posts from their customer community on the subreddit `r/qdoba` to gain insights into their clientele. Additionally, we're conducting a competitor analysis by developing a model capable of distinguishing between the customer bases of `r/Chipotle`, which shares similarities with Qdoba's customer community. The aim of this project is to deliver comprehensive insights on how customers perceive both companies, thereby creating an ideal marketing strategy that integrates feedback for Qdoba.

##### Methodology: 

Utilizing Reddit's PRAW API and natural language processing techniques, 4693 rows of data from both `r/qdoba` and `r/Chipotle` was collected. This process involved extracting 1000 posts per sort type (e.g., 'new' and 'rising').Duplicate rows and posts without text, indicating image-only content, were removed. Multiple NLP models were developed, exploring the optimal use of CountVectorizer (CVEC) or TFIDFVectorizer (TFIDF) to achieve the highest accuracy score for the best-tuned model.

Subsequently, questions pertaining to my problem statement were explored. An example of the type of questions is outlined below:

- Top unigrams for `r/qdoba` vs. `r/Chipotle`
- Top bigrams for `r/qdoba` vs. `r/Chipotle`
- Top trigrams for `r/qdoba` vs. `r/Chipotle`

<img src="images/chip_triwords.png" alt="Top 15 Trigrams in Chipotle" width="500">
<img src="images/qdoba_triwords.png" alt="Top 15 Trigrams in Qdoba" width="500">

##### Key Findings:
The model I found to perform the best at predicting posts belonging to which subreddit was a tuned Random Forest model utilizing TFIDF Vectorizer. The selected performed better than the baseline which had an accuracy score of only 60%. 

| Model |Train Score Accuracy | Test Score Accuracy |
| --- | --- | --- |
| **Random Forest TFIDF** | 99.34% | 97.44% |
| **KNN CVEC** | 99.34% | 96.48% |
| **Logistic Regression CVEC** | 98.58% |93.71% 
| **Naive Bayes TFIDF** | 84.70% | 82.00% 
| **Baseline** | 60% |

`Random Forest TDFIDF` only made 23 incorrect predictions out of 939 on the test set and had very few Type I and Type II errors. 
<img src="images/confusion_matrix.png" alt="Random Forest TFIDF Classification Results" width="500">


Ultimately, my firm discovered that customers are excited about Qdoba's tortilla soup return. I recommend Qdoba to leverage this excitement with a special reward points promotion because bonus points and giveaways are well-received. There's occasional mention of Taco Bell among customers, indicating a collaboration opportunity. Qdoba developing their own chicken al pastor could attract customers, as it is very popular amongst their biggest competitor, Chipotle, customer base. Reintroducing old recipes, like the previous salsa roja, could address concerns over recent changes.

##### Next Steps?
My firm will continue to monitor customer sentiment, allowing Qdoba to gauge the effectiveness of our recommendations and overall marketing plan for the company. We will track changes in customer perception and perform competitor analysis with other similar companies, such as Cava. Gathering more posts can further enhance the predictive model we found to be the best performing. Additionally, we will partner with Qdoba to leverage social media marketing, including initiating new email campaigns and social media promotions.
# Sources
[PRAW](https://praw.readthedocs.io/en/stable/index.html)

[Qdoba Subreddit](https://www.reddit.com/r/qdoba/)

[Chipotle Subreddit](https://www.reddit.com/r/Chipotle/)
