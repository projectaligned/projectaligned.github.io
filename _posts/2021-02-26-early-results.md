---
title: 'Early Results'
date: 2021-02-26
permalink: /posts/2021/02/early-results
tags:
  - open-ai
  - behavior-cloning
  - reward-modeling
---

# Ambient Human Feedback

My research goal is to radically increase the scope and scale of human feedback used to train language models.
Current methods that use human feedback such as "Learning to Summarize from Human Feedback" rely on hiring expensive contractors.
My active hypothesis is that given a multi-turn dialog corpus we can extract specific dialog acts such as
summarization, explanation, or question-answering from the corpus and then extract the sentiment of the response to the dialog act.
I want to show that the combination of dialog act and sentiment together provide sufficient human feedback to train a model.

## Work So Far

I focused on story-telling as the primary dialog act, and I have used structured feedback in the form of Reddit upvotes.
I have done both behavior cloning and reward modeling using a dataset of story prompts and story completions from reddit.com/r/writingprompts .

### Behavior Cloning

I trained a model based on huggingface's gpt2-xl to generate plausible story completions.
I made some adaptations to the huggingface run_clm.py script to change the prompt+completion padding and
to add a callback that would generate story completions at every save checkpoint for fast feedback.
I used Microsoft's Deepspeed library to fit the 1.5 billion parameter gpt2-xl model
into memory on an azure virtual machine with 4 V100 GPUs and costing almost $10k per month.
I gathered reddit data using the PRAW reddit API, but found that I was limited to the most recent 1,000 prompts,


### Reward Modeling

I then used the reddit upvote data to categorize story completions into three quality tiers: good, ok, or bad.
The story completion score is not a direct measure of the completion's quality because this score is also correlated
with the score of the prompt and also how quickly the completion posted after the prompt.
To control for the score of the prompt, I elected to use the relative score rankings of the story completions for a given post as the primary metric.
The rankings are still confounded by the time of posting, so instead I use an "adjusted ranking"
that is a linear combination of the z-scores for the ranking and the time of posting.
I then binned these adjusted rankings into the three tiers,
and then added the tier to the training data so that the model would receive prompt+completion+score_bin.
This way, given a prompt and a completion for that prompt the model would be able to roughly classify how good the completion was.

## Up Next:
- Using the upvote reward model to optimize an rl policy.
- Merging upvote reward models for two different reddit tasks.
- Building a reward model from child comment sentiment on reddit.
- Using Information Retrieval to locate dialog acts in a multi-turn corpus.
