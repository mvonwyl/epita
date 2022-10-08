# Introduction to Natural Language Processing 2 Lab02

## Encoder-decoder model

Today you will implement a pretty decent machine translation model using the transformer and then compare it to what you could have, with the same amount of training time, with a combination of RNN + Attention.

###  Go through the pyTorch tutorial

To start with, just follow the pyTorch [language translation with nn.Transformer and torchtext tutorial](https://pytorch.org/tutorials/beginner/translation_transformer.html).

To make the code turn on Google Colab, you need to update the preinstalled version of spaCy and download the small German and English spaCy models. As pyTorch doesn't seem to maintain its tutorial with their most recent changes, you also need to install torchdata.
```
!pip install spacy sacrebleu torchdata -U
!python -m spacy download en_core_web_sm
!python -m spacy download de_core_news_sm
```

As the training takes time (~20min), you can start looking at the following steps while it finishes.

At training, you will encounter `TypeError: ZipperIterDataPipe instance doesn't have valid length` (pyTorch doesn't update their tutorials). A workaround can be found [here](https://github.com/pytorch/tutorials/issues/1868).

### **(5 points)** Decoding functions

The tutorial uses a greedy approach at decoding. Implement the following variations.
* (2 points) A top K sampling with and without temperature.
* (3 points) A beam search (from scratch).
* (1 point) Qualitatively compare a few (at least 3) translation samples for each approach (even the greedy one).

### **(2 points)** Compute the BLEU score of the model

Use the [sacreBLEU](https://github.com/mjpost/sacreBLEU) implementation to evaluate your model and quantitatively compare the 4 implemented decoding approaches. Explain what all the output values mean (when using the `corpus_score` function).

In the [python section](https://github.com/mjpost/sacrebleu#using-sacrebleu-from-python), you'll notice the library accepts more than just one possible translation as reference, but the given dataset only has one translation per sample.

Using the `translate` function provided in the tutorial is pretty slow, as it translate text by text. It's recommended you modify the function to accept a list of texts as input, and batch them for translations (also **bonus point**).

### **(Bonus)** Try with another language

Use the [Tatoeba dataset](https://huggingface.co/datasets/tatoeba) with the language pair of your choice to train the model again. Beware that the Multi30K dataset has 29K training sample and 1K test sample, while the Tatoeba dataset only has a training set (you'll have to split it yourself) and 262K sentence pairs for their English-French data. So maybe train on a sub-sample. As a suggestion, sort the sentences per size and only use the first 30K. 

* Extract data from the Tatoeba dataset.
* Train a model with it.
* Compute the BLEU score using sacreBLEU on left-out data.

## Going further

If you want to understand in-depth how the transformer model works, I recommend you check [The Annotated Tranformer](http://nlp.seas.harvard.edu/2018/04/03/attention.html) from HarvardNLP. This article helps you write your own transformer from scratch in pyTorch.

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

This part provides 7 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 17th of November 2022 at midnight. Thought is is advised to send them progressively.