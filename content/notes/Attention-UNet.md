---
title: Attention-UNet
draft: false
tags:
  - review
related:
---

# Attention-UNet
- General idea: focus *more* on the "important" parts of an image, focus *less* on what is not important.
- Technical idea: highlight only the relevant *activations* during training.
	- Reduced computational resources wasted on irrelevant sections of the images.
	- Better generalization of the network.
- **Hard attention** vs **Soft attention**
	- Hard Attention:
		- Highight relevant sections by *cropping*.
		- Consider one patch of an image at a time.
			- Non differentiable.
			- Needs reinforcement learning.
		- The network takes a decision (focus/not focus) for whole patches.
	- Soft Attention:
		- Weighting different parts of the image.
		- Relevant parts of the image get *large weights*, less relevant parts get *small weights*.
		- Differentiable.
		- During training, also the weights that are assigned are trained, making the model pay more attention to relevant regions as it evolves.
- Skip connections in the UNet architecture
	- Needed to combine the spatial information from the down-sampling path with the up-sampling path to retain *good spatial information*.
	- However, this process brings along the poor *feature representation* from the initial layers.
		- Remember that better, more relevant *features* get extracted as the image is down-sampled in the encoding path. Hoverer, this feature extraction process comes at the cost of losing the spatial information from the original image.
	- Soft attention implemented at the skip connections will *actively suppress activations at irrelevant regions* coming from the concatented output of the downsampling step.
- Implementation of the Attention gate in the UNet architecture
	- At each skip connection, the attention gate takes two inputs:
		- Gating signal $g$: the output of the last convolution in the encoding layer (layer $l-1$) *before* it is upsampled.
		- Input $x_l$ coming from the corresponding layer in the downsampling path (layer $l$).
	> [!hinit] Note that this means that the gating signal contains more *feature rich* information coming from the deeper layer that is used to "decide" which parts of $x_l$ need to "receive attention".
---
# References
- [(YouTube) Attention U-net. What is attention and why is it needed for U-Net?](https://www.youtube.com/watch?v=KOF38xAvo8I)
- [(Paper) Attention U-Net: Learning Where to Look for the Pancreas](https://arxiv.org/abs/1804.03999)