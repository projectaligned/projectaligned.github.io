---
title: 'Strategies for Steering Neural Text Generation'
date: 2021-01-12
permalink: /posts/2021/01/strategies-for-steering-neural-text-generation
tags:
  - open-ai
  - text-generation
---

# Outline
- Thesis: Steering language models is a high leverage problem, and I have identified a few reasonable strategies to explore.
  - language models are receiving increasing investment.
    - The Scaling Laws papers strongly suggest that increased investment should continue to reduce the loss of the generative models
    - The Learning to Summarize from Human Feedback paper suggests that human labeled data sets can improve the specific task performance of the generative model.
    - These human labeled datasets are expensive to curate because they require motivated human effort over an extended period of time.
  - A few natural questions emerge:
    1. Can one learn human preferences to train a reward model without having humans in the loop? How do these "offline" human preferences compare to "online" human preferences?
    2. What is the best way of allocating resources between training a reward model and training a generative model? Does this change as the total resources available change? Is there a limit in which the reward model becomes redundant and the language model is sufficient on its own?
  - I'll explore some strategies for exploring the questions:
    1. Human preferences for text have already been given on any website with a voting system for posts (e.g. Reddit, StackExchange, Quora, Twitter, etc.), this rating data could then be used to fine tune the generative model to produce human preferred results. This might be a cheap and easy way of generically improving language model quality.
    2. Human preferences for text could be extracted by using a "Task Extractor" language model to identify triples of <task, output, review> in the training corpus. These triples could then be passed into a reward model. This would enable us to train reward models much more cheaply.
    3. The overlap between what the language model learns and what the reward model learns could be probed by reformatting the training data for the reward model as language samples and then fine-tuning the language model on those samples. This would tell us about the "exchange rate" between language model data and reward model data.

