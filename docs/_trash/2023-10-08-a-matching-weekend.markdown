---
layout: post
title: "43 years in the making"
date: 2023-10-08
categories: jekyll update
---

Earlier this week I listened to Vijay Vazirani's
[talk](https://simons.berkeley.edu/events/theory-alternating-paths-blossoms-perspective-minimum-length)
on the Micali-Vazirani algorithm for general graph matching.
And it was something out of this world.
From my ICPC days, I was quite familiar with the idea of successively using shortest augmenting paths for
constructing minimum cost flows, but in my wildest dreams couldn't I have imagined the underlying
theory to be so sophisticated. And yet, the algorithm turns out to be so simple and elegant.
The intricacies required the author 43 years to be investigated in full detail; what a legend.

A central concept in the MV algorithm is that of _phases_, where in each phase a maximal set of
augmenting path is selected and added modulo 2.
This lead me to ponder over applying the all nearest neighbours algorithm as a
subroutine in constructing greedy matchings for surface code error correction
Empirically analyzing its average case complexity under a circuit-level noise model might lead to something.

As for Yue Wu's [fusion blossom](https://github.com/yuewuo/fusion-blossom), the existence of the "fusion" step
is essentially saying that the point-set matching problem in the plane is decomposable in the sense of Bentley
(see the previous blog post).
The "proof" of the linear complexity of the merge step is somewhat handwavy
in that it's left to empirical evidence. (\*cough\* why hello kettle, this is pot \*cough\*).
But I believe that's correct since we should expect the complexity of the partition-crossing edges in
_every_ triangulation of the points to be linear.
Moreover the linear complexity of the entire algorithm is somewhat dubious, I don't believe it's better
than $$ O(nh) $$ for $$ n $$ point being fused with a tree of height $$ h $$. Could be wrong though.
They will probably end up merging the code with Google's [pymatching](https://github.com/oscarhiggott/PyMatching).

As for fully dynamizing it, I feel like there's probably a linear lower bound on the fusion step,
meaning even if we dynamically maintained the fusion tree in memory,
maintaining the matching will be super-polylog because of the costly merge step. Again, could be wrong.

These exact matching algorithms however are quite costly in terms of hardware.
Sure parallelizing using fusion trees could cut latency, but I'm afraid that might still turn out to be not enough.
The latest cryogenic hardware specific algorithms are quite promising in that light
[[NISQ+](https://arxiv.org/abs/2004.04794)] [[QECOOL](https://arxiv.org/abs/2103.14209)].
But we likely won't have the hardware needed for the forseeable future.

If I can get the greedy decoding scheme, (which is just the no-brainer half-factor approximation of matching)
to work on GPUs faster than the exact matching algorithms, with acceptable threshold / mean time to first failure,
that would be awesome. And probably more practical while scaling up qubits.

