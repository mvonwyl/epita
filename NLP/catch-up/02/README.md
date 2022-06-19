# Introduction to Natural Language Processing Catch-up 2

## Introduction

The second evaluation is made of two small projects and theoritical questions on the class.

For coding standards, please respect the following guidelines
* Use [docstring](https://www.programiz.com/python-programming/docstrings) format to describe your functions and their arguments.
* Use typing.
* Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...).
* Make your results reproducible (force random seeds values when necessary and possible).
* Don't hesitate commenting in details part of the code you consider complex or hard to read.

## First project: closing on the sentiment classifier (9 points)

### Library and dataset

On the first part, you will continue the work on our sentiment classifer using a pre-trained transformer. The goal is to use the HuggingFace transformers library to fine-tune a pre-trained transformer on the old IMDB dataset. If you haven't done it yet (and as it was asked on the [7th lab](https://github.com/mvonwyl/epita/tree/master/NLP/07)), it is strongly recommended that you follow [HuggingFace course](https://huggingface.co/course/chapter1/1), at least lessons 1 to 4, before you start this part.

The IMDB sentiment dataset is a collection of 50K movie reviews, annotated as positive or negative, and split in two sets of equal size: a training and a test set. Both set have an equal number of positive and negative review. The dataset is available on several libraries, but we ask that you use the following one HuggingFace [datasets](https://huggingface.co/datasets/imdb) version. If you haven't done it yet, follow their [tutorial](https://huggingface.co/docs/datasets/load_hub) on how to use the library for more details.

### Fine-tuning a model

Use the HuggingFace transformer library to fine-tune a model on the IMDB library dataset and then evaluate it on the test set. Go through the following steps.

1. Fine-tune the model on the training data. (4 points)
   * You can use Google colab if you do not have access to a machine with a strong GPU. Thus, for that part only, you can put all your code on a single notebook without packaging it.
   * We recommend using `https://huggingface.co/distilbert-base-uncased` as pre-trained model, as it is light and will fine-tune fast. If you want to use any other model, please make sure your document choice and why you use the model. **Beware** some models have already been fine-tuned with the IMDB dataset, so make sure you do not use any of those (the data used to train/fine-tune a model should be visible on the model's card). Other potential models are:
      * [BERT](https://huggingface.co/bert-base-uncased)
      * [RoBERTa](https://huggingface.co/roberta-base)
   * Provide the notebook used to train your model with adequate comments.
   * It is not mandatory that you save your model on HuggingFace model hub, but if you do, please fill up the model's card.
2. Evaluate the model in term of accuracy on the test data. (2 points)
3. Find the samples on the test set which are wrongly classified with the highest probability (sample on which the model gives the highest probability on the wrong class), and for at least 2 of them, try explaining why the model could have been wrong. (2 points).
4. What are the advantages and inconvenient of using this model in production compared to the naive Bayes we implemented in the first part of the course? (1 point)

## Second project: semantic search

For this second project, you will implement a very simple semantic search engine using a pre-trained model from the sentence-transformers library. You will compare a couple of models on one of BEIR's dataset in term of speed and relevance, and accelerate things using approximate nearest neighbours (ANN) methods.

### Vector search

1. Download the MS MARCO v2 dataset using the BEIR library.
2. Choose 2 models from the sentence transformers library and embedd the full **test** dataset.
   * Beware that different models have been trained on different similarities (dot product or cosine similarity).
3. Compute the MRR on the test set using your two dataset, as well as the average query time.
4. With the best model, take at least 2 queries where the desired result don't appear in the top 10, and discuss why.

### Approximate nearest neighbours

Choose one an approximate nearest neighbour library. Suggested library:
* Annoy
* FAISS (though beware it might be tricky to install, and is not installed on the machines at EPITA)
* HSNW
* Scann

With one of these library.
1. Find the parameter which regulate speed vs relevance and varying this parameter, generate a speed vs MRR plot.
   * Find the parameter that you can modify to make either the model faster or better (closer to not using an ANN).


## Theoritical questions

Answer the following questions.
1. What is the purpose of subword tokenization used by transformer models? (1 point)
   * Part of the answer is in the first part of the course (lesson 2).
   * What is the effect of the vocabulary size?
   * How does it impact out-of-vocabulary words (words which are in test data, but have not been seen in the training data)?
2. What are the differences between an RNN and an LSTM? (1 point)
   * What problem is an LSTM trying to solve compared to an RNN?
3. When building an encoder-decoder model using an RNN, what is the purpose of adding attention? (1 point)
   * What problem are we trying to solve?
   * How does attention solve the problem?
4. In a transformer model what is the multihead attention used for? (1 point)
   * What the purpose of self-attention?
   * Why do we use muliple head instead of one?
5. In a transformer, what is the purpose of positional embedding? (1 point)
   * What would be the problem if we didn't use it?
6. What is the purpose of having benchmarks to evalute models? (1 point)
7. In BERT, describe the two tasks used for pre-training (unsupervised) with a few sentences. (2 points)
   * **\[Bonus\]** Are they really unsupervised?
8. In a few sentences, explain how triplet loss is used to train a bi-encoder model for semantic similarity? (1 point)