# Introduction to Natural Language Processing
# Project

## Introduction

The project is a continuation of we started on the third lab. We will try beating the results we obtained with naive Bayes and logistic regression on hand made features using word vectors such as Word2Vec.

## The dataset

We continue with the IMDB sentiment dataset, which is available on several libraries.
* HuggingFace [datasets](https://huggingface.co/docs/datasets/)
* [TorchText](http://pytorch.org/text/master/datasets.html?highlight=imdb#torchtext.datasets.IMDB)
* [Keras](https://keras.io/api/datasets/imdb/)

## FastText baseline

FastText provides two main features:
1. A trainable [text classifier](https://fasttext.cc/docs/en/supervised-tutorial.html)
2. Trainable and pre-trained word embeddings in [157 languages](https://github.com/facebookresearch/fastText/blob/master/docs/crawl-vectors.md)

Train a FastText classifier on the IMDB dataset as a baseline.
* Try with and without pretreatment (please document your pretreatment).
* Do a bit of [hyperparameters tunning](https://fasttext.cc/docs/en/autotune.html). Play with the learning rate, vector dimensions, and word ngrams parameters. Please use a subset of the training set as validation set. **Do not use the test set for hyperparameter tuning**.
* Report the accuracy of your experiments on the test data.
* For your best classifier, provide examples of wrongly classified samples for both class as well as why you believe these examples were wrongly classified.

## Beating the baseline

Try beating the baseline using a combination of methods we have seen in class. You can choose one or several of the following word embeddings.
* FastText ([training your own word embeddings](https://fasttext.cc/docs/en/unsupervised-tutorial.html) or using the [pretrained ones](https://github.com/facebookresearch/fastText/blob/master/docs/crawl-vectors.md)).
* [GloVe](https://github.com/stanfordnlp/GloVe)
* [Word2Vec](https://radimrehurek.com/gensim/models/word2vec.html)

All of them provide pretrained word embeddings and ways of training word embedding on given data. Note that FastText can create word embedding for unknown words (words which have not been seen at training), but GloVe and Word2Vec are dictionary based.

Connect the word embeddings to a classifier of your choice (logisitic regression, SVM, ...). A common way of doing so is taking the average vector of all the words in the review and using the vector as input for your classifier.

Document your experiments (accuracy, hyperparameters search, model selection, ...), and for the best model provide examples of wrongly classified samples for both class as well as why you believe these examples were wrongly classified.

## Tips and advices

* Pretreatment is key for these models. Make sure you apply the same pretreatment at training and test time.
* Do not do hyperparameter search using the test set. Extract a validation set from the training data for that purpose. The test set is only made for comparing final models (see [data leakage](https://en.wikipedia.org/wiki/Leakage_%28machine_learning%29)).
* It's fine if you don't beat the baseline. Just make sure you tried enough methods, and explain and analyse your results well enough.

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