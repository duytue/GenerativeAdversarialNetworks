# Domain Adaptation Using Adversarial Learning
[Source video](https://www.youtube.com/watch?v=uUUvieVxCMs&index=8&list=PLazcgz-LJ6ZIrJV-qiqw16JyJFuE4TNKF)   
Speaker: Victor Lempitsky, Skoltech, Moscow, Russia

* What we have:
    * Lots of labeled data in the source domain (synthesis images)
    * Lots of unlabeled data in the target domain (real images)
* What we want:
    * train on deep net on source domain that does well on target domain

### Problem   
* Feature distributions (of target) do not match them of source dist (blue is source, red is target)   
![problem1](img/domain_1.png)
    
### Goal
* Align two distributions so that they are similar.   
    ![goal](img/domain_2.png)

## Aligning domain distributions in feature space
* **Overall approach**: add a loss to measure dist. mismatch into learning process
    * Measuring second-order moments mismatch (Sun and Saenko 2016)
    * Maximum mean discrepancy (MMD) (Long and Wang ICML 2015)
    * Through Adversarial Learning: ...

## Alignment through Adversarial learning:
### Adding domain classifier (Discriminator)
* From a point, try to predict which domain it comes from.
* If 2 domain dist. are:
    * distinguishable: domain loss will be **low**
    * mixed: domain loss will be **high**   
    ![domain_loss](img/domain_loss.png)

![domain_model](img/domain_model.png)
* Network:
    * Build the network
    * Train *feature extractor + class predictor* on source data
    * Train *feature extractor + domain predictor* on source + target data
    * Use *feature extractor + class predictor* on target data to test

    ![backprop](img/backprop_update.png)

    * **Objective**: small label prediction loss + large domain classification loss   
    ![saddle_point](img/saddle_point.png)

* One possible improvement: sharing the features extractor between domains
    * [Rozantsev, Salzmann, Fua 2016], *Beyond Sharing Weights for Deep Domain Adaptation*
        * Idea: share only some layers, result may get better

    * [Bousmalis, Trigeorgis, et al. NIPS 2016], *Domain-separation networks*
        * There is a shared encoder, and the classifier uses shared component only.
        ![shared_encoder](img/shared_encoder.png)

    * [Tseng, Hoffman, Saenko, Darrell CVPR17], *Adversarial Discriminative Domain Adaptation*
        * Pretrained a source classifier
        * Adaptation with conditional GAN
        ![ADDD](img/ADDD.png)
        
