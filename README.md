# NLP Deception Detection
In this project, I developed of a method for automatically classifying Amazon reviews as real or fake.<br> The project has 3 stages - simple setup with basic pre-processing, addition of other pre-processing methods and finally addition of other features included in the input data.

## Dataset used
I used a subset of the corpus of Amazon reviews whch has been manaully analysed and annotated by Amazon. Available [here](https://s3.amazonaws.com/amazon-reviews-pds/readme.html).<br>
The input data contains the review text, label indicing whether the review it real or fake, rating, verified purchase, product category, product ID, product title and review title. The input data contains 21,000 reviews and is provided in `amazon_reviews.txt` file.

## Simple setup
The first stage was to train the classifier with basic pre-processing, converting data to vectors and feature vectors and using cross validation. With this setup, a Support Vector Machine classifier achieved the following results on test data:<br>
Precision: 0.6036<br>
Recall: 0.6036<br>
F Score: 0.6036<br>
Accuracy: 0.6036<br>

## Preprocessing improvement
Next, I improved the pre-processing of the data. The addition methods I considered were:
- stopwords removal
- punctuation removal
- tokens stemming
- tokens lemmatising
- n-grams


Additionally, I amended the feature dictionary to return weights instead of counts for the tokens.<br>
<br>
I obtained the best results by including the following methods: stemming, lemmatisation and feature weighing.
These amendments resulted in the following results on test data:<br>
Precision: 0.6363<br>
Recall: 0.6362<br>
F Score: 0.6361<br>
Accuracy: 0.6362<br>

## Looking beyond textual features of the review
The input data contained additional features which could be used by the classifier. When tested, the following features improved the classifier: <br>
- verified purchase
- product category
- product id

These amendments resulted in the following results:<br>
Precision: 0.8186<br>
Recall: 0.8150<br>
F Score: 0.8144<br>
Accuracy: 0.815<br>

## Conclusions
Below, I present a list of results I obtaned by running the model on the test dataset using the base functions, amended pre-processing and using additonal features. Each time the model is run, the results might be slightly different as the model splits the whole dataset into training and test at random.

| Metrics | Base functions | Additional pre-processing | Additional features |
| --- | --- | --- | --- |
| Precision | 0.6036 | 0.6363 | 0.8186 |
| Recall | 0.6036 | 0.6362 | 0.8150 |
| F1 Score | 0.6036 | 0.6361 | 0.8144 |
| Accuracy | 0.6036 | 0.6362 | 0.815 |

Overall, the improvement is significant, particularly when additional features not from the text of the review were included. The performance of the classifier started ar around 60% and improved to over 81%, an improvement of over 21%.<br>
<br>
The full list of improvements made:
- stemming of tokens
- lemmatisation of tokens
- feature weighing of vectorised tokens
- inclusion of 'Verified purchase' as a feature
- inclusion of 'Product category' as a feature
- inclusion of 'Product ID' as a feature

## Possible extensions of this project:
- Use of 'Review Title' as another feature. This would require the same pre-processing as 'Review Text'
- Experimentation with different parameters of the Support Vector Machine model
