---
layout: post
title: "A dynamic week"
date: 2023-10-04
categories: jekyll update
---

I've been settling into my new abode near USC, and getting started with
my duties as a research assistant at the [deep learning group](https://deep.usc.edu/) here.

This post's title sounds like something out of a Petr Mitrichev blogpost, but I digress.

In this week's news, I've been looking at ideas similar to the dynamic split-and-merge tree.
There is a whole class of [problems](https://www.sciencedirect.com/science/article/pii/0196677480900152)
dug up by Bentley and Saxe -- those that allow dynamic solutions to what are called decomposable search problems.

An example of which would be the closest pair problem: given a set of points in the plane, find the pair closest to each other.
This can be generalized to the [all closest neighbours](https://github.com/sumeetshirgure/Codex/blob/master/Geometry/AllNearestNeighbours.hh)
problem where the objective is to find for every point a neighbour closest to it. The linked code runs in $$ O(n log(n)) $$ for $$n$$ vertices.
The standard split-and-merge approaches rely on the fact that while merging two solutions we don't need more than a constant number
of checks across the split for any point.
Dynamizing this would mean that we can maintain a list of closest neighbours for every point in polylogarithmic time under point
additions and deletions, which is kinda awesome.

And now for the cherry on top, I'm thinking of possibly applying similar ideas to problems arising in topological quantum error correction
[[link]](https://github.com/yuewuo/fusion-blossom) in a kind of "sliding-window" setting, where a stream of stabilizer measurements
is continually being fed to a decoder that is tasked with maintaining the logical state.
It is natural to consider retiring older defects whose impact decreases over time.
So a fully dynamic variant of the matching problem on a fixed lattice topology could be something worth looking into.


In an unrelated update, I just sat in on a class featuring dynamical decoupling for quantum error correction, and it was an inspiration.
Somehow the discussion ended up on the representation theory of finite groups, and this idea of group averaging.
Never had I seen such a direct connection between abstract algebraic theory with direct experimental results being obtained from it.
This idea of averaging over a group is quite a powerful one, and is one I believe also employed in Weyl's unitarization trick.
Closely related are the notions of convolution over a group, which are used to define abstract Fourier transforms [link](/assets/pdfs/projects/cs_599_project.pdf).
