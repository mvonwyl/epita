# Introduction to Natural Language Processing 2 Lab03

## HuggingFace Transformers

Follow the [HuggingFace transformers course](https://huggingface.co/course/chapter0), from chapter 0 to 4.

## **(9 points)** Sentence classification

Use the HuggingFace transformer library to fine-tune a model on the IMDB library dataset and then evaluate it on the test set. As you do not necessarily have access to a good GPU, and Google Colab is not always providing well, you do not have to fine-tune the model for more than one epoch. There is a fine-tuned model available for steps 2 onward.

Go through the following steps.

1. (5 points) Fine-tune the model on the training data.
   * Again, at least for one epoch, to make sure your code works.
   * If you want to make sure your model is loaded on GPU, after creating the `Trainer` object (see HuggingFace [course](https://huggingface.co/course/chapter3/3?fw=pt)), you can look at `model.device`. It should tell you it's on a `cuda` device.
   * We recommend using [distilbert](https://huggingface.co/distilbert-base-uncased) as pre-trained model, as it is light and will fine-tune fast. **Beware** some models have already been fine-tuned with the IMDB dataset, so make sure you do not use any of those (the data used to train/fine-tune a model should be visible on the model's card). Other potential models are:
      * [BERT](https://huggingface.co/bert-base-uncased)
      * [RoBERTa](https://huggingface.co/roberta-base)
      * [DeBERTa](https://huggingface.co/microsoft/deberta-base)
   * Provide the notebook used to train your model with adequate comments.
   * You can save your model on HuggingFace model hub (totally optional). If you do, please fill up the model's card.
   
For what follow, you can either use a model you fully fine-tuned, or [this one](https://huggingface.co/mvonwyl/distilbert-base-uncased-imdb).

2. (2 points) Evaluate the model in term of accuracy on the test data.
3. (1 point) For at least 2 samples which have been wrongly classified in the test set, try explaining why the model could have been wrong.
4.  (1 point) What are the advantages and inconvenient of using this model in production compared to the naive Bayes we implemented in the first part of the course?
5. **\[Bonus\]** Fine-tune your model using the accuracy as evaluation instead of the loss (default). You can use the base `Trainer` class, create your own custom trainer class, or even not use `Trainer` at all. Return the model with the best results on the validation set instead of the last one. (many points)

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

This part provides 9 points + 3 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions, and by packaging your code in extra python files. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, and presenting a language.

All projects have to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 17th of November 2022 at midnight. Thought is is advised to send them progressively.
