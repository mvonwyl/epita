# Introduction to Natural Language Processing 01
# Lab 03

## Introduction

The project is a continuation of we started on the third lab. We will try beating the results we obtained with naive Bayes using the FastText library.

## FastText **(9 points)**

Use the [FastText library](https://fasttext.cc/docs/en/support.html) to train and test a classifier.

Go through the following steps.
1. (2 points) Turn the dataset into a dataset compatible with Fastext (see the _Tips on using FastText_ section a bit lower).
   * For pretreatment, only apply lower casing and punctuation removal.
2. (2 points) Train a FastText classifier with default parameters on the training data, and evaluate it on the test data using accuracy.
3. (3 points) Use the [hyperparameters search functionality](https://fasttext.cc/docs/en/autotune.html) of FastText and repeat step 2.
   * To do so, you'll need to [split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html) your training set into a training and a validation set (don't forget to shuffle your dataset).
   * Let the model search for 5 minutes (it's the default search time).
4. (1 points) Look at the differences between the default model and the attributes found with hyperparameters search. How do the two models differ?
   * Check the _Tips on using FastText_ section for a bit of help).
   * Only refer to the attributes you think are interesting.
   * See the _Tips on using FastText_ (just below) for help.
5. (1 point) Using the tuned model, take at least 2 wrongly classified examples from the test set, and try explaining why the model failed.
6. (Bonus point) Why is it likely that the attributes `minn` and `maxn` are at 0 after an hyperparameter search on our data?
   * Hint: on what language are we working?

### Tips on using FastText

FastText is not exactly documented in details, so you might run into a few problems. The following tips can be useful.

#### Training file format

Training a FastText classifier takes a text file as input. Every line corresponds to a sample and must have the following format
```
__label__<your_label> <corresponding text>
```
For example, in our case a line should look like this.
```
__label__positive you know robin williams god bless him is constantly...
```
Also, the data are presented `positive` first and then `negative`. To avoid having a strong model bias toward `negative`, **shuffle your data before training**.

#### Attributes

You can check a model's attributes as they are listed on the [cheatsheet](https://fasttext.cc/docs/en/options.html). Also, if you have a well configure IDE or use Jupyter Lab, tab is your friend.

#### Random seed

To my knowledge, there is no way to set the random seed for FastText. It uses C++ code in the back, so using `random.seed()` won't help. For every other model you will use in these projects, please set the random seed to make your results reproductible.

## Tips and advices

* Pretreatment is key for these models. Make sure you apply the same pretreatment at training and test time.
* Do not use the test set for hyperparameters search. Extract a validation set from the training data for that purpose. The test set is only made for comparing final models (see [data leakage](https://en.wikipedia.org/wiki/Leakage_%28machine_learning%29)).

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

This project provides 9 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 6th of October 2022 at midnight. Thought is is advised to send them progressively.
