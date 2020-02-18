# Project: Continuous Control

The goal of this project project is to move 20 double-jointed arms to target locations and  maintain such position for as many time steps as possible.

![Alt Text](https://video.udacity-data.com/topher/2018/June/5b1ea778_reacher/reacher.gif)

### Learning Algorithm
Deep Deterministic Policy Gradient (DDPG) algorithm has been used to train the agents. In general, it learns both a Q-function and a policy at the same time. More specifically, the algorithm use off-policy data together with the Bellman equation for finding the Q-values, while the policy uses the Q-function. More detailed description could be found [here](https://spinningup.openai.com/en/latest/algorithms/ddpg.html).

**Quick Facts**
Here are some quick facts abou the DDPG algorithm from OpenAI:
- DDPG is an off-policy algorithm.
- DDPG can only be used for environments with continuous action spaces.
- DDPG can be thought of as being deep Q-learning for continuous action spaces.

**Pseudocode**
Authors in the [Continuous control with deep reinforcement learning](https://arxiv.org/abs/1509.02971) paper summarises DDPG algorithm using the following pseudocode:

![Pseudocode](https://i.imgur.com/HVYe1A7.png)

Some of these steps are not straight-forward and might require additional explanation.

**Replay buffer**
The main idea behind the replay buffer is to generate a finite number of experiences (state, action, reward, next state) and store them into a cache. Later, this buffer is used for sampling mini-batches needed for updating both policy (Actor) and value (Critic) networks. As a result, this helps to decorrelate experiences used for training and should lead to some better convergence properties.

**Actor and Critic network updates**
The updates of the value network are similar to those in the Q-learning algorithm. However, in this situation next state values are calculated based on the value and policy target networks. Later, the goal is to minimaze a mean-squared loss between original and updated Q values.

**Target network updates**
Soft updates are used for target network, meaning that its weights are slowly blending into the weights of the corresponding regular network. So, there is a slight mismatch between both target and regular networks.

**Exploration**
Instead of using epsilon-greedy exploration for selecting actions, DDPG alorithm adds noise to the action itself. This is needed as the algorithm deals with continuous actions, so the same logic could not apply as with distrete action spaces.

**Hyperparameters**

| Parameter | Value | Description |
|---|---|---|
| n_episodes | 2000 | maximum number of training episodes |
| max_t | 1000 | maximum number of timesteps per episode |
| BUFFER_SIZE | 1e6 | replay buffer size |
| BATCH_SIZE | 1024 | minibatch size |
| GAMMA | 0.99 | discount factor |
| TAU | 1e-3 | for soft update of target parameters |
| LR_ACTOR | 1e-4 | learning rate of the actor |
| LR_CRITIC | 3e-4 | learning rate of the critic |
| WEIGHT_DECAY | 0 | L2 weight decay |

**Neural network architecture**
The neural network consists of two hidden layers (`first_layer_size = 256` and `second_layer_size = 128`) for both Actor and Critic. Also, it uses a **rectified linear unit (ReLU)** activation function for Actor and **leaky rectified linear unit (Leaky ReLU)** for Critic. More information about the network architecture could be found in the `model.py` file.


### Plot of Rewards
The environment is considered solved after agents get an average score of +30 (over 100 consecutive episodes, and over all agents). The current architecture allows the agent to solve it over 55 episodes.

```
Episode 10	Average Score: 0.84
Episode 20	Average Score: 1.40
Episode 30	Average Score: 2.45
Episode 40	Average Score: 3.92
Episode 50	Average Score: 5.61
Episode 60	Average Score: 7.60
Episode 70	Average Score: 9.92
Episode 80	Average Score: 12.29
Episode 90	Average Score: 14.50
Episode 100	Average Score: 16.04
Episode 110	Average Score: 19.10
Episode 120	Average Score: 22.22
Episode 130	Average Score: 24.96
Episode 140	Average Score: 27.35
Episode 150	Average Score: 29.29
Episode 155	Average Score: 30.01
Environment solved in 55 episodes!	Average Score: 30.01
```

A plot of rewards per episode:

![Rewards plot](https://i.imgur.com/vBTrjwT.png)

### Ideas for Future Work
It would be possible to experiment with alternative algorithms. For instance, it wold be possible to implement algorithms like [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience. Also, it might be interesting to try other more complicated environments (i.e. [Crawler](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#crawler)).

**Reference:** 
[Udacity Deep Reinforcement Learning Nanodegree Program](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893)
[Deep Deterministic Policy Gradients Explained](https://towardsdatascience.com/deep-deterministic-policy-gradients-explained-2d94655a9b7b)
[OpenAI](https://spinningup.openai.com/en/latest/algorithms/ddpg.html)