# Introduction to Natural Language Processing 1 Lab03

## Introduction

In this session, you will code the first part of our project: a sentiment classifier. Where you will use and compare several classifiers on the IMDB sentiment dataset.

## The dataset

The IMDB sentiment dataset is a collection of 50K movie reviews, annotated as positive or negative, and split in two sets of equal size: a training and a test set. Both set have an equal number of positive and negative review. The dataset is available on several libraries.
* HuggingFace [datasets](https://huggingface.co/docs/datasets/)
* [TorchText](http://pytorch.org/text/master/datasets.html?highlight=imdb#torchtext.datasets.IMDB)
* [Keras](https://keras.io/api/datasets/imdb/)

Start by downloading the dataset with any of the resources above and looking at the data.

## First two classifiers

Implement the two following classifiers.
1. A naive Bayes classifier
2. A logistic regression based on hand-made features

### Naive Bayes classifier

Start by implementing a very simple version, then add pretreatment methods seen in class such as stemming, lemmatization, or stop-word removal to see if it improves performances. Implement also the binary version which only check the presence of a work and doesn't count them.

### Logistic regression

Use the following features to start with.
* 1 if "no" appear in the doc, 0 otherwise
* The count of first and second pronouns in the document
* 1 if "!" is in the document, 0 otherwise
* log(word count in the document)
* Number of words in the document which are in the positive lexicon
* Number of words in the document which are in the negative lexicon

To generate your positive and negative lexicons, you can use the resources provided by [VADER sentiment](https://github.com/cjhutto/vaderSentiment). Look for the `vader_lexicon.txt` and, for example, consider positive word if they score above a certain threshold and negative word if they score below a certain threshold. Feel free to use another lexicon if you find one.

You don't need to code your own logistic regression from scratch. You can simply use [scikit-learn implementation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html), for example.


### Evaluation measure

Since the classes are balanced, you can use accuracy as an evaluation measure.


## Project

This is the first part of the project of this module. You are expected to code both models described above and also
* For the naive Bayes model
  * Try with and without pretreatment (especially stemming or lemmatization), and discuss the improvement (if any).
  * Compare counting words with just checking their presence (binary naive Bayes)
  * With your best model, provide examples of wrongly classified samples, as well as explanations on why these examples were attributed to the wrong class.
* For the logistic regression
  * Try with and without pretreatment (especially stemming or lemmatization), and discuss the improvement (if any).
  * Observe the data and add at least 2 more features (justify your choices with observations).
  * Try with and without regularization, and document your observations.
  * With your best model, provide examples of wrongly classified samples, as well as explanations on why these examples were attributed to the wrong class.
  
The second part of the project will be presented during the next lab session.

## Evaluation

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
* How to install the dependencies, run the code, and reproduce your results
  * Provide at least a `requirements.txt` or a conda yaml file, and the minimum python version to run your code.

Please send the final project in archived zip or tar file before the 14th of October (last chance Wednesday at midnight).