# Introduction to Natural Language Processing 01
# Lab 03

## Introduction

The project is a continuation of what we started on the second lab. You will train a logistic regression classifier on manually extracted features.

## Features (6 points)

For every given text, we want to generate a vector with the features seen in class.

**(6 points)** Code the following features:
* 1 if "no" appears in the document, 0 otherwise.
* The count of first and second pronouns in the document.
* 1 if "!" is in the document, 0 otherwise.
* Log(word count in the document).
* Number of words in the document which are in the positive lexicon.
* Number of words in the document which are in the negative lexicon.
* **\[Bonus\]** Add another feature of your choice.

For positive and negative lexicons, you can use the resources provided by [VADER sentiment](https://github.com/cjhutto/vaderSentiment). Look for the `vader_lexicon.txt` file and consider positive word if they score above a certain threshold (for example 1) and negative word if they score below a certain threshold (for example -1). Feel free to use another lexicon if you find one, but make sure you document your choice.

### Tips

* Don't forget to use a similar pre-treatment as the one you used for the previous lab.
* Beware that words in the VADER dictionary are not lemmatized or stemmed. Do not use these pretreatments here.
* When checking for occurences of "no" or pronouns, split the text into token. Just using `"no" in text` would return true if the word "notable" is in your text.

## Logistic regression classifier (6 points)

The `logistic_regression_pytorch.ipynb` notebook, in the same directory, shows how to train a logistic regression classifier using PyTorch on a dummy dataset.

* **(3 points)** Adapt the code by adding your feature extractor and train a classifier.
  * For training, don't use the test set as validation. Instead, split the training set into a training and a validation set (use 10 to 20% of the training set as validation).
* **(1 point)** Evaluate your classifier in terms of accuracy for the training, validation, and test set.
* **(1 point)** Look at the weights of your classifier. Which features seems to play most for both classes?
* **\[Bonus\]** The parameter `weight_decay` of the [SGD optimizer](https://pytorch.org/docs/stable/generated/torch.optim.SGD.html) corresponds to the L2 penalty. Try playing with this value and explain how it influence the model's weights.
* **(1 point)** Take two wrongly classified samples in the test set and try explaining why the model was wrong.
* **\[Bonus\]** Train logistic regression classifier using the [scikit-learn implementation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html). How does it compare with the PyTorch version?

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code **before the 7th of April at 10pm**. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report. Please send an email to `marc.von-wyl` at `epita` dot `fr`, when the project is ready to be graded.

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