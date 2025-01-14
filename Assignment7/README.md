# Assignment 7

_For more background context, I would recommend reading the README of the main (Supervised-NLP-Models) repository_

## Description

This purpose of the repository in general is to analyse Hindi Facebook data for hate speech. One of many ways of doing this is by using pre-trained language models and fine tuning them to perform sentiment analysis.<br>
In this folder, one such activity is run. A dataset is provided of 9074 facebook posts in mostly Hindi within this folder, containing the post, and the manually allocated sentiment score. <br>
However, some of the entries contain English words, hashtags in the Roman alphabet, and so on; hence the need for a multilingual language model rather than a monolingual Hindi language model. When working with Hindi data, this is almost always the case.<Br>

In brief, the notebook in this folder does the following:<br>
* Loads the dataset, and processes it
* Retrieves the desired NLP model from HuggingFace
* Runs the model with the data using PyTorch
* Outputs predictions
* Plots a histogram of these predictions
* Computes Accuracy, Precision, Recall, and Macro-F1 score.

## More in-depth information & resources.
<Br>
As this is an ipynb file, using a notebook such as Jupyter Notebook is required. Running this on Google Colab should also be fine insofar as the csv is accessible.<Br>
<br>
**Requirements** - Those are taken care of by running the !pip install commands (transformers, sentencepiece, and pip upgrade). The other libraries which are needed are SciPy and NumPy (a reasonably up to date version). There haven't been any errors observed yet with installing, so let me know if you come across any.<br>
If an external download is necessary, then one tip is to run through Anaconda instead of Miniconda as Miniconda may not have these libraries in its package.<br>
<br>
The CSV for running this particular experiment has two columns, "review" and "sentiment". Review is the actual text to review, whereas sentiment is the score given by a human (by people manually reading these and manually assigning a score to them).<br>
The data behind this CSV comes from CrowdTangle, a Facebook API which circumvents having to scrape Facebook manually.<br>
The model used for evaluation is twitter-xlm-roberta-base-sentiment, an NLP trained on 198 million tweets. Here's more info about it: https://huggingface.co/cardiffnlp/twitter-xlm-roberta-base-sentiment?text=I+love+you%21<br>
The evaluation is split into 3: negative, neutral and positive, where negative implies being hateful, harassment, etc.<br>
The code has comments around it explaining which bits do what, and have further resources allocated to them.<br>

## What's the point of this?
As the results show, there is a large amount of negative sentiment, and that the NPL model has an accuracy of between 60-70%.<br>
Since this is CrowdTangle data, we know that this is data that is still up on Facebook, content deleted for violating Facebook's Terms of Use do not appear in CrowdTangle. As such, there should be no (or very little) negative sentiment. However, it has been noted that Facebook has done a poor job of moderating hateful communities in India which speak predominantly in Hindi. This is the motivation behind the whole folder (not just this assignment).<br>
By running predictions we can do two things: We can show that models are able to detech this negative sentiment (and by extension, so should Facebook), and we can also evaluate how well different models are able to do these predictions, and perhaps improve upon them.
