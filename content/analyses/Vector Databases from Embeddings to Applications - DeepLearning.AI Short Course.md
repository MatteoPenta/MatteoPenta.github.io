---
title: Vector Databases from Embeddings to Applications - DeepLearning.AI Short Course
draft: false
tags:
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
### Example 1: Image embeddings using an Autoencoder model
- Embeddings can be obtained using [[Autoencoder]] models.
	- ![[autoencoder.png]]
	- The output is reconstructed by the Decoder starting only from a vector in the [[Latent Space]].

> [!info]+ Regularity of [[Variational Autoencoder]]'s latent space 
> Explained in [this Medium article](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73).
> The idea is that, without ***proper regularization***, some points in the latent space are "meaningless" once decoded, as the model severely overfits the training data.

- The following image shows the embeddings of the images in the MNIST test dataset represented in the 2D latent space of an Autoencoder trained on the MNIST training dataset:
![[mnist_embeddings.png|480]]

### Example 2: Text embeddings using a Transformer model
- Pre-trained [[Transformer]] models can be used to obtain the embeddings of sentences, which somehow capture their meaning. Thus, embeddings of semantically similar sentences will be closer than those of dissimilar sentences.

> [!question] In what way does the training process of a Transformer model enforce embeddings of semantically similar sentences to be close together?

### Measuring the distance between embeddings
1. **Euclidean distance (L2)**
	- Defined as the length of the shortest path between two points: $\sqrt{\sum_{i=1}^n A_i + B_i}$
	- It's sensitive to single-attribute outliers, i.e. to points having an extreme value in one of the dimensions. This is due do the square in the formula.
2. **Manhattan distance**
	- Defined as the distance between two points if one was constrained to move only along one axis at a time: $\sum_{i=1}^n |A_i + B_i|$
	- Less sensitive to single-attribute outliers than the Euclidean distance.
3. **Dot product**
	- Measures the magnitude of the projection of a vector onto the other: $A \cdot B$
	- Note: it's not a proper distance measure, as higher values of the dot product correspond to "more similar" vectors, i.e. two vectors that are closer to being parallel.
4. **Cosine distance**
	- Measures the difference in directionality between two vectors: $1 - \frac{A \cdot B}{||A|| \; ||B||} = 1 - \frac{||A|| \; ||B|| \; cos(\alpha)}{||A|| \; ||B||} = 1 - cos(\alpha)$
	  where $\alpha$ is the angle between the two vectors.
	- It's a proper distance metric, as lower values mean "closer" vectors.

## Search for similar vectors

## Approximate nearest neighbours

## Vector databases

## Sparse, dense and hybrid search

## Application - Multilingual search

## Conclusion

---
# References
- [DeepLearning.ai course page](https://learn.deeplearning.ai/courses/vector-databases-embeddings-applications/lesson/1/introduction)