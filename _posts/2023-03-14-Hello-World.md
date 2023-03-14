---
layout: post
title: Calibrate Before Use for improving Few-Shot Performance of Language Models
---



<!--- #![_config.yml]({{ site.baseurl }}/images/config.png) <--->

This blog is a report on the Learning from Limited Data in NLP. This blog summarizes the methods & results of the paper: [Calibrate Before Use for improving Few-Shot Performance of Language Models](https://arxiv.org/pdf/2102.09690.pdf)
</br>

GPT-3 can perform numerous tasks when provided a natural language prompt that contains a few training examples known as few shot learning. This research paper finds that few-shot learning can be unstable due to the choice of prompt format, training examples, and even the order of the training examples. This leads to large variance in the accuracies. This paper further focuses on why this instability occurs and how to this instability can be mitigated by a procedure called "contextual calibration".