---
title: 'Open AI Review Two'
date: 2020-11-06
permalink: /posts/2020/10/open-ai-review-two/
tags:
  - open-ai
  - reinforcement-learning
  - language-models
---

_In the Open AI Scholars program, we write a recap of learning and progress every two weeks. This post is the second such recap._

## Research Direction Update

A couple of weeks ago, my mentor, John Schulman, proposed a simple research idea: what if you could improve a language model’s output using upvotes as a reward signal? For simplicity, I'll refer to this proposal by "Upvotes as Rewards." This proposal was a natural follow-up to the recent Open AI publication “Learning to Summarize from Human Feedback.” This research focused on improving Reddit posts’ summaries by using the information on what summaries people preferred. Using a direct human comparison of two summaries through manual human input ensured good alignment between actual preferences and the reward model. The researchers demonstrated that people preferred the augmented language model over the language model alone. This work was an essential step towards ensuring that the language models satisfy human preferences of correctness and cultural sensitivity. 

The constraint of using manual human input is resource-intensive, so an interesting question is what preferences can be learned directly from upvotes as a reward signal. Upvotes are nice because they are straightforward to gather and because they are a natural extension of the past Open AI work that used a minimum number of upvotes as a hard cutoff for data quality. Overall, "Upvotes as Rewards" was appealing because I could adopt the same architecture as “Learning to Summarize from Human Feedback” while only augmenting the data gathering system to include upvote data. Replicating this architecture would enable me to learn more about Reinforcement Learning, Supervised Learning, and Generative Language Models. The downside of "Upvotes as Rewards" was that no part required any novel architectural or analytical ideas. I wanted to dig deep into some part of a system and understand its mathematical properties.

At the same time that I was thinking about "Upvotes as Rewards,” I was also studying Policy Gradient methods in Machine Learning and learning about the Transformer architecture.  After racking my brain for a couple of days for an angle on "Upvotes as Rewards" that would be mathematically interesting, I noticed some similarities between the Markov Decision Process at the heart of Reinforcement Learning and the Autoregressive problem that Language Models solve. A recent trend in deep learning is expanding the scope of autoregressive models to more problem domains. So far, researchers have applied these models to Language, Images, and Audio. I began to think about what it would look like to embed the Reinforcement Learning problem into an autoregressive model. I then simplified this idea into the question: what would it look like to bias your autoregressive model towards outputting a specific token next? Could you fix your model’s weights and change the input sequence so that the desired token is more likely.

For simplicity, I have referred to this research direction as "Goals in Autoregressive Models." To make progress in this direction, I need to look deeply into the more general question: how does change the input of a neural network while holding the weights fixed affect its output?
