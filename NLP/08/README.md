# Introduction to Natural Language Processing 2
# Project

## Introduction

For this project, you will code a question-answering engine. The engine is composed of the following parts.
1. An search engine based on semantic similarity embedding
2. A nearest neighbour approximation index
2. An extractive QA model

The idea is to build each of this part separately before putting them together. Each part will have to be evaluated separately and then the model as a whole.


### Imporant

Read the following point before you start.
* **Read this document entirely before starting.** You might miss important notes and tips.
* There is a bit of code, but a lot of evaluation and digging into the results to understand the models' limitations.
* **Dont start the project on the last week.** Some parts of this project will need to run for at least an hour.

## Train a question-answering model \[8 points\]

To start with, you will train your own question-answering model on [SQuAD v2](https://rajpurkar.github.io/SQuAD-explorer/). Use the [notebook example](https://github.com/huggingface/notebooks/blob/master/examples/question_answering.ipynb) given by the transformer library as guide. Use one of the following model as base.
* `distilbert-base-uncased` (default)
* `bert-base-uncased`
* `robert-base`

SQuAD v2 is made of 130K training samples. Training a model on it for 3 epochs takes easily 6 hours on a colab notebook with a GPU. Use a subset of SQuAD (perhaps a few thousand samples) to train a very basic model. Save this model on HuggingFace hub **and make sure you describe it clearly on the mode card**. Evaluate your model on the evaluation data, and compare it with a fully trained model found on HuggingFace hub.

### What needs to be done

1. **\[5 points\]** Take the [example notebook](https://github.com/huggingface/notebooks/blob/master/examples/question_answering.ipynb) and **extract the training code** so it's packaged in a clean way. Fine-tune one the model proposed above on a subset of SQuAD v2 (it shouldn't train for more than an hour).
2. **\[3 points\]** Evaluate your model on the validation data. **Extract the evaluation code** from the notebook so it's packaged and reusable (especially you will need to reuse it later).
3. **\[1 point\]** Use a fully pre-trained model of your choice (e.g. `mvonwyl/roberta-base-finetuned-squad2`) and evaluate it on the validation data.
  1. Show at least 2 examples badly classified and discuss what might have gone wrong.

## Create an index \[8 points\]

In this part, you will build an index using semantic similarity and nearest neighbour approximation. As you might have realized during the previous part, using an extracting QA model on a lot of data is slow. We can't just use the model on more than a few documents. To speed up our system, we will only propose relevant document to the QA model.

Even so SQuAD validation data were used for validation loss when training the model, we will use them as "test" data (as we don't have access to the test data). **Keep in mind this is not good practice**.

If you look in depth into SQuAD v2 data, you'll realize that a lot of questions refer to the same contexts. So out of the 11K validation samples, we have on around 1K unique contexts. To make our QA model a bit more challenging you will mix it with [DBPedia entity dataset](https://github.com/UKPLab/beir#beers-available-datasets). Use the BEIR library to extract DBPedia corpus and add enough paragraph of at least 50 words to SQuAD validation set so your dataset has at least 10K samples.

Once your dataset is big enough, use the [sentence-transformers](https://www.sbert.net/) library to index your dataset. [As queries and documents are different](https://www.sbert.net/examples/applications/semantic-search/README.html#symmetric-vs-asymmetric-semantic-search), use an [asymetric similarity models](https://www.sbert.net/docs/pretrained-models/msmarco-v3.html). Pick one model across the ones proposed. Make sure to document your choice, and why you picked it (it can because of performances, speed, ...). Project your full dataset with this model and measure its [MRR](https://en.wikipedia.org/wiki/Mean_reciprocal_rank) and speed.
Basically, you measure the models' capacity to find relevant documents/paragraphs within your index for a given question. 

Use a nearest neighbour approximation library to see if you can speed your search while not losing perforances. Pick one among the 3 proposed as examples [here](https://www.sbert.net/examples/applications/semantic-search/README.html#approximate-nearest-neighbor). Play with their parameters and plot a speed vs MRR curb.

### What needs to be done

1. **\[1 point\]** Add DBpedia contexts of at least 50 words to your corpus of unique SQuAD v2 validation context, so the corpus of unique contexts reaches at least 10K samples.
2. **\[4 points\]** Index your corpus by projecting it in a vector space using two [asymetric similarity models](https://www.sbert.net/docs/pretrained-models/msmarco-v3.html) of your choice. Document these choices (why these two). Compare their result on your corpus using MRR and their speed.
  1. Beware, some models were train with cosine similarity, others with dot product. Make sure you use the right similarity operation when using them.
3. **\[3 points\]** Use a nearest neighbour approximation library to speed up your search. Pick one across the 3 proposed [here](https://www.sbert.net/examples/applications/semantic-search/README.html#approximate-nearest-neighbor), and do a bit of parameter comparison (MRR vs speed).
  1. Here too, make sure you use the right similarity. Note that Annoy and FAISS don't support cosine similarity, so you'll have to [tweak things a bit](https://github.com/facebookresearch/faiss/issues/61)

### Tips

* To make things easier, only use the descriptions as searchable attributes (in DBPedia it's the `text` attribute, in SQuAD it's `context`).
* There is no need to put the created dataset in your report. Just make sure its creation is reproductible by forcing random seeds in your code.
* In the second part you need to
  1. Project the full dataset (so SQuAD `context` with the extra DBPedia `text`) as a list of vectors using the `sentence-transformer` model.
  2. For each query
     1. Project it using the same model.
     2. Compute the similarity between the projected query and the list of vectors (the similarity can be dot product or cosine similarity depending of the model).
     3. Sort from most similar to least .similar
  3. Compute the MRR on thse rankings.

## Put everything together \[4 points\]

Connect your two systems as one. Put together a system that can extract an answer from the whole dataset created at the previous step. If you packaged everything correctly, you'll just have to connect the different classes and functions.

Create a system which takes a question, return the top K relevant documents, and look into these K document to extract the potential answers.

### What needs to be done

1. **\[2 point\]** Connect both part of your code together
2. **\[2 points\]** Evaluate your full system in terms of exact match and F1-score (the metrics provided by datasets: `metric = load_metric("squad_v2")`).

If the nearest neighbour system you used on the previous step is not good enough (it doesn't manage to provide the relevant text in the its first results), use the full index search instead.

## Evaluation

Please provide your code on a github repo as well as a report sent to `marc.von-wyl` at `epita` dot `fr` before the 25th of November 2021.
* Your QA model trained on the little amount of data should be available on HuggingFace Hub with a model card describing its state (trained on a subset of SQuAD v2).
* The code should be executable with scripts or notebooks. In both cases, its usage must be documented in a README file or within the notebooks.
* Remember that notebooks are not made to contain a lot of code. So please package your code so it's reusable.

You'll also be graded on the quality of your code. You might lose point if
* Your code is not well packaged
* The naming/typing conventions are not respected
  * Though we'll be flexible on the typing using external libraries
* Your requirements.txt file is incomplete (your code doesn't run without installing missing dependencies).

## Tips

* On the first part, most of the work is already done for you. It's about extracting code in a reusable way and evaluating models.
* Once again, **start this project early**.
* If something goes wrong, don't hesitate asking questions.
* Most of this project is about using libraries and already written code. 