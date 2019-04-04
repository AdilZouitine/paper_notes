# [Playing Atari with Deep Reinforcement Learning](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)

**TLDR** :

- The algorithm will play "like a human" in fact in input these are the raw pixels.
- The model had same architecture and hyperparameters for all games.
- New technique **experience replay**.
- Result : 6/7 game out performed all previous RL algorithms and supassed three human exepert on 3/7 games.


---

**Key points** :

- Convolutional Neural Networks trained with Q-learning.
- Input is pixels.
- Value function predict future recompense.
- They use a technique call **experience replay**. They store the agents experiences at each time-step in dataset.
- Learning directly from consecutive sample is **inefficient**, due the strong correlation between the sample. Sample the buffer break these correlation.
- The buffer does not differentiate important transition.
An more efficient strategy is sampling the transition which we can learn the most. [In 2015 this paper provides the solution : PRIORITIZED EXPERIENCE REPLAY ](https://arxiv.org/pdf/1511.05952.pdf)

- Raw atary image are 210 x 160 with 128 colors pallette. The raw frame was preprocessed from pixel in color to grayscale, downsampled to 160 x 84 and croped to  84 x 84

- The **four last frame** of a history to produce the **input** of Q-learning
(With the last frames we can understand the trajectory of the ball in pong but with only one it is impossible.)

- The neural network architecture is :
    - 16 Conv2D 8x8 filters, stride 4, apply rectifier non linearity
    - 32 Conv2D  4x4 filters, stride 2, apply rectifier non linearity
    - Fully connected with 256 rectifier non linearity
    - Fully connected layer with a single output for each valid action.


---
**My impression** :

- Really well-written paper with good explanations
- The principle of experience replay is very clever, for having tried the vanilla Q-learning (so without the experience replay) the model really has trouble learning
- The principle of adding the N previous images as inputs is very clever because it allows to give the notion of "trajectory".
