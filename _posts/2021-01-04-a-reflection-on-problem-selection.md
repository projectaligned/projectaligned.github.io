---
title: 'A Reflection on Problem Selection'
date: 2021-01-04
permalink: /posts/2021/01/a-reflection-on-problem-selection.
tags:
  - open-ai
  - problem-selection
---

# On Incrementalism

At the start of the scholars program I did not have a clear idea of what to work on for the remainder of the program.
I still do not have a clear idea of what to work on for the remainder of the program. Unlike at the beginning, I am
now comfortable with this state of ambiguity. Instead of aiming to control the outcome months from now, I have decided
to focus on concrete execution every day. In practice this means that I aim to create one new type of plot a day every day.
This can mean that I have new way of generating data, a new way of analyzing the data, or a new way of visualizing data.
Regardless how or what precisely, it means that I am learning something new. I trust myself to steer each next incremental
step in an interesting direction.

In many ways, this mindset of incremental improvement mirrors the stepwise optimization process at the heart of modern deep learning.
The stochastic gradient descent optimizer takes a sequence of small steps through the high dimensional [loss landscape](https://losslandscape.com/gallery/).
These small steps together enable the optimizer to reach a surprisingly good minimum of the loss function. The high-dimensionality of the space
means that there usually exists a direction to continue the optimization procedure in without getting stuck.

I believe a similar truth applies to picking my research direction. At each step of my research journey, there are so many things to try
that I am never worried about running out ideas or getting stuck. The most important thing has been having a clear vision of what problem is worth solving.
In some sense, this choice of problem is similar to the choice of the loss function itself. I have found that trying to plan out a solution to the problem
from the start is unlikely to succeed. For example, during the scholars program I have been focused on the problem of how to use a language model to generate text
that is good according to some metric. I spent three days working on a project proposal that I thought would solve the problem outright. The proposal document was
pretty, and my presentation was well-received, but the idea had a simple flaw at its core.
Thankfully my mentor pointed out this flaw in our meeting after the presentation.
Ultimately I should have spent more time testing out the simple ideas at the core of the proposal.

# On Problem Selection

While I believe in choosing simple steps at each stage of solving the problem, I believe that the problem itself must also be worth solving.
This points towards a picking an ambitious problem. Choosing a visionary problem has the added benefit that it provides more motivation.  
The challenge then becomes reconciling the necessarily small solution steps with the necessarily big problem. One strategy is to find a sequence  
of simpler approximations, such that the insights from the easier problems still transfer to the harder problems. This is the dominant strategy in  
physics, where research often consists of solving model systems where complexities are represented as perturbations. A guiding principle in physics is the
idea that the more complex theory must also capture the properties of the simpler theory in a certain limit. In this way, quantum mechanics encapsulates classical mechanics
in the [high action limit](https://en.wikipedia.org/wiki/Classical_limit), and general relativity encapsulates Newtonian gravity in the [limit of slow speeds and weak gravitation](https://en.wikipedia.org/wiki/Newtonian_limit).
Though physics is of course different from AI research, with the recent exploration of scaling laws for transformer models, it appears that a new focus on how to transfer insights
across problem scales has emerged.

In conclusion, I have not quite figured out the best way of subdividing a big problem into smaller problems that can be tackled incrementally,  
but I will write more when I learn more. In the meantime, its just one new plot a day.

