---
title: 'Open AI Review One'
date: 2020-10-23
permalink: /posts/2020/10/open-ai-review-one/
tags:
  - open-ai
  - reinforcement-learning
  - language-models
---

_In the Open AI Scholars program, we write a recap of learning and progress every two weeks. This post is the first such recap._

## Overview
The [Open AI Scholars Program](https://openai.com/blog/openai-scholars/) is a six-month Deep Learning research program. I work with my mentor [John Schulman](http://joschu.net/) at the intersection of reinforcement learning and language models.

## Starting Project

My mentor proposed this idea in our first meeting: Using upvotes as a reward function to fine-tune language models' output. I'll refer to this project by "Upvotes As Rewards." This project has some similarities to the recent Open AI paper [Learning to Summarize from Human Preferences](https://openai.com/blog/learning-to-summarize-with-human-feedback/) in the sense that it uses a novel RL reward function to fine-tune a language model.

"Upvotes as Rewards" is compelling because it develops a novel reward function and is ambitious but achievable. This project uses my mentor's RL expertise while also reflecting the large scale trend towards language models.

## Starting Syllabus

For "Upvotes As Rewards," I will need to utilize RL and language models. I have some background for RL because I have read Barto and Sutton and have also implemented Tabular Q-Learning and Deep Q-Learning to play generalized tic-tac-toe. My particular focus in RL will be on understanding Online Policy Gradient methods, culminating in understanding Proximal Policy Optimization. For Language Models, I don't have any background, so I will learn what is necessary to understand GPT-3. I will eventually implement proximal policy optimization and transformer models from scratch and integrate them into "Upvotes As Rewards."

## Prototype Plan

I will start by using baseline implementations and pre-trained models to accelerate the prototype development process.

* Once I understand Proximal Policy Optimization, I will use an existing Open AI Baselines implementation for the prototype.
* Once I understand GPT-3, I will use a pre-trained language model implementation for the prototype.
* I will choose a website with prompts, responses, and upvotes to serve as the source of training data (e.g., Reddit or Twitter) and implement a web crawler to fetch the data I need.
* I predict that knowing enough about reinforcement learning and language models to begin working on the project will take four weeks. 
* I predict that implementing the web crawler and gauging the data quality will take two to three weeks.
* I predict that implementing making a pre-trained transformer work on the data will take two to four weeks.
* I predict that implementing and training a stable reward model will take two to four weeks.
* This timeframe still gives me time to run many experiments and potentially implement a transformer model and PPO from scratch during the training and hyperparameter tuning period.

## Next two weeks

I have chosen a subset of tasks to complete within the next two weeks.

* I plan to develop a big-picture view of my project by reading "Learning to Summarize from Human Feedback" and discussing it with one of the paper's authors.
* I plan to complete my understanding of Proximal Policy Optimization by doing the following:
  * Reading chapter three of John Schulman's thesis so that I can understand Trust Region Policy Optimization. I read chapters one and two this past week.
  * Reading the Generalized Advantage Estimators Paper
  * Reading the Proximal Policy Optimization Paper
* I plan to blog twice a week, highlighting interesting statistical details in the papers I read.
* I plan to start studying transformers by learning about autoregressive models from the first two lectures of the UC Berkeley graduate class on Deep Unsupervised Learning.
