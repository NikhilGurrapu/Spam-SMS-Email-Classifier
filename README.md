# Spam-SMS-Email-Classifier

### A classifier which can classify an SMS and E-mail as Spam or Not Spam

To build the model we performed the following steps:

### Data Cleaning:
Removing all the unwanted rows and columns from our data so that it gets easier to analyze it.
### Exploratory Data Analysis:
Analyzing our data to find the trends in it and visualizing it for better understanding.
### Data Reprocessing:
After getting a better understanding about our data, we processed our data to provide more reliable data points for our model. This step helps us to further improve our model.
### Model Building and Testing:
Then we built the model, tested compared the results with various classification algorithms and then improved on it accordingly.

### Our data is in the form of CSV and has 5 columns.

As you can see, the last 3 columns (unwanted,2,3,4) have only 50,12,6 non-null values. This means these columns will not help us in our data analysis. Where as the first 2 columns have 0 non-null values.
V2 Contains the corpus sms and email text samples to which v1 describes as spam or ham (not spam). We have to process the first 2 columns and create more data points for accurate classification.

Since the first 2 columns are the only columns we need we will drop the remaining columns. After which we will check for duplicate values. We found out that there are 403 duplicate values in our data set, so we drop them and this is what we get.

Since we checked for null values before and we know there are no null values in the first 2 columns, we don’t need to check for them again. Now we will perform EDA

## EDA
First we found the divide of data in our model, i.e How many messages belong to the spam and ham category respectively messages which are not spam. As we can see, there’s a clear imbalance of data in our dataset. So while building our model we have to give preference to precision over accuracy as we need more precise classification.

For further data analysis we needed more data points, so we processed our data to find out the number words,sentences and characters in each message of our data set.

With this new data, we performed some data analysis
### Histogram of number of characters the number of messages:
Red color indicates spam and blue indicates ham. From this we can concur that usually spam messages have a higher number of characters. And only a few not spam messages. Around 180-190 spam messages have 170+ characters whereas around 20-30 ham messages have 180-190 characters. Number of characters can be used to improve our model.
### Histogram of number of words the number of messages:
The data shows a similar relationship like the one with the number of characters. However there are some outliers.
### Corelation heatmap:
With this heat map we can conclude that
The number of characters, words and sentences all have a positive corelation with the target (spam or not spam)
Number of sentences has the lowest corelation of 0.27
Number of characters has the highest corelation

After this analysis we found out that sms/emails with higher number of characters are more likely to be scam. Same goes for the number of words, however there are some outliers in this case which can hinder our classification. So we will most likely use number of characters as a parameter for classification.

## Model Building , evaluation and improvement
* We decided to go with the Naive Bayes algorithm for our prediction
* We decided to go with it as after research we found out this algorithm usually provides the best results in text classification
* We first converted our text into vectors using countvectorizer and TFIDF vectorizer
* Then we ran the values in 3 different Naive Bayes algorithms(GaussianNB, MultinomialNB, BernoulliNB) and tested which provided the best precision and here are the results in the form of a data frame.

### As we can see TFIDF provided better precision and accuracy all around however we can still improve the model.

* So we decided to run the TFID vectorizer again but this time we decided to vectorize our data depending upon the top 3000 most used words in our data.
* As you can see, our accuracy increased by  0.02 points in the multinomialNB algorithm. Since its accuracy is sufficient and it has a 100% precision score we will go with this algorithm.
* As we can see TFIDF provided better precision and accuracy all around however we can still improve the model.
* So we decided to run the TFID vectorizer again but this time we decided to vectorize our data depending upon the top 3000 most used words in our data. 
