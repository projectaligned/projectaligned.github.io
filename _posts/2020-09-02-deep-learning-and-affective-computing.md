---
title: 'Deep Learning and Affective Computing'
date: 2020-09-01
permalink: /posts/2020/09/deep-learning-and-affective-computing/
tags:
  - affective-computing
  - deep-learning
  - open-ai
---

_This post is excerpted from my response to the Open AI Scholars application asking why I want to study deep learning._

My goal is to learn the deep learning techniques necessary to implement state-of-the-art Affective Computing research. 

I have worked on optimization in several forms. At Rigetti on the applications engineering team with Johannes Otterbach, I applied continuous and discrete quantum optimization to operations research. At Sisu, I have contributed to building a data analysis platform based on the A Priori algorithm for association rule learning.

Over the past year, I have reflected on what we choose to optimize individually and as part of organizations. I have decided to use optimization to help people achieve their psychological goals. This interest has led me to Affective Computing and the work done by Rosalind Picard's group at the MIT Media Lab. My long-term goal extending beyond the Scholars Program is to build a platform that assists introspection and offers behavioral recommendations to help people achieve their psychological goals. I have also begun working on a prototype system myself.

For months, I have collected data daily in a Google spreadsheet on my overall happiness and productivity for the day and approximate time spent on various activities. My goal here has been to determine the causal factors. This process is similar to the association rule learning at the core of Sisu, albeit applied to a very different dataset. There were two limitations to this manual collection process. The first is that it was time-consuming to record by hand. The second is that there were systemic gaps in when I recorded data. These limitations caused me to recognize the benefit of automatically inferring my approximate happiness based on my behavioral data.

I learned that this concept of inferring physiological or psychological state fits within Affective Computing. For example, Ehimwenma Nosakhare from the Picard group has used supervised Latent Dirichlet Allocation (sLDA) to infer causal factors for happiness, health, and stress from smartphone usage patterns. Other papers also use more direct Deep Learning approaches. Terumi Umematsu et al. used LSTM models to forecast student stress. Likewise, Natasha Jacques et al. used multi-task learning to build personalized mood, health, and stress predictions. Also, Ognjen Rudovic et al. used Multi-Modal Deep Reinforcement Learning to improve task engagement estimation. These examples show that state-of-the-art Affective Computing research relies heavily (but not entirely) on Deep Learning Methods.

My interest in Deep Learning and especially Reinforcement Learning predates my interest in Affective Computing. I was a member of the Harvard College Go Club when AlphaGo beat Lee Sedol. This surprising upset propelled me to read Barto and Sutton’s Reinforcement Learning book. I then built a generalized Tic-Tac-Toe environment for comparing RL algorithms, which extended to an arbitrary number of rows, columns, and tokens-in-a-row required. I compared agents using classical minimax, tabular q-learning, and deep q-learning. I am excited to continue building upon this experience, now applied to a domain that I find both fun and meaningful. 