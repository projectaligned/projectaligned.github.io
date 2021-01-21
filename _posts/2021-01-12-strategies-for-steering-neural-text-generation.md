---
title: 'Strategies for Steering Neural Text Generation'
date: 2021-01-12
permalink: /posts/2021/01/strategies-for-steering-neural-text-generation
tags:
  - open-ai
  - text-generation
---

<!---
# Outline
- Thesis: Steering language models is a high leverage problem, and I have identified a few reasonable strategies to explore.
  - language models are receiving increasing focus.
    - The Scaling Laws papers strongly suggest that increased investment should continue to reduce the loss of the generative models
    - The Learning to Summarize from Human Feedback paper suggests that human labeled data sets can improve the specific task performance of the generative model.
    - These human labeled datasets are expensive to curate because they require motivated human effort over an extended period of time.
  - A couple of natural questions emerge:
    1. Can one learn human preferences to train a reward model without having humans in the loop? How do these "offline" human preferences compare to "online" human preferences?
    2. What is the best way of allocating resources between training a reward model and training a generative model? Does this change as the total resources available change? Is there a limit in which the reward model becomes redundant and the language model is sufficient on its own?
  - I'll explore some strategies for exploring the questions:
    1. Human preferences for text have already been given on any website with a voting system for posts (e.g. Reddit, StackExchange, Quora, Twitter, etc.), this rating data could then be used to fine tune the generative model to produce human preferred results. This might be a cheap and easy way of generically improving language model quality.
       - This kind of quality filtering was already done in a loose sense because gpt-3 was only trained on Reddit posts with at least five karma.
       - This system would also capture negative preference and hopefully penalize toxicity by penalizing the type of language that gets heavily down-voted.
       - Extracting scores from reddit and fine-tuning a gpt-2 model is relatively easy using existing tools.
       - The most time-consuming part of the project is probably evaluating the outputs of the fine-tuned model. This is connected to the general problem of evaluating generative models.
    2. Human preferences for text could be extracted by using a "Task Extractor" language model to identify triples of <task, output, review> in the training corpus. These triples could then be passed into a reward model. This would enable us to train reward models much more cheaply.
       - The hardest part of this project is building the "Task Extractor". This system should be built for a specific task domain like summarization to start. This system could be built using a parser, using keyword search, or trained on lots of examples of summarization commands.
       - Another challenging part of this project would be extracting a numerical score from the rating. This could be based on sentiment analysis.
       - This project would be particularly novel, but also particularly challenging.
    3. The overlap between what the language model learns and what the reward model learns could be probed by reformatting the training data for the reward model as language samples and then fine-tuning the language model on those samples. This would tell us about the "exchange rate" between language model data and reward model data.
       - Instead of using a human preference between two summaries A and B to train a reward model, those summaries could be fed into the language model in the format "A is a better summary than B". I would then evaluate how well the language model with the additional training samples performs compared to the original language model and compared to the trained policy.
       - This is based on the idea that the language model itself learns something about human preference from the training data, and when a prompt is given in the right way, the language model can express those human preferences.
       - This project is effectively an ablation study that seeks to understand how the reward model makes better use of preference data.
       - One speculative hypothesis that I have is that a sufficiently large and well-trained language model actually would not need an additional reward model, because it could accurately infer what humans prefer based on the training data alone.
-->

# The Control Problem

Large Language Models are the most important research topic in machine learning today.
Systems like GPT-3 and their multimodal counterparts command both scientific and popular attention.
Recent work (Scaling Laws for Language Models) explains how their performance grows with increasing scale.
Scientists at many companies (Nvidia, Google, Microsoft) continue to build larger models, with increasing financial investment.
Simultaneously, researchers seek to better control these language models (GEDI, PPLM, AutoPrompt), both for all-purpose generation and for specific tasks.
Recent work demonstrates that human preferences (Learning to Summarize from Human Feedback) can feed reward models that shape the generated language.
Furthermore, new benchmarks (Allen Institute) have been developed that evaluate generative language models using human contractors.
However, gathering these human preferences is expensive.
These two trends of increasing compute investment and human reward investment together suggest the following questions:
1. Can one learn human preferences to train a reward model without having humans in the loop? How do these "stationary" human preferences compare to "interactive" human preferences?
2. What is the best way of allocating resources between training a reward model and training a generative model? Does this change as the total resources available change? Is there a limit in which the reward model becomes redundant and the language model is sufficient on its own?

These related questions drive the following projects that I plan on pursuing:
1. Extracting Human Preferences from upvotes on websites.
2. Extracting Human Preferences from natural languages tasks.
3. Turning Human Preferences into natural language.

I take the approach of quickly exploring a few related ideas rather than focusing entirely on just one.
I base this strategy on the fact that these ideas are all closely related, and therefore code and techniques may easily transfer from one to another.
Furthermore, the need to gather extensive datasets and run large experiments means I would spend a lot of time waiting if I were working on just one idea.
Lastly, my research experience thus far has robustly communicated that my first ideas are not my best ideas, and that rapidly iterating through small projects tends to work best.
I will now explain each of the project ideas in further detail.

# Extracting Human Preferences from upvotes on websites

Human preferences for text have already been given on any website with a voting system for posts (e.g. Reddit, StackExchange, Quora, Twitter, etc.), this rating data could then be used to fine tune the generative model to produce human preferred results.
This might be a cheap and easy way of generically improving language model quality.
This kind of quality filtering was already done in a loose sense because gpt-3 was only trained on Reddit posts with at least five karma.
This system would also capture negative preference and hopefully penalize toxicity by penalizing the type of language that gets heavily down-voted.
Extracting scores from reddit and fine-tuning a gpt-2 model is relatively easy using existing tools.
The most time-consuming part of the project is probably evaluating the outputs of the fine-tuned model. This is connected to the general problem of evaluating generative models.

# Extracting Human Preferences from natural language tasks and responses.

Human preferences for text could be extracted by using a "Task Extractor" language model to identify triples of <task, output, review> in the training corpus.
These triples could then be passed into a reward model.
This would enable us to train reward models much more cheaply.
The hardest part of this project is building the "Task Extractor".
This system should be built for a specific task domain like summarization to start.
This system could be built using a parser, using keyword search, or trained on lots of examples of summarization commands.
Another challenging part of this project would be extracting a numerical score from the rating. This could be based on sentiment analysis.
This project would be particularly novel, but also particularly challenging.

# Turning Human Preferences into natural language.

The overlap between what the language model learns and what the reward model learns could be probed by reformatting the training data for the reward model as language samples and then fine-tuning the language model on those samples.
This would tell us about the "exchange rate" between language model data and reward model data.
Instead of using a human preference between two summaries A and B to train a reward model, those summaries could be fed into the language model in the format "A is a better summary than B".
I would then evaluate how well the language model with the additional training samples performs compared to the original language model and compared to the trained policy.
This is based on the idea that the language model itself learns something about human preference from the training data, and when a prompt is given in the right way, the language model can express those human preferences.
This project is effectively an ablation study that seeks to understand how the reward model makes better use of preference data.
One speculative hypothesis that I have is that a sufficiently large and well-trained language model actually would not need an additional reward model, because it could accurately infer what humans prefer based on the training data alone.



