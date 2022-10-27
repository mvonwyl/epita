# Introduction to Natural Language Processing 2 Lab03

## Introduction

On this part, you will evaluate a simple semantic search with and without nearest neighbours approximation. You fill first create a searchable index, then evaluate queries on it in terms of Mean Average Precision and speed.

## **(8 points)** Create a searchable index

Use the [Beir](https://github.com/beir-cellar/beir) library to extract the **test set** of the [DBPedia entity dataset](https://github.com/UKPLab/beir#beers-available-datasets). Once done, looks at what the data are like.
* (1 point) Explain the data structure. What are the three values returned by Beir, and how are they presented.

You should have noticed that the corpus is quite huge. If you want to project the full corpus in vector space with`sentence-transformers` it could take up to 40 hours on a CPU.
* (2 points) To ease the problem,  extract all the document from the corpus which are relevant to at least one query. Then, add 100K random documents which are not relevant to any query. Make sure the process is reproducible by setting the random seed on whatever random sampling method you use.

Now, we should be ready to start experimenting with our smaller dataset. Use the [sentence-transformers](https://www.sbert.net/) library to index your dataset. [As queries and documents are different](https://www.sbert.net/examples/applications/semantic-search/README.html#symmetric-vs-asymmetric-semantic-search), use an [asymetric similarity models](https://www.sbert.net/docs/pretrained-models/msmarco-v3.html). Pick one model across the ones proposed. Make sure to document your choice, and why you picked it (because of accuracy, speed, ...).
* (2 points) Embed the reduced corpus and the queries using the chosen model.
    * Note that sentence-transformers allows you to normalize the projection. So you can later use a simple inner product instead of a cosine similarity (remember the cosine similarity is equivalent to the inner product of the normalized vectors).
* (3 points) Using the annotated set of queries, compute the Mean Average Precision (MAP) @100 as well as the average time per query.

## **(4 points)** Approximate nearest neighbours

Use a nearest neighbour approximation library to see if you can speed your search while not losing perforances. Pick one among the 3 proposed as examples [here](https://www.sbert.net/examples/applications/semantic-search/README.html#approximate-nearest-neighbor). 
* (3 points) Find a good set of parameters for the chosen ANN library and compute the Mean Average Precision @100.
* (1 point) explain what the parameters you picked are, and why you chose them.
* (Bonus) Play with these parameters and plot a speed vs MAP curve.

### Tips

* You can either index the `text` field of DBPedia only, or add the `title` field to it.
* There is no need to put the created dataset in your report. Just make sure its creation is reproductible by forcing random seeds in your code.

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

This part provides 12 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 17th of November 2022 at midnight. Thought is is advised to send them progressively.
