# Introduction to Natural Language Processing 2 Lab02

## Encoder-decoder model

Today you will implement a pretty decent machine translation model using the transformer and then compare it to what you could have, with the same amount of training time, with a combination of RNN + Attention.

## Transformer model

### 1. Go through the pyTorch tutorial

To start with, just follow the pyTorch [language translation with nn.Transformer and torchtext tutorial](https://pytorch.org/tutorials/beginner/translation_transformer.html). **Note that to make it work on Google Colab, you'll have to update the preinstalled version of spaCy**. You will also have to download the small German and English spaCy models.
```
!pip install -U spacy
!python -m spacy download en_core_web_sm
!python -m spacy download de_core_news_sm
```
### 2. Compute the BLEU score of the model
Once you have gone through the tutorial, measure the BLEU score of your model on the test set. As we have seen in class, you should not try coding your own version of the algorithm. Instead use the [sacreBLEU](https://github.com/mjpost/sacreBLEU) implementation. In the [python section](https://github.com/mjpost/sacreBLEU), you'll notice the library accepts more than just one possible translation as reference, but the given dataset only has one translation per sample. You can also 

### 3. Try with another language

Use the [Tatoeba dataset](https://huggingface.co/datasets/tatoeba) with the language pair of your choice to train the model again. Beware that the Multi30K dataset has 29K training sample and 1K test sample, while the Tatoeba dataset only has a training set (you'll have to split it yourself) and 262K sentence pairs for their English-French data. So maybe train the transformer on a sub-sample.

## Classical RNN + Attention model


## Going further

If you want to understand in-depth how the transformer model works, I recommend you check [The Annotated Tranformer](http://nlp.seas.harvard.edu/2018/04/03/attention.html) from HarvardNLP. This article helps you write your own transformer from scratch in pyTorch.