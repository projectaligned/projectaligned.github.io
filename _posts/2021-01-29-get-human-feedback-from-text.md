---
title: 'Get Human Feedback from Text.'
date: 2021-01-29
permalink: /posts/2021/01/get-human-feedback-from-text
tags:
  - open-ai
  - text-generation
  - reinforcement-learning-from-human-feedback
---

# The Bottleneck

Reinforcement Learning from Human Feedback depends on lots of human preference data for task output. Prior work has depended on contractors to provide this feedback on an interactive platform. For example, Learning to Summarization from Human Feedback uses summary preferences to feed a gpt-3-based reward model which a gpt-3-based policy is trained against. However, the raw text corpus that gpt-3 is trained on also contains some information about human preferences for summaries. In the text corpus itself, there are examples of summaries together with human judgments of those summaries. More generally, in the text corpus, we may be able to locate tuples of `(task, output, rating)`, for many different tasks. For example, in a task-oriented dialogue within the corpus, we would want to find summarization tasks like: `(task="{context}…could you summarize what you just wrote", output="sure, here is a summary…", rating=sentiment_evaluation("thanks this summary makes sense"))`. My goal is to build a system that can locate these tasks. My hypothesis is that even if I can only detect a small fraction of these tasks in the corpus, it would still exceed the number of tasks that interactive systems with humans in the loop are able to gather.
