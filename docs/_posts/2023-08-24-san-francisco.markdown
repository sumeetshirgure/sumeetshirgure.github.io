---
layout: post
title: "San Francisco 2023"
date: 2023-08-24 14:00:00 -0700
categories: jekyll update
---

After staying in the sunny, not-so-gloomy, Seattle for the entirety of August I'm going to San Francisco for a change.
I'll be interviewing with [chalk.ai](https://chalk.ai) at their offices!

In other news, lately I've been revisiting my
[implementation](https://github.com/sumeetshirgure/IncrementalConvexHull) of an
[online convex hull](https://en.wikipedia.org/wiki/Dynamic_convex_hull) structure for a stream of points on a 2D plane.
It's based on a clever application of supplying custom predicates to cut and join
[treaps](https://en.wikipedia.org/wiki/Treap) (randomized binary search trees).
[Here](https://cp-algorithms.com/data_structures/treap.html) is a good tutorial on treaps.

Computational geometry has always been close to my heart, and I've been thinking of implementing
the fully dynamic case as well that also supports point deletion.
There are several papers
[
    [1](https://link.springer.com/chapter/10.1007/3-540-44985-X_7)
    [2](https://dl.acm.org/doi/10.1145/363647.363652)
    [3](https://www.sciencedirect.com/science/article/pii/002200008190012X?via%3Dihub)
]
that give various approaches, and I haven't seen an open source implementation that supports tangent and
inclusion queries that is also easy to read.
I'm considering again using treaps for representing ordered sets, because of how convenient they are.

Very well might be that the next post will describe the same. Until then, goodbye!
