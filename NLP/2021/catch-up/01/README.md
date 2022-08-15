# Introduction to Natural Language Processing Catch-up 1

## Introduction

In this small project, you will code a sentiment classifier using the naive Bayes methods seen in class and compare it with the FastText library. There are a few theoritical questions to answer as well.

**Please, read the full assignment before starting.**

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments.
* Use [typing](https://realpython.com/python-type-checking/).
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...).
* Make your results reproducible (force random seeds values when necessary and possible).
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
   3. **\[Bonus\]** add other pretreatments. (bonus points)
2. Train a naive Bayes classifier on the training set. (4 points)
3. Report the accuracy on both training and test set. (1 point)
4. Why is accuracy a sufficient measure of evaluation here? (1 point)
5. **\[Bonus\]** What are the top 10 most important words (features) for each class? (bonus points)
   1. Look at the words with the highest likelihood in each class (if you use scikit-learn, you want to check `feature_log_prob_`).
   2. Remove stopwords (see [NLTK stopwords corpus](https://pythonspot.com/nltk-stop-words/)) and check again.
6. Take at least 2 wrongly classified example from the test set and try explaining why the model failed. (1 point)

## FastText **(9 points)**

Use the [FastText library](https://fasttext.cc/docs/en/support.html) to train and test a classifier.

Go through the following steps.
1. Turn the dataset into a dataset compatible with Fastext (see the _Tips on using FastText_ section a bit lower). (2 points)
   * For pretreatment, only apply lower casing and punctuation removal.
2. Train a FastText classifier with default parameters on the training data, and evaluate it on the test data using accuracy. (2 points)
3. Use the [hyperparameters search functionality](https://fasttext.cc/docs/en/autotune.html) of FastText and repeat step 2. (3 points)
   * To do so, you'll need to [split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html) your training set into a training and a validation set (don't forget to shuffle your dataset).
   * Let the model search for 5 minutes (it's the default search time).
4. Look at their [attributes](https://fasttext.cc/docs/en/options.html). How do the two models differ? (1 points)
   * Only refer to the attributes you think are interesting, not all of them.
   * See the _Tips on using FastText_ (just below) for help.
5. Using the tuned model, take at least 2 wrongly classified examples from the test set, and try explaining why the model failed. (1 point)
6. **\[Bonus\]** Why is it likely that the attributes `minn` and `maxn` are at 0 after an hyperparameter search on our data? (bonus point)
   * Hint: think about the morphology of English.

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

## Theoritical questions **(7 points)**

The following questions have been seen during the course and can be found on the support and references. Don't copy-paste what is written in the course, answer with your own words.

Answer the following questions.
1. Explain with your own words, using a short paragraph for each, what are: (2 points)
   * Phonetics and phonology
   * Morphology and syntax
   * Semantics and pragmatics
2. What is the difference between stemming and lemmatization? (1 point)
   * How do they both work?
   * What are the pros and cons of both methods?
3. On logistic regression: (1 point)
   * How does stochastic gradient descent work?
   * What is the role of the learning rate?
   * Will it always find the global minimum?
4. What problems does TF-iDF try to solve? (1 point)
   * What the is the TF part for?
   * What is the iDF part for?
5. Summarize how the skip-gram method of Word2Vec works using a couple of paragraphs. (2 point)
   * How does it uses the fact that _two words appearing in similar contexts are likely to have similar meanings_?


## Evaluation

The assignment will be evaluated on the following criteria.

* A report answering the questions above, describing your technical choices, and analysing your results.
   * Can be written in French or English.
* The quality of your code (modularity, efficiency, comments, coding standards).

Provide a `README.md` file with:
* A short description of the project.
* A description of the file/module architecture.
* How to install the dependencies, run the code, and reproduce your results.
  * Provide at least a `requirements.txt` or a conda yaml file, and the minimum python version to run your code.

Please provide your code and report on a github repository, and send a link to it to `marc.von-wyl` at `epita` dot `fr` before midnight on the 6th of July.

### Grade computation

Every part of this work is graded on a certain number of points.
* 3 points on the dataset.
* 9 points on naive Bayes.
* 9 points on FastText.
* 7 points on the theory.
* 4 points on coding standards.

It sums to 32 points which are then projected to a grade going from 0 to 16. Additional points can be earned by answering the bonus questions, or going further than what was asked.