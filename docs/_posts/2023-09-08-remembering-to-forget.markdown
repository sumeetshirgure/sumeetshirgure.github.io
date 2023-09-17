---
layout: post
title: "Remembering to forget"
date: 2023-09-09 09:00:00 -0700
categories: jekyll update
---

_"Remind me to erase that from my memory" - Someone from Gravity Falls_

For a fresh diversion from the discrete world of point set convex hulls and range trees,
I've been asked to take a look at the recently released
[NeurIPS 2023 unlearning challenge](https://unlearning-challenge.github.io/),
and I had some initial thoughts about it.

Just from the challenge’s introductory passage it’s unclear as to what forgetting should even mean.
The authors of the starter kit say that a good definition of a model that has forgotten some set of
data, is one where an adversary shouldn’t be able to distinguish between a data point that’s supposed
to be forgotten vs. one that the model has never seen.

But the problem with such a definition is that the training data must have had some information
about the distribution of the unseen data as well. Saying that the model must be trained to forget
something should be like saying it must remember to treat something specially. Which admittedly
is something of a contradiction. Intuitively it only results in the burden of memory being passed on
to something other than the model.

Deep neural networks tend to have lower values of the cross-entropy loss, which they were trained to
minimize, for inputs from the training set - [Shokri et al. (2017)](https://arxiv.org/abs/1610.05820).


What I observed is that the average loss is also lower for samples from the ”retain” set compared
to that of the ”unseen” and ”forget” data subsets.
And this is true especially for the models trained solely on the ”retain” dataset that
is hailed as the ideal. What we will show is that the ideal model is also ”overfit” in some sense to
the ”retain” dataset. An adversary can simply train a logistic regression model on the output loss to
differentiate between a data point from the retain set vs. one not in it.

All of the above is true for the average entropy of the output as well (and not just cross entropy with
the target distribution). That’s precisely what I like to call the "entropy attack", does :
if the pure entropy of the output logits of the neural network is below a certain threshold,
it classifies the point as from the dataset.
I show in my experiment that such an attack achieves an accuracy of roughly
57% to 60% on the ideal network trained solely on ”retain” dataset.
The advantage of studying entropy attacks and not just cross entropy attacks is that the _latter depends
on the class labels_, whereas the former has no such restriction and purely depends on the input and
the deep neural network model weights.

The idea is to penalize the KL-divergence between the output distribution and the uniform distribution.

$$ D_{KL}(P||\mathcal{U}) = \sum_{i}{p_i(log p_i - log(1/N))} = -H(P) + log(N) $$

Note that this is the same as a regularizing term that penalizes
small output entropy. Using the KL-divergence as a regularization term is not a new concept, and is
widely studied in variational autoencoding - [Kingma & Welling (2022)](https://arxiv.org/abs/1312.6114).
In this context however, the regularization of entropy acts as a shield against the entropy attack.

The objective function is :

$$ L = \gamma \{\sum_{(r, l) \in R}{H(P(r), l)}\} - \alpha \{\sum_{(f, l)\in R \cup F}{H(P(f))}\} $$

where R and F are retain and forget sets respectively.
