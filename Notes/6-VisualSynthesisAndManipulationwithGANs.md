# Visual Synthesis and Manipulation with GANs
[Source video](https://www.youtube.com/watch?v=I_8Dp_fRzv8&index=9&list=PLazcgz-LJ6ZIrJV-qiqw16JyJFuE4TNKF)   
Speaker: Jun-Yan Zhu, UC Berkeley

## Visual Synthesis
* Generating images, ... from descriptive text, labels

### What makes an image look real/fake?

### Deep Generative Models
* GANs, VAE, DRAW (RNN) [Gregor et al. 2015], Pixel RNN + Pixel CNN [Oord et al 2016]

## Challenges of GANs in vision and graphics
* random, hard to control images
* low-resolution, unrealistic photos


## How to manimulate output images with GANs
* [Zhu et al. 2016] *Generative Visual Manipulation on the Natural Image Manifold*
    * Scribble --hard-coded optimization--> Latent space --pretrained GAN--> Image

* Interactive 3D editing with GANs

### Image-to-Image Networks
* [Isola, Zhu, Zhou, Efros, 2017] *Image-to-Image Translation with Conditional Adversarial Networks*   
![i2i](img/i2i.png)
    * Normal GAN:   
![i2i_1](img/i2i_1.png)   
![i2i_2](img/i2i_2.png)
![i2i_formula](img/formula_GAN.png)
    * Conditional GAN: take the source image into consideration for D   
![i2i_CGAN](img/i2i_CGAN.png)


* More examples:

i2i | i2i
:---:|:---:
![1](img/i2i_ex1.png)|![2](img/i2i_ex2.png)
Edge to image|Sketch to image
![3](img/i2i_ex3.png)|![4](img/i2i_ex4.png)
Edges to cats|Maps
![5](img/i2i_ex5.png)|![6](img/i2i_ex6.png)
Labels to Facades|BW to Color
![7](img/i2i_ex7.png)|![8](img/i2i_ex8.png)
Scribbler|Texture GANs
![9](img/i2i_ex9.png)|![10](img/i2i_ex10.png)
Auto-painter|Multi-view Generation
![11](img/i2i_ex11.png)|![12](img/i2i_ex12.png)
Swapping Fashion|Semantic Image Synthesis
![13](img/i2i_ex13.png)|![14](img/i2i_ex14.png)
Super-resolution|Face Destylization
![15](img/i2i_ex15.png)|
GAN in medical field|

## Conclusions
* Visual synthesis is a learning problem.
* We can to do it with trillions of photos.
* Conditional GANs are much easier to train.
* Build general-purpose tools and find cool problems.

# Code 
#pix2pix   
[PyTorch Implementation](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix)