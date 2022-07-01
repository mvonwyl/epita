# Introduction to Natural Language Processing Catch-up 2

## Introduction

The second evaluation is made of a small project and theoritical questions on the course.

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments.
* Use typing.
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...).
* Make your results reproducible (force random seeds values when necessary and possible).
* Don't hesitate commenting in details part of the code you consider complex or hard to read.

## Project closing on the sentiment classifier (12 points)

### Library and dataset (3 points)

You will apply a pre-trained transformer model to our sentiment classifier dataset. The goal is to use the HuggingFace transformers library to fine-tune a pre-trained transformer on the old IMDB dataset. If you haven't done it yet (and as it was asked on the [7th lab](https://github.com/mvonwyl/epita/tree/master/NLP/07)), it is strongly recommended that you follow [HuggingFace course](https://huggingface.co/course/chapter1/1), at least lessons 1 to 4 (especially 3), before you start this part.

**You can use Google colab if you do not have access to a machine with a strong GPU. Thus, you can put all your training code on a single notebook without packaging it.**

The IMDB sentiment dataset is a collection of 50K movie reviews, annotated as positive or negative, and split in two sets of equal size: a training and a test set. Both set have an equal number of positive and negative review. The dataset is available on several libraries, but we ask that you use the following one HuggingFace [datasets](https://huggingface.co/datasets/imdb) version. If you haven't done it yet, follow their [tutorial](https://huggingface.co/docs/datasets/load_hub) on how to use the library for more details.

Note that the dataset doesn't have a "validation" set, and we will need one to train the model. During training, we will train the model on the training set, and use the validation set to select which epoch gave us the best model.

1. (2 points) Create a validation set([tutorial](https://huggingface.co/course/chapter5/3?fw=pt#creating-a-validation-set), [documentation](https://huggingface.co/docs/datasets/v2.3.2/en/package_reference/main_classes#datasets.Dataset.train_test_split)) from the test set. It should 20% of the size of the training set. Make sure it's stratified (the proportion of each class must be the same in the training and validation set).
2. (1 point) Make sure the training and validation set have the same proportion of both class.

### Fine-tuning a model (9 points)

Use the HuggingFace transformer library to fine-tune a model on the IMDB library dataset and then evaluate it on the test set. As you do not necessarily have access to a good GPU, and Google Colab, is not always providing well, you do not have to fine-tune the model for more than one epoch. There is a fine-tuned model available for steps 2 onward.

Go through the following steps.

1. (5 points) Fine-tune the model on the training data.
   * Again, at least for one epoch, to make sure your code works.
   * If you want to make sure your model is loaded on GPU, after creating the `Trainer` object (see HuggingFace [course](https://huggingface.co/course/chapter3/3?fw=pt)), you can look at `model.device`. It should tell you it's on a `cuda` device.
   * We recommend using [distilbert](https://huggingface.co/distilbert-base-uncased) as pre-trained model, as it is light and will fine-tune fast. If you want to use any other model, please make sure your document choice and why you use the model. **Beware** some models have already been fine-tuned with the IMDB dataset, so make sure you do not use any of those (the data used to train/fine-tune a model should be visible on the model's card). Other potential models are:
      * [BERT](https://huggingface.co/bert-base-uncased)
      * [RoBERTa](https://huggingface.co/roberta-base)
   * Provide the notebook used to train your model with adequate comments.
   * You can save your model on HuggingFace model hub (totally optional). If you do, please fill up the model's card.
   
For what follow, you can either use a model you fully fine-tuned, or [this one](https://huggingface.co/mvonwyl/distilbert-base-uncased-imdb).

2. (2 points) Evaluate the model in term of accuracy on the test data.
3. (1 point) For at least 2 samples which have been wrongly classified in the test set, try explaining why the model could have been wrong.
4.  (1 point) What are the advantages and inconvenient of using this model in production compared to the naive Bayes we implemented in the first part of the course?
5. **\[Bonus\]** Fine-tune your model using the accuracy as evaluation instead of the loss (default). You can use the base `Trainer` class, create your own custom trainer class, or even not use `Trainer` at all. Return the model with the best results on the validation set instead of the last one. (many points)

## Theoritical questions (10 points)

Answer the following questions.
1. (1 point) What is the purpose of subword tokenization used by transformer models?
   * Part of the answer is in the first part of the course (lesson 2).
   * What is the effect on the vocabulary size?
   * How does it impact out-of-vocabulary words (words which are not in the training data, but appear in the test data, or production environment)?
2. (1 point) What are the differences between an RNN and an LSTM?
   * What problem is an LSTM trying to solve compared to a basic RNN?
3. (1 point) When building an encoder-decoder model using an RNN, what is the purpose of adding attention?
   * What problem are we trying to solve?
   * How does attention solve the problem?
4. (1 point) In a transformer model what is the multihead attention used for?
   * What the purpose of self-attention?
   * Why do we use muliple head instead of one?
5. (1 point) In a transformer, what is the purpose of positional embedding?
   * What would be the problem if we didn't use it?
6. (1 point) What is the purpose of having benchmarks to evalute models?
7. (2 points) In the BERT model, describe the two tasks used for pre-training (unsupervised) with a few sentences.
   * **\[Bonus\]** Are they really unsupervised?
8. (1 point) In a few sentences, explain how the triplet loss is used to train a bi-encoder model for semantic similarity?
   * The simplest verson of the triplet loss.
9. (1 point) What is the purpose of using an Approximate Nearest Neighbour method to speed up search?
   * How does it help?


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

**Please provide your code and report on a GitHub or GitLab repository, and send a link to it to `marc.von-wyl` at `epita` dot `fr` before midnight on the 20th of July.**

### Grade computation

Every part of this work is graded on a certain number of points.
* 12 points on the first part (sentiment classifier).
* 10 points on Theoritical questions.
* 4 points on coding standards.

It sums to 26 points which are then projected to a grade going from 0 to 16. Additional points can be earned by answering the bonus questions, or going further than what was asked.
