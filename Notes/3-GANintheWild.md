# GANs in the wild
[Source Video](https://www.youtube.com/watch?v=Qc1F3-Rblbw&list=PLazcgz-LJ6ZIrJV-qiqw16JyJFuE4TNKF&index=5)

* Comparision to Classification Convnets
    * Try different things and see what works
    * Intuition is poorer
    * Theoretical work is somewhat improving but still far away
    * Objective validation metrics are not there yet

## HOW TO TRAIN GAN (Tips and Tricks)
For a stable GAN :D
1. Normalize the inputs
    * normalize images between -1 and 1
    * tanh as the last layer of the generator output ( or some differentiable function)

2. Modified loss function
    * dont use min(log(1-D))
    * in practice, flips the labels when training generator: fake = real, real = fake
    * [GAN models in PyTorch](https://github.com/znxlwm/pytorch-generative-model-collections)
    * [GAN models in TF](https://github.com/hwalsuklee/tensorflow-generative-model-collections)

3. Use spherial z
    * interpolation via great circle
    * Tom White "Sampling Generative Networks"
        * arxiv.org/abs/1609.04468

4. BatchNorm
    * different batches for real and fake
    * If cant use BN, use **instance norm**

5. Avoid Sparse Gradients: ReLU, MaxPool
    * stability will suffer
    * Use Leaky **ReLU**
    * Downsampling: Avgpool, Conv w/ stride
    * Upsampling: PixelShuffle, ConvTranspose w/ stride

6. Soft and Noisy labels
    * Label smoothing
    * making the labels noisy a bit for the D

7. Architectures: DCGANs, Hybrid
    * DCGAN when u can, seems pretty good
    * If not and no model is stable: Hybrid (KL + GAN or VAE + GAN)
    * Width matters more than Depth

8. Stability tricks from RL (Reinforcement Learning)
    * Experience replay

9. Optimizer: Adam
    * SGD for Discriminator, Adam for Generator (maybe)
    * Adam in general is good in both cases

10. Gradient Penalty
    * Regularize the norm of gradients

11. Don't balance via loss statistics

12. If you have labels, use them
    * Auxillary GANs: train the D to also classify the samples

13. Add noise to inputs, decay over time
    * Add noise to inputs
    * Add Gaussian noise to every layer of G (Zhao et al.)

14. Train discriminator mroe
    * especially when there are noises
    * WGAN/WGAN-gp papers suggest 5x D iterations per G iterations

15. Avoid discrete spaces
    * Conneau, Lample et at., *Word Translation Without Parallel Data*

16. Discrete Variables (Conditinal GAN: Text-to-image, etc.)
    * Use an Embedding layer
    * Add as additional channels to images


