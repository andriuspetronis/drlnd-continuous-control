# Project: Continuous Control

The goal of this project project is to move 20 double-jointed arms to target locations and  maintain such position for as many time steps as possible.

![Alt Text](https://video.udacity-data.com/topher/2018/June/5b1ea778_reacher/reacher.gif)

### Project Details

**State:** The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm.

**Action:** Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

**Reward:** A reward of +0.1 is provided for each step that the agent's hand is in the goal location.

**Solution:** Agents must get an average score of +30 (over 100 consecutive episodes, and over all agents). More specifically,

- After each episode, the rewards that each agent received are added up (without discounting), to get a score for each agent. This yields 20 (potentially different) scores. Then the average of these 20 scores is calculated.
- This yields an **average score** for each episode (where the average is over all 20 agents).


### Getting Started
For this project, you could download a pre-built Unity environment from one of the links below. You need only select the environment that matches your operating system:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

Then, place the file in the `data/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(*For Windows users*) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(*For AWS*) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (*To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the Linux operating system above.*)

**Further setup steps to run code locally:**

1. Create a new environment:
```
conda create --name drlnd python=3.6
source activate drlnd
```
2. Install Jupyter notebook:
```
conda install jupyter notebook
```
3. Place extracted `Reacher_Linux` folder in the `data/` directory:
```
./data/Reacher_Linux/Reacher.x86_64
```


### Instructions
Follow the instructions in Continuous_Control.ipynb to get started with training your own agent!

**Note:** The original notebook has been trained on the Udacity DRLND workspace with CPU. Here is the specific line for training the agent:

```
scores = ddpg()
```

**Reference:** [Udacity Deep Reinforcement Learning Nanodegree Program](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893)