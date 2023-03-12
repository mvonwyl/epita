# Introduction to NLP 01
# Lab 02

## Introduction

In this session, you will code a sentiment classifier on the IMDB sentiment dataset.

**Please, read the full assignment before starting.**

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments.
* Use [typing](https://realpython.com/python-type-checking/).
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...).
* Make your results reproducible (force random seeds values when necessary and possible).
* Packaging your functions and classes in separate python files make them more easily reusable.
* Don't hesitate commenting in details part of the code you consider complex or hard to read.

Do not hesitate contacting me if you have any question, but please don't wait until the last moment.

## The dataset **(3 points)**

The IMDB sentiment dataset is a collection of 50K movie reviews, annotated as positive or negative, and split in two sets of equal size: a training and a test set. Both set have an equal number of positive and negative review. The dataset is available on several libraries, but we ask that you use the HuggingFace [datasets](https://huggingface.co/datasets/imdb) version. Follow their [tutorial](https://huggingface.co/docs/datasets/load_hub) on how to use the library for more details.

Download and look at the dataset, and answer the following questions.
1. How many splits does the dataset has? (1 point)
2. How big are these splits? (1 point)
3. What is the proportion of each class on the supervised splits? (1 point)

## Naive Bayes classifier **(13 points)**

Implement your own naive Bayes classifier (the pseudo code can be found in the slides or the [book reference](https://web.stanford.edu/~jurafsky/slp3/)) or use [one provided by scikit-learn](https://scikit-learn.org/stable/modules/naive_bayes.html#multinomial-naive-bayes) combined with a [CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html).

Go through the following steps.
1. (2 points) Take a look at the data and create an adapted preprocessing function with at least:
   1. Lower case the text.
   2. Replace punctuations with spaces (you can use `from string import punctuation` to ease your work). Think that maybe not all punctuations should be removed or replaced.
2. (4 points) Implement your own naive Bayes classifier from scratch. The pseudo code can be found in the slides or the [book reference](https://web.stanford.edu/~jurafsky/slp3/).
3. (3 points) Implement a naive Bayes classifier using scikit-learn.
   * Use a scikit-learn [Pipeline](https://scikit-learn.org/stable/modules/compose.html#pipeline) with a [CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html) and [MultinomialNB](https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.MultinomialNB.html) classifier. You can use other 
4. (1 point) Report the accuracy on both training and test set, for both your implementation and the scikit-learn one.
5. (1 point) Most likely, the scikit-learn implementation will give better results. Looking at the documentation, explain why it could be the case.
6. (1 point) Why is accuracy a sufficient measure of evaluation here?
7. (1 point)Using one of the implementation, take at least 2 wrongly classified example from the test set and try explaining why the model failed.
8. **\[Bonus\]** What are the top 10 most important words (features) for each class? (bonus points)
   1. Look at the words with the highest likelihood in each class (if you use scikit-learn, you want to check `feature_log_prob_`).
   2. Remove stopwords (see [NLTK stopwords corpus](https://pythonspot.com/nltk-stop-words/)) and check again.
9. **\[Bonus\]** Play with scikit-learn's version parameters. For example, see if you can consider unigram and bigram instead of only unigrams.

## Stemming and Lemmatization **(4 points)**

The two notebooks in this directory give examples on how to run stemming and lemmatization using NLTK or spaCy. Pick either stemming or lemmatization, and add the operation to your pretreatment.

1. (2 points) Add stemming **or** lemmatization to your pretreatment.
2. (1 point) Train and evaluate your model again with these pretreatment.
3. (1 point) Are the results better or worse? Try explaining why the accuracy changed.

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code **before the 31st of March (deadline is Thursday 30th at midnight)**. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report. Please send an email to `marc.von-wyl` at `epita` dot `fr`, when the project is ready to be graded.

The assignment will be evaluated on the following criteria

* A report answering the questions above, describing your technical choices, and analysing your results.
* The quality of your code (modularity, efficiency, comments, coding standards).

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments
* Use typing
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...)
* Make your results reproducible (force random seeds values)
* Don't hesitate commenting in details part of the code you consider complex or hard to read

Provide a `README.md` file with 
* A short description of the project
* A description of the file/module architecture

