---
layout: post
title: Calibrate Before Use for improving Few-Shot Performance of Language Models
---



<!--- #![_config.yml]({{ site.baseurl }}/images/config.png) <--->

This blog is a report on the Learning from Limited Data in NLP. This blog summarizes the methods & results of the paper: [Calibrate Before Use for improving Few-Shot Performance of Language Models](https://arxiv.org/pdf/2102.09690.pdf)

GPT-3 can perform numerous tasks when provided a natural language prompt that contains a few training examples known as few shot learning. This research paper finds that few-shot learning can be unstable due to the choice of prompt format, training examples, and even the order of the training examples. This leads to large variance in the accuracies. This paper further focuses on why this instability occurs and how to this instability can be mitigated by a procedure called **"contextual calibration"**.

## Introduction

First let us see what is  fine-tuning , few-shot learning and few-shot-incontext-learning and also about the GPT-3. 

**Fine tuning** - When you already have a model trained to perform the task you want but on a different dataset, you initialise using the pre-trained weights and train it on target (usually smaller) dataset (usually with a smaller learning rate).

**Few shot learning** - When you want to train a model on any task using very few samples. e.g., you have a model trained on different but related task and you (optionally) modify it and train for target task using small number of examples.

**Few shot in-context learning** - During in-context learning, we give the LM a prompt that consists of a list of input-output pairs that demonstrate a task. At the end of the prompt, we append a test input and allow the LM to make a prediction just by conditioning on the prompt and predicting the next tokens. To correctly answer the prompts, the model needs to read the training examples to figure out the input distribution (financial or general news), output distribution (Positive/Negative or topic), input-output mapping (sentiment or topic classification), and the formatting. More about it can be found here. [The mystery of in-context learning](http://ai.stanford.edu/blog/understanding-incontext/)

**For example:**

**Fine tuning** - Training a model for intent classification and then fine tuning it on a different dataset.

**Few shot learning** - Training a language model on large text dataset and modifying it (usually last (few) layer) to classify intents by training on small labelled dataset.

**Few shot in-context learning** 


![_config.yml]({{ site.baseurl }}/images/incontext.png)

Now let us know a little bit about auto-regressive model GPT-3 and how its training happens

## GPT-3

GPT-3, or the third-generation Generative Pre-trained Transformer, is a machine learning model trained using internet data to generate any type of text. GPT-3 processes text input to perform a variety of natural language tasks. It uses both natural language generation and natural language processing to understand and generate natural human language text. Generating content understandable to humans has historically been a challenge for machines that don't know the complexities and nuances of language, but GPT-3 is trained to generate realistic human text. GPT-3 has been used to create articles, poetry, stories, news reports and dialogue using a small amount of input text that can be used to produce large amounts of copy. GPT-3 can create anything with a text structure and not just human language text. It can also generate text summarizations and even programming code.

**Training**

Training is the process of exposing the model to lots of text.


<img src="https://github.com/gowtham07/gowtham07.github.io/blob/master/images/1.gif?raw=true" alt="gif">
(source  [https://twitter.com/JayAlammar/status/1285848228873801728](https://twitter.com/JayAlammar/status/1285848228873801728))