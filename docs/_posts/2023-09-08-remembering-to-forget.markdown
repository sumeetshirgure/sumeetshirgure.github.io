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

**It's unclear as to what forgetting should even mean.**
The authors of the starter kit say that a good definition of a model that has
forgotten some set of data, is one where an adversary shouldn't be able to distinguish
between a data point that's supposed to be forgotten vs. one that the model has never seen.

But the problem with such a definition is that the training data must have had some
information about the distribution of the unseen data as well.
Saying that the model must be trained to forget something is like saying it should
remember to treat something specially, which is something of a contradiction.
You're just passing off the burden of memory on to someone other than the model.

One definition that I like is where the deep learning model _intentionally sucks_ at classifying
an image that's supposed to be forgotten. In other words, the output entropy of the predicted
distribution is high compared to the average entropy of the distribution for a randomly
selected data point.

To that effect, one can define a regularizer which penalizes the KL-divergence of the output
distribution with respect to the uniform distribution.
Minimizing which just comes out to be the same as maximizing the output's entropy.

Assuming that in the real world, there is no "unseen data", and everything is part of either
the "retain" set or the "forget" set, one can simply construct a classifier (just like the one in the starter kit)
to infer if the data point is part of the retain set just by looking at the average output entropy.
I call this technique the "entropy attack" (the starter kit classifier can be thought of as a specialization of
the entropy attack in that it only looks at the negative log likelihood of the correct class; i.e cross-entropy)

I found that such regularization does indeed protect against the entropy attack between "retain" and "forget" sets.
Also also, simply adding regularization and not fine-tuning boosts accuracy on the "forget" set, which is uncanny.

Here is a Github Gist with all of the work.

<script src="https://gist.github.com/sumeetshirgure/6543c8752a103f02c3b8b19e251e4436.js"></script>
