# Introduction to Natural Language Processing 1 Lab02

## Virtual environments
Before we start, we strongly encourage the use of [virtual environments](https://www.section.io/engineering-education/introduction-to-virtual-environments-and-dependency-managers/) to manage your different courses and projects. A few popular choices are
* [miniconda](https://docs.conda.io/en/latest/miniconda.html)
* [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)
* [pipenv](https://pipenv.pypa.io/en/latest/)

## Libraries

For today's lab, we will use several popular libraries for NLP

### NLTK

The [Natural Language Toolkit](https://github.com/nltk/nltk), NLTK is a suite of libraries and programs for symbolic and statistical natural language processing mostly done for English.
It started with Steven Bird and Edward Loper in the Department of Computer and Information Science at the University of Pennsylvania in 2001, and count now more than 300 contributors.
It contains a variety of modules data sets, and tutorials.

Even so it implements mainly what is considered traditional NLP technics (rule-based approach), the library is still widely used, maintained and updated.

### spaCy

[spaCy](https://github.com/explosion/spaCy) is an open-source software library for advanced natural language processing, written in the programming languages Python and Cython. It was developed initially by Matthew Honnibal and Ines Montani in 2015, but now counts more than 500 contributors.
The library was made for industrial applications (fast and robust) and provides pretrained pipelines for [60+ languages](https://spacy.io/models) (actually, 18 languages and two multilingual models, so far)

They also provide [interactive tutorials](https://course.spacy.io/en/) and [YouTube video introduction](https://www.youtube.com/c/ExplosionAI).

## Lab 02

In this lab, we will see and compare the effect of basic stemming and lemmatization, before introducing the NLTK interface to WordNet.

### Notebooks

* The stemming and lemmatization notebook show examples of code using NLTK and spaCy libaries for word tokenization, stemming, and lemmatization. Run them and compare results.
* The subword tokenization notebook shows the effect of using different type of subword tokenization algorithms and the difference in vocabulary generated between monolingual and multiligual models.

### WordNet

To get a grip on what WordNet can do, just follow the tutorial provided by the NLTK implementation [here](http://www.nltk.org/howto/wordnet.html)

## Start of the first project

For the first module, you will be evaluated on implementing several methods of text sentiment classification.
We start today with discovering the dataset. We will use the IMDB 50K movie reviews dataset. This dataset contains 50K manually written review with an associated sentiment: positive and negative. 25K reviews are used as training set and 25K review as evaluation set.

Start by [downloading](https://pytorch.org/text/stable/datasets.html#imdb) the dataset from torchText here, and look at the data (presentation, label, ...).


