# Summary

## [Miyato et al. 2018] Spectral Normalization
* Weight normalization technique
* Stabilize (only) D training

## [Zhang et al. 2018] Self-Attention GANs
* Attention-driven, long-range dependency modeling/image generation.
* Current problems (w/ GAN):
	* Good w/ gen. classes with few structural constraints (ocean, sky, landspaces)
	* Still have trouble with geometric or structural patterns (counting, symmetric, ...)
* Why?
	* CNN has local receptive fields.
	* Longer/Deeper models (CNN) may solve this problem, but are computational inefficiency.
* Solution (SAGAN)
	* Self-attention technique
		* Calculates response at a position in a sequence b attending to all positions within the same sequence.
		* Calculates response at a position as a weighted sum of the features at all positions (attention vectors)
	* Spectral Normalization (on both D & G)
		* Stabilize training process
		* Lest computational expensive
	* Two-timescale update rate (for D & G)
		* Regularization of D slows down GAN training
		* Faster training

## [Zhu et al. 2018] Cycle-Consistent Adversarial Networks
* Image to image translation
* Last year: *[Isola et al. 2017] Paired Image-to-image translation using Conditional GAN*
* Problems:
	* Usually works on set of aligned image pairs
	* What if paired training data is not available?
* Solution:
	* Adversarial loss: good translation
	* Cycle consistency loss (translate back to source domain to ensure it works both ways): good *reconstruction?*

## [Wang et al. 2017] A-Fast-RCNN: Hard Positive Generation via Adversary for Object Detection
* Object detection
* Problems:
	* Lack of images w/ deformation, occlusions
	* Current FastRCNN performs badly on those
* Solution:
	* Base detector(D): Fast-RCNN
	* Two types of G: ASDN (Adversarial Spatial Dropout Network), ASTN (Adversarial Spatial Transformer Network)
	* Use GAN to create and detect odd cases (w/ occlusions (masks), deformation (rotation,...)) of images.
	* Improving detection performance

## [Hoffman et al. 2017] CyCADA: Cycle-Consistent Adversarial Domain Adaptation
* Domain Adaptation
* Problems:
	* Adversarial domain models (applied in feature spaces):
		* can find domain invariant representations
		* can NOT (sometimes) captures pixel-level, low-level domain shifts.
* Solution:
	* Adapt in both feature-level and pixel-level
	* Enforce adversarial objectives, cycle-consistency, and **semantic** consistency
	* Leveraging task loss