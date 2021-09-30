# Project 3 - Reddit NLP Classification
## Overview

Financial scams in Singapore have seen increases in the recent years, especially as more and more transactions migrate online. In 2020, cases reported rose 65.1% up to 15,756 total cases, from 9,545 cases in the previous year. With cyber crime on the rise and elderly individuals being the most frequent target, there is an onus to try to protect them as much as possible.

A division of our Government, Classifying Spam Agency of Singapore, wants to work with us to try to develop a filter that specifically targets financial updates. Their issue is two fold:

*    The recent rise in the multitude of online opinions on the best financial investments, such as meme stocks, cryptocurrency
*    The increase in mobile investment apps easing the path to investing, as well as allowing the masses access to such investing tools as options trading and leveraging

This has led to an increase in the more vulnerable classes losing their life savings on uneducated and risky bets.

The goal is to try to create a filter that can help label financial news for this division, CSA:

1.    To flag the type of news that comes out, if it involves trendy financial topics
2.    To help provide news that is still balanced and conservative to help educate the masses on investments in a gainful manner
3.    To prevent the topics of meme stocks, cryptocurrency, and such news from flooding the market and as a consequence, prevent scams related to such topics

We will scrape two large, popular subreddits, r/personalfinance and r/wallstreetbets, with the aim of training a filter to flag posts that are too focused on trending financial news and flag them for review.

##  Model Considerations

Due to the nature of the task and the model, we will be trying to reduce the number of type 2 II errors as much as possible. Allowing false positives through, mean that we will have to look over a few more posts/articles to ensure that they are inline with expectations.

However, allowing false negatives through, may unduly influence more of the vulnerable classes into detrimental transactions, which is expressly what we are trying to prevent. Fixing these situations would be much more difficult and much costlier, and may even be impossible.

Hence, for the purposes of this project, we will looks to maximise the Sensitivity over the Specificity.

#### Initial Hypothesis

At first glance, these two subreddits are both financially related, and we would expect there to be a fairly comprehensive coverage of financial terms. However, the two do have very different crowds, particularly when considering only the posts that are being made, and not so much the comments.

#### r/personalfinance

    Posters here to be more beginners seeking financial help
    Topics would tend to include issues more to do with daily life or saving for retirement:
        Individual Retirement Accounts (IRAs)
        Debt (House, cars,...)
        Budgeting
        Sudden Windfalls

#### r/wallstreetbets

    Posters here tend to be people who are more in tune with current financial trends, even if they are not actually financially savvy
    Posts tend to include topics related to stock market investing and feature many meme phrase, and will often be laser focused on the latest trends:
        Common stock tickers recently include: Gamestop(GME), AMC Theatres(AMC)
        Common trends in recent history include: Robinhood & investing as an individual, short selling & options trading
        They will also tend to regard investing with a shorter-term investment window (as opposed to til retirement for r/personal finance)

####  Stop words

Stopwords will included the NLTK English Stopwords, as well as the following:
['personalfinance', 'personal', 'finance', 'wallstreetbets', 'bets', 'wallstreet', 'wsb', 'wall street', 'gme', 'gamestop', 'game stop', 'amc', 'amc entertainment', 'tmc', 'ast', 'robinhood']

---

## Datasets

* [`reddit.csv`](.reddit.csv): Raw Reddit data scraped and combined
* [`reddit_clean.csv`](.reddit_clean.csv): Cleaned Reddit data for modelling

---

## Data Dictionary

#### reddit_clean

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**is_wallstreetbets**|*int*|reddit_clean|Whether the post is from wallstreetbets (1 for yes, 0 for no)|
|**word_sum**|*object*|reddit_clean|All the words in the post (Title + selftext)|
|**title**|*object*|reddit_clean|Title of the post|
|**selftext**|*object*|reddit_clean|Body text of the subreddit post|
|**words_clean**|*object*|reddit_clean|Tokenized words from the whole post in a single string|
|**words_lem**|*object*|reddit_clean|Lemmatized words from the whole post in a single string|
|**words_stem**|*object*|reddit_clean|Stemmed words from the whole post in a single string|
|**word_count**|*int*|reddit_clean|Number of words in the title and selftext|

#### reddit

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|*object*|reddit|Subreddit the post belongs to (wallstreetbets/personalfinance)|
|**title**|*object*|reddit|Title of the subreddit post|
|**selftext**|*object*|reddit|Body text of the subreddit post|
|**retrieved_on**|*int*|reddit|Date of the post in UTC epoch (e.g. 1632293155)|

---

## Analysis

Data was scraped from r/personalfinance and r/wallstreebets and cleaned. For the purpose of the project, titles and selftext were combined to include as much text from the post as was possible, before being split into tokenized, lemmatized, and stemmed words.

These three sets were tested through a Count Vectorizer and TF-IDF, in a Multinomial Naive Bayes Model. Due to the small difference between the three word groups, models moving forward were only tested on the tokenized words unless they hit a specific threshold.

Models tested included:
* Multinomial Naive Bayes
* Random Forest
* Extremely Randomized wallstreebets
* ADA Boost

---

## Conclusions

####  Model Efficacy

Our final model was a Multinomial Naive Bayes model, with stemmed words, count vectorized with the following parameteres:

Max Features : 5000 N Gram range: 1, 1 Stop Words: English + a custom stop list

Overall, the model performed very well, identifying posts with a 95.12% accuracy, and when the threshold was adjusted, sensitivity was raised to 94.7%. However, it ultimately let 2 posts through that should be checked. Further steps to improve the model have been listed further below.

#### Model Takeaways

As hypothesised at the start, the difference between the two subreddits held fairly consistent, and where it did not, misclassification occurred. In general, posts from r/personalfinance did post more content related to long-term investing for retirement, general advice on budgeting, and maintaining a responsible, sustainable financial lifestyle. All of which are related to the type of content that we would like to pass unchecked.

In contrast, r/wallstreetbets contained many more financially specific terms, which though not exactly the ones initially suspected, were along the lines of what was hypothesised. Further reinforcing this, was the general rule, that the words that most indicated which subreddit the post belonged to were overwhelmingly words from r/wallstreetbets. This seems to indicate and agree with the initial hypothesis that there is a specific type of language and lingo that persists in r/wallstreetbets.

###  Further Steps

#### Titles

Improvements to the model could include examining whether titles need to be weighted differently. Titles are often summaries and can contain some of the most important words, and also have the least stopwords. Weighting just the titles differently may give us a better indicator for prediction

#### Word Context

The models tested in this project assumed that the words were independent of each other and that context and semantics were unrelated. However, we know this to not be true and one further direction to take the project would be to include context and semantics into the weighting of the words.

#### Metadata

While we did not include anything related to metadata, a model that includes word count may help in both differentiating, as well as in actually segregating financial news spam. We have already noted that r/personalfinance has a higher word count on average, and this may be partly due to the nature of the posts. Posts seeking or giving advice tend to have more details and more steps, than posts that expound a certain action.
