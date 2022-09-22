# Introduction to Natural Language Processing
# Project

## Introduction

This lab is composed of 2 parts. First, using an RNN and LSTM to classify text. Then, a series of theoritical questions.

## RNN/LSTM classifier **(14 points)**

Follow the `IMDB_with_RNN.ipynb` notebook. You'll have to fill missing functions, rewrite an RNN into an LSTM, and anwer a few questions. The notebook is self-explained.

## Theoritical questions **(9 points)**

The following questions have been seen during the course and can be found on the support and references. Don't copy-paste what is written in the course, answer with your own words.

Answer the following questions.
1. **(2 points)** Explain with your own words, using a short paragraph for each, what are:
   * Phonetics and phonology
   * Morphology and syntax
   * Semantics and pragmatics
2. **(1 point)** What is the difference between stemming and lemmatization?
   * How do they both work?
   * What are the pros and cons of both methods?
3. **(1 point)** On logistic regression:
   * How does stochastic gradient descent work?
   * What is the role of the learning rate?
   * Will it always find the global minimum?
4. **(1 point)** What problems does TF-iDF try to solve?
   * What the is the TF part for?
   * What is the iDF part for?
5. **(2 point)** Summarize how the skip-gram method of Word2Vec works using a couple of paragraphs.
   * How does it uses the fact that _two words appearing in similar contexts are likely to have similar meanings_?
6. **(1 point)** What are the differences between an RNN and an LSTM?
   * What problem is an LSTM trying to solve compared to a basic RNN?
7. **(1 point)** What would you expect if we use one of our classifiers trained on IMDB on Twitter data, and why?

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

This part provides 15 points + 3 points on coding standards: naming, typing, comments, and docstring + 9 points on theoritical questions. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

* Naive Bayes: 19 points
* FastText: 12 points
* LSTM: 18 points
* Theory: 9 points
* **Total** 58 points (projected between 0-16).

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 6th of October 2022 at midnight. Thought is is advised to send them progressively.