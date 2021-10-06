# Introduction to Natural Language Processing 2 Lab01

## Introduction

You'll find two notebooks in the same directory.

1. The first one shows how to implement an N-gram language model with NLTK
2. The second one shows how to use an RNN using pyTorch

The goal of this practice session is just to play with the notebooks, compare results between these two approaches and have fun.

## Recommendations

* The second notebook uses pyTorch and will run much faster if you can train the model using a GPU. It's recommended you run it on a Google colab session with GPU (if you don't know how to do that, just ask).
* You can try another dataset than Penn Treebank, but don't forget to split it in sentences (e.g. IMDB has reviews made of several sentences, here to make the problem easier to compute, we only work at sentence level).