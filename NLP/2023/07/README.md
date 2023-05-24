# Introduction to Natural Language Processing 2 Lab02

## HuggingFace Transformers

Follow the [HuggingFace transformers course](https://huggingface.co/course/chapter0), from chapter 0 to 4.

## **(10 points)** Sentence classification

Use the HuggingFace transformer library to fine-tune a model on the IMDB library dataset and then evaluate it on the test set. As you do not necessarily have access to a good GPU, and Google Colab is not always providing well, you do not have to fine-tune the model for more than one epoch. There is a fine-tuned model available for steps 2 onward.

Go through the following steps.

1. (3 points) Fine-tune the model on the training data.
   * Again, at least for one epoch, to make sure your code works.
   * If you want to make sure your model is loaded on GPU, after creating the `Trainer` object (see HuggingFace [course](https://huggingface.co/course/chapter3/3?fw=pt)), you can look at `model.device`. It should tell you it's on a `cuda` device.
   * We recommend using [distilbert](https://huggingface.co/distilbert-base-uncased) as pre-trained model, as it is light and will fine-tune fast. **Beware** some models have already been fine-tuned with the IMDB dataset, so make sure you do not use any of those (the data used to train/fine-tune a model should be visible on the model's card). Other potential models are:
      * [BERT](https://huggingface.co/bert-base-uncased)
      * [RoBERTa](https://huggingface.co/roberta-base)
      * [DeBERTa](https://huggingface.co/microsoft/deberta-base)
   * Provide the notebook used to train your model with adequate comments.
   * You can save your model on HuggingFace model hub (totally optional). If you do, please fill up the model's card.
2. **\[Bonus\]** Fine-tune your model using the accuracy as evaluation instead of the loss (default).
   
For what follow, you can either use a model you fully fine-tuned, or [this one](https://huggingface.co/mvonwyl/distilbert-base-uncased-imdb).

3. (2 points) Evaluate the model in term of accuracy on the test data.
4. (2 points) For at least 2 samples which have been wrongly classified in the test set, try explaining why the model could have been wrong.
5. (3 points) What are the advantages and inconvenient of using this model in production compared to the naive Bayes we implemented in the first part of the course? And compared to a recurrent model like an RNN or an LSTM?
7. **\[Bonus\]** The model only accepts inputs of maximum 512 tokens. Propose and implement a solution that goes around that. For example:
    * Compare using only the beginning (what you already implemented) with only the ending of the review (as review tends to end with a conclusion summarizing the sentiment).
        * You can train a model on the last 512 token of every training input, or use the same model but only predict on the end of each review.
        * Find review longer than 512 tokens, and evaluate on them separately.
        * The [truncation_side](https://huggingface.co/docs/transformers/v4.20.1/en/main_classes/tokenizer#transformers.PreTrainedTokenizer) parameter might help.
    * Or use a sliding window and average the predictions of every part.
        * For example, use a window with a stride of 64 tokens.
        * You can either make the model loop on the tokenized input, or [create your own pipeline](https://huggingface.co/docs/transformers/add_new_pipeline).

## Evaluation

The project must be sent back as a github (or gitlab) project containing a report and the code **before the Thursday 8th of June at 10pm**. The report can be written as a jupyter notebook, but if so, please use markdown to answer questions and structure your report. Please send an email to `marc.von-wyl` at `epita` dot `fr`, when the project is ready to be graded.

The assignment will be evaluated on the following criteria

* A report answering the questions above, describing your technical choices, and analysing your results.
* The quality of your code (modularity, efficiency, comments, coding standards).

**Two non-optional points are dedicated to code quality.**

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
