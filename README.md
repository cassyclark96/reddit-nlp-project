# Reddit-NLP-Project

## Table of Contents
- [Objective](#Objective)
- [Data](#Data)
- [Executive Summary](#Executive-Summary)
- [Findings](#Findings)
- [Next Steps](#Next-Steps)

---

## Objective

The objective for this project was to choose two different subreddits and use the [Pushshift API](https://github.com/pushshift/api) to collect posts from the two subreddits and use NLP to create a model that would predict which subreddit posts came from.

---

## Data

The subreddits I chose were [Shower Thoughts](https://www.reddit.com/r/Showerthoughts/) and [Today I Learned](https://www.reddit.com/r/todayilearned/). I chose these two subreddits because I knew they would have some similarities and differences that I thought would be interesting to test out in a natural language processing machine.

---

## Executive Summary

Reddit is a popular social media platform that offers a sense of community, conversation, and connection. An individual who has a reddit can follow various subreddits based on their interests. I chose the subreddit Shower thoughts where people post about random thoughts they have had like ["Caprese salad seems fancy but it’s just pizza with no dough and less steps."](https://www.reddit.com/r/Showerthoughts/comments/iy3q7l/caprese_salad_seems_fancy_but_its_just_pizza_with/). The other subreddit I chose was Today I Learned where people post interesting uncommon facts they just learned similar to ["[TIL] Tater tots were invented in 1953 to use up leftover slivers of cut-up potatoes"](https://www.reddit.com/r/todayilearned/comments/ixzeia/til_tater_tots_were_invented_in_1953_to_use_up/). Posts like these were ran through a Natural Language Processing Machine to see if the machince could predict which subreddit the post came from.

[Natural Language Processing (NLP)](https://medium.com/@ChrisKnightcms/natural-language-processing-offers-great-business-benefits-f450593e1089) has numerous benefits and uses. It can run through good and bad reviews for movies, restaurants, stores, etc. It can help companies converse with their customers through chatbots on their website. We even hear NLP in products like Siri, Alexa, and Google Home. NLP is so important for the future of businesses and technology because it provides a way to retrieve valuable information in a time efficient manner in a world that is ever evolving with technological advances.

To start the natural language process, requests were made to the Push Shift API to pull posts from Shower Thoughts and Today I Learned with the goal being at least 5,000 posts from each subreddit. Once I had attained more than enough posts I moved on to exploratory data analysis and data cleaning. The steps I took for data cleaning included removing all puncutaion and labeling the subreddits as 1 (Shower Thoughts) and 0 (Today I Learned). A post length count and word count were collected for each subreddit to compare the difference in counts between the two subreddits. 

subreddit | post_length | post_word_count|
----------|-------------|----------------|
0         | 159.748500  |   27.992726    |
1         | 85.388889   |   15.691847    |


All of the posts were then put through a Count Vectorizer that would return the counts of every word that appeared in any post. The standard english stop words (words to ignore/pull out) as well as the words 'shower', 'thought', 'til', 'today', and 'learned' were set up as the stop words parameter for the count vectorizer to ignore. The additional words were added as a way to try and eliminate any bias towards a subreddit that might contain the words of the actual subreddit the post originated from. The most common 15 and least common 15 words were then looked at as well as common and uncommon word pairings. Finally, a sentiment analysis using the [sentiment vader model](https://www.nltk.org/api/nltk.sentiment.html#nltk.sentiment.vader.SentiText) was conducted on the posts to see if there was a trend of positive versus negative posts in the subreddits.

subreddit | neg | neu | pos |
----------|-----|-----|-----|
0         | 0.066721 | 0.863174 | 0.069555 |
1         | 0.078641 | 0.842359 | 0.078210 |


---

## Findings

Two different classification models were performed on the posts which included a [Multinomial Naive Bayes Model](https://scikit-learn.org/stable/modules/naive_bayes.html?highlight=multinomial%20bayes) and a [Logisitic Regression Model](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html?highlight=logistic%20regression#sklearn.linear_model.LogisticRegression). Both models were tested alongside a count vectorizer and a [tf-idf](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html). The multinomial bayes with count vectorizer had an accuracy score of 0.833 and with tf-idf had an accuracy score of 0.824. The logistic regression model with count vectorizer had an accuracy score of 0.834 and with tf-idf had an accuracy score of 0.818.

---

## Next Steps 

The next steps for this project would be to pull even more posts from each subreddit and train the nlp models even more so that the model can produce a higher accuracy score on differentiating between the two subreddits. 
