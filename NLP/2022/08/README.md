# Introduction to Natural Language Processing 2 Lab03

## Introduction (1 point)

Your company wants to sell a moderation API which tackle toxic content on Twitter. They ask you to come up with a model which detect toxic tweets. You remember your NLP classes, and start looking for existing models or datasets. You find a collection of [academic Twitter dataset on HuggingFace hub](https://huggingface.co/datasets/tweet_eval). Especially, the `hate` and `offensive` datasets seem close to what you are looking for.

1. (1 point) Pick one of the datasets between `hate` and `offensive`, and justify your choice. Remember that it is for a commercial application.

## Evaluating the dataset (5 points)

Before using the data to train a model, you have the right reflex and start with a data analysis.

1. (1 point) Check the dataset. Look at the splits, proportion of classes, and see what you can figure out by just looking at the text.
2. (3 points) Use [BERTopic](https://github.com/MaartenGr/BERTopic) to extract the topics within the data, and the main topics within each class. Please, think about [fixing the random seed](https://stackoverflow.com/questions/71320201/how-to-fix-random-seed-for-bertopic).
    * A [good model](https://github.com/MaartenGr/BERTopic#embedding-models) for sentence similarity is `all-MiniLM-L6-v2`, as it is [fast, light, and pretty accurate](https://www.sbert.net/docs/pretrained_models.html). You can use another one, but make sure to document your choice.
3. (1 point) What do you think about the results? How do you think it could impact a model trained on these data?
4. **Bonus** By default, BERTopic extracts single keywords. Play with model to extract bigrams or more. See if you can go deeper in your analysis.

## Evaluate a model (4 points)

You were thinking about fine-tuning a [RoBERTa](https://arxiv.org/abs/1907.11692) model on the dataset, but RoBERTa has been train on 2019 data, which do not include any tweet. Moreover, pretraining a model from scratch can be costly. Fortunately, a [reliable entity](https://github.com/cardiffnlp) pretrained RoBERTa on Tweets and even fine-tuned it on both datasets [here](https://huggingface.co/cardiffnlp/twitter-roberta-base-offensive?text=I+like+you.+I+love+you) and [here](https://huggingface.co/cardiffnlp/twitter-roberta-base-hate?text=I+like+you.+I+love+you).

1. (2 points) Evaluate their model on the test split of the dataset you picked, using precision, recall, and F1-score.

To see how the model would fare on production data, you have 10K English tweets and replies available on the tweets.json file (taken from [internet archive](https://archive.org/details/archiveteam-twitter-stream-2021-07)). Note that the language was filtered using the Twitter API, so there might still be tweets in more than just English. The JSON fields were trimmed to minimum and the text was already preprocessed to mask user handles and URLs, like the tweets in your dataset.

2. (2 points) Extract the top 50 tweets your model is most confident about in the target class (offensive or hateful). Do you believe the model is doing a great job? For at least 2 tweets the model wrongly classified in your target class, try explaining what could have gone wrong.
3. **Bonus** Use [SHAP](https://github.com/slundberg/shap/tree/45b85c1837283fdaeed7440ec6365a886af4a333#natural-language-example-transformers) on the provided tweets, or manually written texts, to see if you can find topics on which the model is biased.
4. **Bonus** Train a naive Bayes model on the data, and compare its results with this model.

## Annotate data (8 points)

Regardless of the model's performances, you decide to annotate your own collection of tweets that you will keep as an evaluation set.

1. (1 point) Extract about 100 tweets containing at least 20% of your target class (offensive/hateful), from the 10K tweets provided. You can use the pretrained model to help you find tweets in the target class.
2. (1 point) Without discussing a guideline, every person in your group is going to annotate these tweets separately. So if you are 4, annotate them 4 times.
    * Typically, create a Google sheet or an excel document, one tab per person, in each tab one column for the text, and annother on the class.
3. (1 point) Evaluate your inter-annotaor agreement using Cohen Kappa (if you are 2) or Fleiss Kappa.
    * If, like your teacher, you have issues making the [NLTK implementation](https://www.nltk.org/_modules/nltk/metrics/agreement.html) work on the latest version of python (3.10+), you can use the [scikit-learn implementation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.cohen_kappa_score.html) of Cohen Kappa, and compute a matrix by pair of annotators.
4. (1 point) Evalute the result. What does the score mean? Are you doing a good job annotating the data and, if not, why?
5. (3 points) Altogether, write down an annotation guildeline (which should be at least 2/3 of a page long).
    * What does the target class look like?
    * Any examples you could provide for ambiguous cases?
    * Keep "Can't tell / not annotable" class. Make sure you document what this class mean in your guideline.
6. (1 point) Annotate the data again. See if your score got better.

Please provide the annotation sheets before and after guideline was written, the guideline, and the inter-annotator agreement before and after the guideline, in your report.

## Theoritical questions (16 points)

Answer the following questions.
1. (2 point) What is the purpose of subword tokenization used by transformer models?
   * Part of the answer is in the first part of the course (lesson 2).
   * What is the effect on the vocabulary size?
   * How does it impact out-of-vocabulary words (words which are not in the training data, but appear in the test data, or production environment)?
2. (2 point) When building an encoder-decoder model using an RNN, what is the purpose of adding attention?
   * What problem are we trying to solve?
   * How does attention solve the problem?
3. (2 point) In a transformer model what is the multihead attention used for?
   * What are we trying to achieve with self-attention?
   * Why do we use muliple head instead of one?
4. (2 point) In a transformer, what is the purpose of positional embedding?
   * What would be the problem if we didn't use it?
5. (2 point) What are the are the reasons we develop benchmarks to evalute models?
6. (4 points) What are the differences of approach between BERT and GPT?
    * What kind of transformer-based model are they?
    * How are they pretrained?
7. (2 points) How are zero-shot and few-shots learning different from fine-tuning?
    * How do fine-tuning, zero-shot, and few-shot learning affect the model's weights?
8. (2 point) In a few paragraphs, explain how the triplet loss is used to train a bi-encoder model for semantic similarity?
9. (2 point) What is the purpose of using an Approximate Nearest Neighbour method to speed up search?
   * What does it really reduce?

## Evaluation

**This lab is mainly about data and model analysis. There is very little code. Make sure you send back a proper report with your code, guideline, and annotated sheets.**

The assignment will be evaluated on the following criteria.
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

This part provides 18 points + 16 points + 2 points on coding standards: naming, typing, comments, and docstring. You can earn extra points by answering the bonus questions. At the end of the module, all project points are summed and projected on a grade between 0 and 16. The last 4 points can be earned by answering the bonus questions, going further than asked, and presenting a language.

This part has to be send back at `marc.von-wyl` at `epita` dot `fr` before Thursday 24th of November 2022 at midnight.
