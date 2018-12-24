# Project 3: Collaboration
## Introduction
This project was carried out as part as Udacity's Deep Reinforcement Learning nanodegree program. It was required to implement a multi-agents learning algorithm that teaches two agents to play tennis. Details regarding the environment are available in the Readme.md file, present in the repository. 

Author: Romain Fournier

Date: 24.12.2018

## Description of the implementation
This environment was solved by tunning the DDPG algorithm described in the second project of this course (see continuous control repository). Basically, a super agent called MultiAgentDDPG(MADDPG) handles the training of two DDPG agents, each one of them corresponding to one of the two players. In particular, this MADDPG agent handles a common replay buffer for its two subagents. 

On their side, each one the DDPG agent has :
 1. An actor seeing the state corresponding to its player and performing an action for it 
 2. A critic seeing the whole picture, i.e. the state of both agents, and estimating the action-value function.  

The training procedure goes like this (once again, see continuous control repository for more details about DDPG) : 

 1) States, actions, rewards, next states are collected in a single replay buffer.

2) Each agent samples a batch of experiences from the replay buffer and asks the other agent to propose an action for each state and next states

3) Each agent is trained like DDP agents, with minor differences. The critic takes as input the states of all agents. The best actions and best next actions are estimated thanks to both agents.  

## Neural Network Architecture (For each DDPG agent)
### Critic
 input : 2 states (the ones see by both agents) as a 1x48 vector

 1. ReLU applied on a linear layer (256 units)
 2. Concatenation: add the action at the bottom of the previous output
 3. ReLU applied on a linear layer (256 units)
 4. Linear layer (output dim=1)
 
### Actor
 input : 1 state a a 1x24 vector

 1. ReLU applied on a linear layer (256 units)
 2. ReLU applied on a linear layer (256 units)
 3. Hyperbolic tangent applied on a linear layer (output dim=2)

## Parameters 
1. Learning Rates (actor, critic): 0.0001,0.001
2. Replay Buffer size: 1000000
3. Batch size: 128
4. Gamma : 0.99
5. Number of updates : 5

## Results
The agent managed to solve the task, i.e., reaching an average score of 0.5 over the last 100 episodes, in 3092 episodes. The score of one episode is defined as the best score over both agents. 

![Training](https://github.com/rmnfournier/collaboration-competition/blob/master/score.png)

A movie of the trained agent is available in the repository.

## Ideas for future works
 Improving the model can be done in many ways, for example : 
 
 1. Add the noise to the network itself, as mentioned in [this paper](https://arxiv.org/abs/1706.01905)
 2. Play with the hyperparameters to converge faster toward a winning agent
 3. Implement a prioritized replayed-buffer 
 4. Train two pairs of agents, and then switch the partners, to see if they are able to play with another player.
 
 It would also be intersting to test this approach in a competitive scenario. 
   
