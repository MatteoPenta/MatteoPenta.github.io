---
tags:
  - note
related: 
timestamp: "202405221719"
---

# Variational Autoencoder

## Introduction

> [!quote] Comparative definition, from [^vae_article_medium]
> *A variational autoencoder can be defined as being an **autoencoder whose training is regularised** to avoid overfitting and ensure that the latent space has good properties that enable generative process.*

![[vae_scheme.webp]]

## Loss function
> Thus, the loss function that is minimised when training a VAE is composed of a “reconstruction term” (on the final layer), that tends to make the encoding-decoding scheme as performant as possible, and a “regularisation term” (on the latent layer), that tends to regularise the organisation of the latent space by making the distributions returned by the encoder close to a standard normal distribution. That regularisation term is expressed as the [Kulback-Leibler divergence](https://en.wikipedia.org/wiki/Kullback–Leibler_divergence) between the returned distribution and a standard Gaussian. [^vae_article_medium]

![[vae_loss.webp]]

## Regularization
- Regularization in VAEs encourages the latent space to be more **disentangled**, which means that the latent factors are more independent and capture distinct aspects of the data. This disentanglement is beneficial for generative tasks as it allows the model to learn more meaningful and interpretable representations

--- 
# References
[^vae_article_medium]: https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73