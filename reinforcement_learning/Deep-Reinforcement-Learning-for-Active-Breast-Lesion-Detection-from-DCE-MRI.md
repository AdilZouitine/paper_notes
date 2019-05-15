# [Deep Reinforcement Learning for Active Breast Lesion Detection from DCE-MRI](https://cs.adelaide.edu.au/~gabriel/DRL_maicasEtAl.pdf)

Understanding note : **8**

 

**TLDR** :

 

- The main objective is to have a state of the art performance and less inference time using deep reinforcement learning.

- Paper very inspired by [Active Object Localization with Deep Reinforcement Learning](http://slazebni.cs.illinois.edu/publications/iccv15_active.pdf) | [Note here](https://github.com/AdilZouitine/paper_notes/blob/master/reinforcement_learning/Active-Object-Localization-with-Deep-Reinforcement-Learning.md)

-  ResNet + Q-learning

 

---

 

**Key points** :

 

- Dataset : Set of 3D Breast from DCE-MRI

- Action space :

    - Set of 9 actions: 6 for shifting, 2 for scaling and 1 trigger

- Reward function :

 

All actions except triggering:

 

<a href="https://www.codecogs.com/eqnedit.php?latex=r\left(\mathbf{o},&space;a,&space;\mathbf{o}^{\prime}\right)&space;:=\operatorname{sign}\left(d\left(\mathbf{o}^{\prime},&space;\mathbf{s}\right)-d(\mathbf{o},&space;\mathbf{s})\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?r\left(\mathbf{o},&space;a,&space;\mathbf{o}^{\prime}\right)&space;:=\operatorname{sign}\left(d\left(\mathbf{o}^{\prime},&space;\mathbf{s}\right)-d(\mathbf{o},&space;\mathbf{s})\right)" title="r\left(\mathbf{o}, a, \mathbf{o}^{\prime}\right) :=\operatorname{sign}\left(d\left(\mathbf{o}^{\prime}, \mathbf{s}\right)-d(\mathbf{o}, \mathbf{s})\right)" /></a>

 

Triggering:

 

<a href="https://www.codecogs.com/eqnedit.php?latex=r\left(\mathbf{o},&space;a,&space;\mathbf{o}^{\prime}\right)&space;:=\left\{\begin{array}{ll}{&plus;\eta,}&space;&&space;{\text&space;{&space;if&space;}&space;d\left(\mathbf{o}^{\prime},&space;\mathbf{s}\right)&space;\geq&space;\tau_{w}}&space;\\&space;{-\eta,}&space;&&space;{\text&space;{&space;otherwise&space;}}\end{array}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?r\left(\mathbf{o},&space;a,&space;\mathbf{o}^{\prime}\right)&space;:=\left\{\begin{array}{ll}{&plus;\eta,}&space;&&space;{\text&space;{&space;if&space;}&space;d\left(\mathbf{o}^{\prime},&space;\mathbf{s}\right)&space;\geq&space;\tau_{w}}&space;\\&space;{-\eta,}&space;&&space;{\text&space;{&space;otherwise&space;}}\end{array}\right." title="r\left(\mathbf{o}, a, \mathbf{o}^{\prime}\right) :=\left\{\begin{array}{ll}{+\eta,} & {\text { if } d\left(\mathbf{o}^{\prime}, \mathbf{s}\right) \geq \tau_{w}} \\ {-\eta,} & {\text { otherwise }}\end{array}\right." /></a>

 

Where d is dice coefficient.

 

- Deep Q-Learning:

    - Experience replay (10 k observation)

    - Target Network

    - Adam (1 x e-6)

 

 

- Agent:

   - The agent is allowed to do a maximum of 20 steps or no lesions are detected

   - "Guided exploration" : Agent will select randomly an action that produces a positive reward.

   - The agent starts with a box covering 75% of the tensor.

  

- The researchers explain of the most important parameter is a good trade-off between exploration and exploitation

 

---

**My impression** :

 

The principle of allowing the agent to do a maximum of 20 steps before the end of the episode seems interesting to me.