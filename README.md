# Predicting Sentiment of Movie Reviews

This analysis utilizes the Rotten Tomatoes movie review dataset, and uses the available movie reviews to predict whether a given movie review is rated:
* 0 - negative
* 1 - somewhat negative
* 2 - neutral 
* 3 - somewhat positive
* 4 - positive

## Dataset
- [Sentiment Analysis on Movie Reviews](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews) 

## Data Overview

The training dataset includes 156060 rows of data, with multiple rows parsing each review into sub-phrases of varying lengths. The dataset was consolidated to parse out the longest phrase for each review, narrowing the dataset down to 8530 unique rows.

The data was then cleaned as follows:
- All non alphanummeric characters are removed
- Reviews are all made lower-case
- Spaces and break characters are removed
- Additional stop-words are included in the stock stop-words dictionary, and removed
- The words "film", "movie" and "one" are removed, as they appear in the top 10 most frequently used words for each sentiment rating
- Reviews are re-built with lemmatied words

## Data Analysis and Evaluation
Data was analyzed using the following models:
- Multinomial Bayes
- Random Forest
These models resulted in severe overfitting and poor results on test data (with high results on the train data).

- Logistic Regression
- KNN
These models resulted in both overfitting and poor results on train and test data.

<br>Data was then analyzed using RNN:
- Sequential models (LSTM)
- Sequential models (GRU); sacrificing some of the benefits from remembering longer strings (LSTM), Gated Recurrent Unit (GRU) will only take a subset of information into the next layer based on what it deems to be significant to the model 
- Sequential models (Word2Vec); adjusting word vectors based on existing language syntax captured in the Word2vec model

Models were updated with dropout, early stopping and regularization to minimize overfitting.

<br>None of the models yielded satisfactory results and did not perform well on test data.

## Conclusions and Next Steps
It will be worth trying the following in order to continue finding improvements in model performance:
- TFIDF and Word2Vec in Multinomial, Logistic, KNN and Random Forest models
- Continued tweaking within RNN
- Removing a different subset of stop words or not removing stop words, to better capture language syntax and complex phrases
- Attempting longer n-grams throughout


