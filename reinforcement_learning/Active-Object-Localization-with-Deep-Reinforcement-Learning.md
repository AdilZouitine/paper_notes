# [Active Object Localization with Deep Reinforcement Learning](http://slazebni.cs.illinois.edu/publications/iccv15_active.pdf)

Understanding note : **7**

**TLDR** :

- Use renforcement learning for determine the best bounding box
- The agent can choose between 9 actions
- CNN train with Q-learning
---

**Key points** :

- The sequence of transformations is decided by an agent that analyzes the content of the currently visible region to select the next best action
- Agent receive reward (positive/negative) for each actions
- The reward function is :

	- <a href="https://www.codecogs.com/eqnedit.php?latex=R_{a}\left(s,&space;s^{\prime}\right)=\operatorname{sign}\left(\operatorname{IoU}\left(b^{\prime},&space;g\right)-\operatorname{IoU}(b,&space;g)\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R_{a}\left(s,&space;s^{\prime}\right)=\operatorname{sign}\left(\operatorname{IoU}\left(b^{\prime},&space;g\right)-\operatorname{IoU}(b,&space;g)\right)" title="R_{a}\left(s, s^{\prime}\right)=\operatorname{sign}\left(\operatorname{IoU}\left(b^{\prime}, g\right)-\operatorname{IoU}(b, g)\right)" /></a>
	- 1 if after the action the Intersection over the Union has increased else -1
	- For the trigger action : n and t are hyperparameters  <a href="https://www.codecogs.com/eqnedit.php?latex=R_{\omega}\left(s,&space;s^{\prime}\right)=\left\{\begin{array}{ll}{&plus;\eta}&space;&&space;{\text&space;{&space;if&space;}&space;I&space;o&space;U(b,&space;g)&space;\geq&space;\tau}&space;\\&space;{-\eta}&space;&&space;{\text&space;{&space;otherwise&space;}}\end{array}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?R_{\omega}\left(s,&space;s^{\prime}\right)=\left\{\begin{array}{ll}{&plus;\eta}&space;&&space;{\text&space;{&space;if&space;}&space;I&space;o&space;U(b,&space;g)&space;\geq&space;\tau}&space;\\&space;{-\eta}&space;&&space;{\text&space;{&space;otherwise&space;}}\end{array}\right." title="R_{\omega}\left(s, s^{\prime}\right)=\left\{\begin{array}{ll}{+\eta} & {\text { if } I o U(b, g) \geq \tau} \\ {-\eta} & {\text { otherwise }}\end{array}\right." /></a> 

- Neural network architecture : 
	- 5 conv layer (pretrained)
	- Flatten + 1 action history
	- Fully connected 
	- output 9 actions

- Using a pre-trained CNN as two advantages : 
	- Fast training you just need to update the parameters of Q-Network only
	- The convolution was pre-trained with a larger dataset

- During exploration the agent is allowed to choose one random action from the set of positive actions

- Results :
	- Significantly better than DetNet, MultiBox and Regionlets but little bit worse than R-CNN


---
**My impression** :

- Reward function is very smart