# Collaboration
3th (and final) project of Udacity's Deep Learning Nanodegree program

## Instructions

You must first download the environment : 

[Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)

[Mac OSX](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip) 

[Windows 32-bit](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)

[Windows 64-bit](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip) 

## Train and Watch the agent
Training and watching the agent is done in the MADDPG.ipynb notebook. Detailed instructions are present in this notebook.

## Environment 

![movie](https://github.com/rmnfournier/collaboration-competition/blob/master/final.gif)

Two agents control rackets to bounce a ball over a net. They receive a reward of +0.1 for hitting the ball over the net and a reward of -0.01 for letting the ball hit the ground or hitting it out of bounds. Thus, each agent wants to keep the ball in play as long as possible. Each agent perceive a state of dimensionality 24 and must take an action in the real square [-1,1]x[-1,1]. 

The goal is to get a minimum score of 0.5 on average over 100 episodic tasks, where the score for each task is the score of the best agent. 

## Training Curve
The training allowed to solve this task in 3092 episodes. See report.md file for more details. 

![training](https://github.com/rmnfournier/collaboration-competition/blob/master/score.png) 
