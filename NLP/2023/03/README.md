# Introduction to Natural Language Processing 01
# Lab 03

## Introduction

The project is a continuation of we started on the second lesson. We will train a logistic regression classifier on manually extracted features.

## Features (6 points)

For every given text, we want to generate a vector with the features seen in class.

**(6 points)** Code the following features:
* 1 if "no" appear in the doc, 0 otherwise
* The count of first and second pronouns in the document
* 1 if "!" is in the document, 0 otherwise
* Log(word count in the document)
* Number of words in the document which are in the positive lexicon
* Number of words in the document which are in the negative lexicon

For positive and negative lexicons, you can use the resources provided by [VADER sentiment](https://github.com/cjhutto/vaderSentiment). Look for the `vader_lexicon.txt` and, consider positive word if they score above a certain threshold (for example 1) and negative word if they score below a certain threshold (for example -1). Feel free to use another lexicon if you find one.

Don't forget to use a similar pre-treatment as the one you used for the previous lab.
**Note that the words in the lexicon are lemmas. So think about lemmatizing the text before hand.**

## Logistic regression

### Scikit-learn (4 points)

* **(2 points)** Train a classifier using the [scikit-learn implementation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) of logisitic regression.
* **(1 point)** Compute the accuracy on the train and test set.
* **(1 point)** Look the coefficients learned by the classifier (`coef_` attribute). What does it tell you about the features and how they influence the decision?
* **\[Bonus\]** Play with the parameters and see how they influence the output (for example, see what happens to the coefficients if you remove the default L2 penalty).

### PyTorch





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

This project provides 8 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.
