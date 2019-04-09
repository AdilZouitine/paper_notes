# [Proximal Policy Optimization Algorithms](https://arxiv.org/pdf/1707.06347.pdf)

[**HUGE THANKS TO ARXIV INSIGHTS CHANNEL**](https://www.youtube.com/watch?v=5P7I-xPq8u8)

Understanding note : **7**

**TLDR** :

- New family of policy gradient methods for reinforcement learning
- Open AI propose a method scalable, data efficieny and robust.
- Easy to implement 
---

**Background** : 

<!---
L^{PG}(\theta) = \hat{\mathbb{E}}_t[log_\pi_\theta(a_t|s_t) \hat{A}_t]
-->

<a href="https://www.codecogs.com/eqnedit.php?latex=L^{P&space;G}(\theta)=\hat{\mathbb{E}}_{t}\left[\log&space;\pi_{\theta}\left(a_{t}&space;|&space;s_{t}\right)&space;\hat{A}_{t}\right]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?L^{P&space;G}(\theta)=\hat{\mathbb{E}}_{t}\left[\log&space;\pi_{\theta}\left(a_{t}&space;|&space;s_{t}\right)&space;\hat{A}_{t}\right]" title="L^{P G}(\theta)=\hat{\mathbb{E}}_{t}\left[\log \pi_{\theta}\left(a_{t} | s_{t}\right) \hat{A}_{t}\right]" /></a>

- log(probabilities) from the output of the policy network
time the Advantage function (estimate of the relative value of selected action in the current state )


-  The idea between Advantage function "What is the action that our agent took was it better than expected or was it worse"

- Policy gradient loss : Multipling the log of probability and this avantage function

- **This objective function doing is** : 

	- If the avantage estimate was positive meaning that the action took by the agent in the sample trajectory resulted in better than average return we'll do is increase the probability of selecting this action in the future when we encouter the same state ( gradient is positive, increase these action probability )

	- If the avantage estimate was negative meaning the action took by the agent in the sample trajectory resulted in worst than average return we'll do is decrease the probability of selecting this action in the future when we encouter the same state ( gradient is negative, decrease these action probability )

- Trust region policies optimization :

	- If the network parameters are updated far away it may destroy the policy,
	The TRPO methods aim to correct this problem 


---

**Key points** :
- **Clipped Surrogate Objective**

<a href="https://www.codecogs.com/eqnedit.php?latex=L^{C&space;L&space;I&space;P}(\theta)=\hat{\mathbb{E}}_{t}\left[\min&space;\left(r_{t}(\theta)&space;\hat{A}_{t},&space;\operatorname{clip}\left(r_{t}(\theta),&space;1-\epsilon,&space;1&plus;\epsilon\right)&space;\hat{A}_{t}\right)\right]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?L^{C&space;L&space;I&space;P}(\theta)=\hat{\mathbb{E}}_{t}\left[\min&space;\left(r_{t}(\theta)&space;\hat{A}_{t},&space;\operatorname{clip}\left(r_{t}(\theta),&space;1-\epsilon,&space;1&plus;\epsilon\right)&space;\hat{A}_{t}\right)\right]" title="L^{C L I P}(\theta)=\hat{\mathbb{E}}_{t}\left[\min \left(r_{t}(\theta) \hat{A}_{t}, \operatorname{clip}\left(r_{t}(\theta), 1-\epsilon, 1+\epsilon\right) \hat{A}_{t}\right)\right]" /></a>

 	- Optimization of expectation taking the minimum of two parameters
	- The first term is the normal objective of a policy gradient
	- The second term is clipped version of normal policy gratients objective
	- The clip is here for limit the effect of the gradient update

- PPO objective : Force the policy update to be conservative if they move far
away from the current policy

- PPO often outperform TRPO

- **Final training objective in PPO**: 

<a href="https://www.codecogs.com/eqnedit.php?latex=L_{t}^{C&space;L&space;I&space;P&plus;V&space;F&plus;S}(\theta)=\hat{\mathbb{E}}_{t}\left[L_{t}^{C&space;L&space;I&space;P}(\theta)-c_{1}&space;L_{t}^{V&space;F}(\theta)&plus;c_{2}&space;S\left[\pi_{\theta}\right]\left(s_{t}\right)\right]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?L_{t}^{C&space;L&space;I&space;P&plus;V&space;F&plus;S}(\theta)=\hat{\mathbb{E}}_{t}\left[L_{t}^{C&space;L&space;I&space;P}(\theta)-c_{1}&space;L_{t}^{V&space;F}(\theta)&plus;c_{2}&space;S\left[\pi_{\theta}\right]\left(s_{t}\right)\right]" title="L_{t}^{C L I P+V F+S}(\theta)=\hat{\mathbb{E}}_{t}\left[L_{t}^{C L I P}(\theta)-c_{1} L_{t}^{V F}(\theta)+c_{2} S\left[\pi_{\theta}\right]\left(s_{t}\right)\right]" /></a>

	- Clip PPO objective
	- Second term updating the baseline network (Value Head)
	- Last term is entropy his role is to be the agent doing enough exploration

- Achitecture : 
	-  2 head  => Policy head and Value head
	-  The policy network returns a distribution and the agent will sample this distribution to do its action. The advantage is that the exploration is done in this way and the more converged the network converges, the less it will explore. Because indeed the probabilities of taking an action for a given state will be higher and higher for one action and therefore much lower for the others.


---
**My impression** :

- A lot of math behind but the researchers' intuition is simple. The result is elegant.
- Very well written paper.
- This is the paper where I had to take the longest time to understand for now.


