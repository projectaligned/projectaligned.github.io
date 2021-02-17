---
title: 'Get Human Feedback from Reddit.'
date: 2021-02-12
permalink: /posts/2021/02/get-human-feedback-from-reddit
tags:
  - open-ai
  - text-generation
  - reddit
  - behavior-cloning
---

# Rewards From Reddit

I am using https://www.reddit.com/r/WritingPrompts/ to test whether human feedback from the environment is a suitable reward signal for reinforcement learning. In the case of Reddit, the reinforcement learning setup is the following. The state is the writing prompt, the action is the response to the prompt, and the reward is the karma of the response.
So far, I have focused on behavior cloning before doing reinforcement learning. In particular, I have fine-tuned gpt-xl with 1.5 billion parameters on 10 MB of Reddit prompt and response pairs.

## An Example Task

###  Prompt:

_[WP] you arrive home late one night from work, only to find that your home has become a museum honoring you.
It looks as if someone went to great lengths to decorate it to look like you lived there._

### Generated Response:

_“I’m crazy,” I say, “You shouldn’t have made me look like the antiques dealer.”“Well, I suppose that’s the way things are,” she shrugs.
“But no,” she says, “we aren’t crazy here. We’re just here, to honour you.” 
I want to argue with her, but I can’t, not when her voice breaks me. 
I want to tell her everything, but the truth is I only have so much time.“I was there when the whole thing happened. 
It’s weird; I know this house has special powers. Like there’s magic in it. And that’s what makes us so special. 
I can see what will happen if I choose right.”I don’t even know how I chose, or why I chose to not save her. 
Maybe it was by chance or fate, but I can no longer save her. I can’t undo the choices that I made, even if I wanted to.
So I stand there, in my tiny room, surrounded only by the cold walls and the blank canvas that is my bathroom. 
The light is soft, almost ghostly at night. The smell of the soap makes me shiver, even now. The clock ticks. 
My thoughts turn. I wonder if the others are gone. I wonder if this is some elaborate prank, because I feel so helpless. 
I don’t know how I know this house has powers, but maybe it should have taught me something, by now. 
Then maybe this world wouldn’t have been so hard for me, and everyone else. I try to remember. I just can't. 
“You’re crazy,” she says, and her tone is soft now. My whole body is shaking, and it takes my breath away. 
“I knew one day you’d say that to me.”I’m silent. I haven’t said anything. I’m not even sure what I’m doing._

Most of the effort so far has been in scaling my infrastructure. In particular, the Deepspeed library has been necessary to enable moving from the 117 million parameter model that I was prototyping on to the full 1.5 billion parameter model. Without the Deepspeed memory optimizations, the A100 GPUs I am using for training would not have had sufficient memory to hold the model. In particular, mixed-precision training, activation checkpointing, and gradient checkpointing have been critical for reducing memory usage.

My next steps are to experiment with learning rate schedules and to do further data preprocessing so that none of the prompt-completion pairs get truncated by the transformer block.
