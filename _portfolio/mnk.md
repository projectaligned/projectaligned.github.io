---
title: "MNK game environment for Deep RL."
excerpt: "A Deep Reinforcement Learning environment using generalized tic-tac-toe.<br/><br/><img src='/images/mnk.png' width='400'>"
collection: portfolio
---

[On Github](https://github.com/projectaligned/mnk)

## Outline
This project includes the following:
- A Board object which can have a variable number of rows and columns.
- A Win detection function which can detect wins for variable number of required tokens in a row.
- A Game Tree which represents the sequence of moves made and pruned explorations from those moves.
- Many Agents, ranging from a trivial bot which simply makes randomized moves up to more sophisticated bots using Minimax, Tabular Q Learning, and Deep Q Learning.
- A Competition function to train bots with self-play and also to compare different bots against each other.
- Tests with extensive coverage for all of the above.
