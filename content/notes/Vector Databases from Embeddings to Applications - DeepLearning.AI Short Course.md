---
title: Vector Databases from Embeddings to Applications - DeepLearning.AI Short Course
draft: false
tags:
  - reference
  - course
  - work_in_progress
related:
  - "[[Vector Databases]]"
timestamp: "202405221549"
---

# Vector Databases from Embeddings to Applications - DeepLearning.AI Short Course

## Introduction
- **Limitation of [[Large Language Models|LLMs]]**: knowledge reaches up to a certain point in time, and it does not include proprietary data.
	- **Solution**: use [[RAG]] (Retrieval Augmented Generation), which is bases on [[Vector Databases]].
- Vector databases were used before LLMs, for example in [[Semantic Search]] applications and [[Recommendation Systems]].

## How to obtain vector representations of data
- [[Embeddings]]: (compressed) vectorial representation of data.
- Embeddings can be obtained using [[Autoencoder]] models.
	- ![[autoencoder.png]]
	- The output is reconstructed by the Decoder starting only from a vector in the [[Latent Space]].

> [!info]+ Regularity of [[Variational Autoencoder]]'s latent space 
> Explained in [this Medium article](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73).
> The idea is that, without ***proper regularization***, some points in the latent space are "meaningless" once decoded, as the model severely overfits the training data.


## Search for similar vectors

## Approximate nearest neighbours

## Vector databases

## Sparse, dense and hybrid search

## Application - Multilingual search

## Conclusion

---
# References
- [DeepLearning.ai course page](https://learn.deeplearning.ai/courses/vector-databases-embeddings-applications/lesson/1/introduction)