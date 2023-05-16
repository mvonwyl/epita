# Introduction to Natural Language Processing 2
# Lab02

## Encoder-decoder model

Today you will implement a pretty decent machine translation model using the transformer and implement several decoding strategy.

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

### **(5 points)** Theoretical questions

Answer the following questions.

* In the positional encoding, why are we using a combination of sinus and cosinus?
* In the `Seq2SeqTransformer` class,
  * What is the parameter nhead for?
  * What is the point of the `generator`?
* Describe the goal of the `create_mask` function. Why does it handle differently the source and target masks?
* In the 
  

### **(6 points)** Decoding functions

The tutorial uses a greedy approach at decoding. Implement the following variations.
* (3 points) A top-k sampling with temperature.
* (1 point) A top-p sampling with temperature.
* (2 point) Play with the k, p and temperature parameters, and qualitatively compare a few (at least 3) translation samples for each approach (even the greedy one).

### **(2 points)** Compute the BLEU score of the model

Use the [sacreBLEU](https://github.com/mjpost/sacreBLEU) implementation to evaluate your model and quantitatively compare the 4 implemented decoding approaches on the test set. Explain what all the output values mean (when using the `corpus_score` function).

In the [python section](https://github.com/mjpost/sacrebleu#using-sacrebleu-from-python), you'll notice the library accepts more than just one possible translation as reference, but the given dataset only has one translation per sample.

Using the `translate` function provided in the tutorial is pretty slow, as it translate text by text. It's recommended you modify the function to accept a list of texts as input, and batch them for translations (also **bonus point**).

**\[Bonus\]** Use part of the test set to perform an hyperparameters search on the value of temperature, k, and p. Note that, normally, this should be done on a validation set, not the test set.

## Going further

If you want to understand in-depth how the transformer model works, I recommend you check [The Annotated Tranformer](http://nlp.seas.harvard.edu/2018/04/03/attention.html) from HarvardNLP. This article helps you write your own transformer from scratch in pyTorch.

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code **before the Monday 29th of May at 10pm**. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report. Please send an email to `marc.von-wyl` at `epita` dot `fr`, when the project is ready to be graded.

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
