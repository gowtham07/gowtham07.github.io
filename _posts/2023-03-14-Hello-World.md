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

**Few shot learning** - During in-context learning, we give the LM a prompt that consists of a list of input-output pairs that demonstrate a task. At the end of the prompt, we append a test input and allow the LM to make a prediction just by conditioning on the prompt and predicting the next tokens. To correctly answer the prompts, the model needs to read the training examples to figure out the input distribution (financial or general news), output distribution (Positive/Negative or topic), input-output mapping (sentiment or topic classification), and the formatting. More about it can be found here. [The mystery of in-context learning](http://ai.stanford.edu/blog/understanding-incontext/))

**For example:**

**Fine tuning** - Training a model for intent classification and then fine tuning it on a different dataset.

**Few shot learning** - Training a language model on large text dataset and modifying it (usually last (few) layer) to classify intents by training on small labelled dataset.
