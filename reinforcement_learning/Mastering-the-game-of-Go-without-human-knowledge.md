# [Mastering the game of Go without human knowledge](https://www.nature.com/articles/nature24270.pdf)

Understanding note : **7**

**TLDR** :

- AlphaGo Zero reach superhuman level without human knowledge in the process
- One neural network for estimate move probabilities and position evaluation
- A great achievement in artificial intelligence (Buzzword)

---

**Key points** :

- Neural networks were **combined** with Monte Carlo tree search 

- Game state is 19x19x17 stack:
	- current position of black/white's (1x2)
	- The position of the black/white stones from the previous 7 rounds (7x2) 
	- All 1 if black to play/ All 0 if white to play (1x1) 

- AlphaGo Fan/Lee use two deep neural network :
	- Policy network outputs move probabilities
	- Value network outputs a position evaluation
	- First train with supervised learning 
	- Second train with Policy-gradient

AlphaGo Zero differs from AlphaGo Fan/Lee :

- Train by self-play reinforcement learning
- Only use black and with stone from the board as input features
- Use single neural network with **2 head** (Policy head and Value Head)

- In each state MCTS is **guided** by neural network.
- AlphaGo Zero outperform AlphaGo Lee after **36h** of training.

- Supervised learning achieved a better initial performance (obvious) and
self-learned player performed much **better overall**

- AlhpaGo Zero may be learning a strategy that is qualitatively **different** to human play

Achitecture : 

- 40 residual layer  : 
	- Conv 256 filters  3x3 kernel 
	- BN 
	- ReLu 
	- Conv 256 filters  3x3 kernel 
	- BN 
	- Skip connection 
	- ReLu

- Policy head :

	- Conv 2 filters 1x1 kernel 
	- BN 
	- ReLu 
	- Fully connected 19x19 +1 (for pass) move logit probabilities )

- Value head : 
	- Conv 1 filter 1x1 kernel
	- Batch normalisation
	- ReLu
	- Fully connected layer
	- ReLu
	- Fully connected layer
	- Tanh [-1, 1] (game value for current player)

Improvements :

- **DualresNet** architecture have the best elo rating
- Residual network increase the performance of AlphaGo by over 600 elo
- Combining policy and value in single neural network increase the performance of AlphaGo by another 600 elo



---
**My impression** :

- The way the game state was made is super brilliant
- Residual architecture always wins
- Prunned the Monte Carlo tree is super smart.
- Check out the AlphaGo documentary on Netflix it's epic
