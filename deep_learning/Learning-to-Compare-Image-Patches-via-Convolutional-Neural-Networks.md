# [Learning to Compare Image Patches via Convolutional Neural Networks](https://arxiv.org/pdf/1504.03641.pdf)

[Source](http://imagine.enpc.fr/~zagoruys/publication/deepcompare/)

Understanding note : **6**

**TLDR** :

![](https://i.ibb.co/LQ5sndy/lam.png)
- Learn directly from image data a general similarity function
- They found an apporach can significantly outperform state of the art on several dataset.

---

**Key points** :
- They only use grey scale during training

- This paper mainly designs three types of network models and their variants

![](https://i.ibb.co/THX9z0S/lamb2.png)

- 2 channels : 
    
    - Concatenate the two patches and put them at the input of the CNN.

- Siamese :
    - The two images are entered into both networks with the same structure for feature extraction.
    - If both branches are set to the same parameters then the network is Siamese otherwise it is pseudo-siamese.

- Central surround :
    

---
**My impression** :