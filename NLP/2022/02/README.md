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

## Naive Bayes classifier **(9 points)**

Implement your own naive Bayes classifier (the pseudo code can be found in the slides or the [book reference](https://web.stanford.edu/~jurafsky/slp3/)) or use [one provided by scikit-learn](https://scikit-learn.org/stable/modules/naive_bayes.html#multinomial-naive-bayes) combined with a [CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html).

Go through the following steps.
1. (2 points) Take a look at the data and create an adapted preprocessing function which at least:
   1. Lower case the text.
   2. Remove punctuation (you can use `from string import punctuation` to ease your work).
2. (4 points) Implement and train a naive Bayes classifier on the training data. Either:
   * Code your own classifier following the algorithm given in class.
   * Or use a scikit-learn [Pipeline](https://scikit-learn.org/stable/modules/compose.html#pipeline) with a [CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html) and [MultinomialNB](https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.MultinomialNB.html) classifier. (Recommended)
3. (1 point) Report the accuracy on both training and test set.
4. (1 point) Why is accuracy a sufficient measure of evaluation here?
5. **\[Bonus\]** What are the top 10 most important words (features) for each class? (bonus points)
   1. Look at the words with the highest likelihood in each class (if you use scikit-learn, you want to check `feature_log_prob_`).
   2. Remove stopwords (see [NLTK stopwords corpus](https://pythonspot.com/nltk-stop-words/)) and check again.
6. Take at least 2 wrongly classified example from the test set and try explaining why the model failed. (1 point)

## Stemming and Lemmatization **(4 points)**

The two notebooks in this directory give examples on how to run stemming and lemmatization using NLTK or spaCy. Pick either stemming or lemmatization, and add the operation to your pretreatment.

1. (2 points) Add stemming or lemmatization to your pretreatment.
2. (1 point) Train and evaluate your model again with these pretreatment.
3. (1 point) Are the results better or worse? Try explaining why the accuracy changed.

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report.

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

Please send the final project in archived zip or tar file before the 7th of October (last chance Wednesday at midnight).

This project provides 16 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 6th of October 2022 at midnight. Thought is is advised to send them progressively.
