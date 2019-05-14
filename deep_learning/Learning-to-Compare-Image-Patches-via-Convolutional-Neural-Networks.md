# [Learning to Compare Image Patches via Convolutional Neural Networks](https://arxiv.org/pdf/1504.03641.pdf)

[Source](http://imagine.enpc.fr/~zagoruys/publication/deepcompare/)

Understanding note: **5**

**TLDR** :

![](https://i.ibb.co/LQ5sndy/lam.png)
- Learn directly from image data a general similarity function
- They found an approach can significantly outperform state of the art on several datasets.

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

**This is the part I least understood of the paper.**
- Central surround : 
    - Perform two operations on a 64 x 64 image. One is to capture the central 32x32 patch to form a central patch, and once, the original image is down-sampled at half to obtain a surround patch. In this way, the information in the middle of the image is used twice, so that the information in the intermediate image has a greater impact on the final result.

- Spatial pyramid pooling at the end of the feature extraction block. (Handle multi-resolution).

- Optimisation :

    - Objective function : <a href="https://www.codecogs.com/eqnedit.php?latex=\min&space;_{w}&space;\frac{\lambda}{2}\|w\|_{2}&plus;\sum_{i=1}^{N}&space;\max&space;\left(0,1-y_{i}&space;o_{i}^{n&space;e&space;t}\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\min&space;_{w}&space;\frac{\lambda}{2}\|w\|_{2}&plus;\sum_{i=1}^{N}&space;\max&space;\left(0,1-y_{i}&space;o_{i}^{n&space;e&space;t}\right)" title="\min _{w} \frac{\lambda}{2}\|w\|_{2}+\sum_{i=1}^{N} \max \left(0,1-y_{i} o_{i}^{n e t}\right)" /></a>

    - SGD
    - Batch size 128

- Data augmentation 
    - Rotation (90, 270)
    - Horizontal/Vertical flip

- Results: 2ch-2stream get the best results

---
**My impression** :

- This paper presents us well to make CNN's to learn the similarity between two images.

- I need to know more now about Spatial pyramid pooling. 