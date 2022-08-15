# Introduction to NLP 01
# Lab 02

## Introduction

In this session, you will code the first part of our project: a sentiment classifier. Where you will use and compare several classifiers on the IMDB sentiment dataset.

**Please, read the full assignment before starting.**

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments.
* Use [typing](https://realpython.com/python-type-checking/).
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...).
* Make your results reproducible (force random seeds values when necessary and possible).
* Packaging your functions and classes in separate python files make them more easily reusable.
* Don't hesitate commenting in details part of the code you consider complex or hard to read.

Do not hesitate contacting me if you have any question, but please don't wait until the last moment to do so.

## The dataset **(3 points)**

The IMDB sentiment dataset is a collection of 50K movie reviews, annotated as positive or negative, and split in two sets of equal size: a training and a test set. Both set have an equal number of positive and negative review. The dataset is available on several libraries, but we ask that you use the HuggingFace [datasets](https://huggingface.co/datasets/imdb) version. Follow their [tutorial](https://huggingface.co/docs/datasets/load_hub) on how to use the library for more details.

Download and look at the dataset, and answer the following questions.
1. How many splits does the dataset has? (1 point)
2. How big are these splits? (1 point)
3. What is the proportion of each class on the supervised splits? (1 point)

## Naive Bayes classifier **(9 points)**

Implement your own naive Bayes classifier (the pseudo code can be found in the slides or the [book reference](https://web.stanford.edu/~jurafsky/slp3/)) or use [one provided by scikit-learn](https://scikit-learn.org/stable/modules/naive_bayes.html#multinomial-naive-bayes) combined with a [CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html).

Go through the following steps.
1. Create a pretreatment function which (2 points)
   1. Lower case the text.
   2. Remove punctuation (you can use `from string import punctuation` to ease your work).
2. Train a naive Bayes classifier on the training set. (4 points)
3. Report the accuracy on both training and test set. (1 point)
4. Why is accuracy a sufficient measure of evaluation here? (1 point)
5. **\[Bonus\]** What are the top 10 most important words (features) for each class? (bonus points)
   1. Look at the words with the highest likelihood in each class (if you use scikit-learn, you want to check `feature_log_prob_`).
   2. Remove stopwords (see [NLTK stopwords corpus](https://pythonspot.com/nltk-stop-words/)) and check again.
6. Take at least 2 wrongly classified example from the test set and try explaining why the model failed. (1 point)

## Stemming and Lemmatization

The two notebooks in this directory give examples on how to run stemming and lemmatization using NLTK or spaCy. Pick either stemming or lemmatization, and add the operation to your pretreatment.

1. (2 points) Add stemming or lemmatization to your pretreatment.
2. (1 point) Train and evaluate your model again with these pretreatment.
3. (1 point) Are the results better or worse? Try explaining why the accuracy changed.

## Theoritical questions **(5 points)**

The following questions have been seen during the course and can be found on the support and references. Don't copy-paste what is written in the course, answer with your own words.

Answer the following questions.
1. (2 points) Explain with your own words, using a short paragraph for each, what are:
   * Phonetics and phonology
   * Morphology and syntax
   * Semantics and pragmatics
2. (1 point) What is the difference between stemming and lemmatization?
   * How do they both work?
   * What are the pros and cons of both methods?
3. (1 point) What are the two assumptions made by the Naive Bayes algorithm?
4. 1(point) On logistic regression:
   * How does stochastic gradient descent work?
   * What is the role of the learning rate?
   * Will it always find the global minimum (for logistic regression)?
