# Introduction to Natural Language Processing 02
# Lab 01

## Introduction

This lab focuses on RNNs. We will code our own RNN before using the implementation provided by pyTorch. The aim of this lab is to understand the data structure and be confortable applying it on a simple problem, we thus still use the IMDB dataset.

## Code your own RNN (11 points)

Follow the `01 code your own RNN.ipynb` notebook. Fill and create functions and classes as asked.

## Using pyTorch's implementation (5 points)

Follow the `02 using pyTorch RNNs.ipynb` notebook. Fill and create functions and classes as asked. The whole vocabulary creation and input preparation parts are exactly the same as the one used for the first notebook, so feel free to reuse the code or, even better, to package functions in separate python files.

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code **before the Thursday 18th of May at 10pm**. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report. Please send an email to `marc.von-wyl` at `epita` dot `fr`, when the project is ready to be graded.

The assignment will be evaluated on the following criteria

* A report answering the questions above, describing your technical choices, and analysing your results.
* The quality of your code (modularity, efficiency, comments, coding standards).

**From now on, two non-optional points are dedicated to code quality.**

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments
* Use typing
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...)
* Make your results reproducible (force random seeds values)
* Don't hesitate commenting in details part of the code you consider complex or hard to read

Provide a `README.md` file with 
* A short description of the project
* A description of the file/module architecture

A `requirements.txt` is also recommended.