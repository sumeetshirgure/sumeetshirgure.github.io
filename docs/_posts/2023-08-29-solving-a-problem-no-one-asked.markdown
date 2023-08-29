---
layout: post
title:  "Solving a problem no one asked"
date:   2023-08-29 15:00:00 -0700
categories: jekyll update
---

San Francisco was fun! Sunny slopes and windy lunches could only have been better had I not completely bombed my interviews.
But I got to meet my friends after a long time (and in one case for the first time in person) and that made the trip worth it.

I've been thinking about how to implement dynamic planar convex hull, and the approach by Overmars and van Leeuwen is the most amenable to
read and code directly. I also found a [blog post](https://codeforces.com/blog/entry/75929) on Codeforces that discusses the crux of the paper.

The idea is to store all points currently in the dynamic set in a balanced tree (which they call the "segment tree" on the blog post)
such that the leaves are the points and the internal nodes are unions of their two children. Inside each internal node contains the data about
a single edge of the convex hull. This edge is special in that it's the bridge between the convex hulls of the two subsets that are the two
children of said internal node.

We can keep the convex hull of the corresponding set in a bunch of treaps (or any other tree that allows split and concatenate)
within the internal node and find the bridge in logarithmic time using the procedure described in the blog post.
Since we're allowed $$ O(log(n))^2 $$ per update, we might be able to keep $$ O(log(n)) $$ many containers chained in a single node.
This will bump memory usage to $$ O(n log(n)) $$ but the ease of implementation could be worth it.

To maintain the set itself, it might be useful to explore other strategies like [weight balancing](https://en.wikipedia.org/wiki/Weight-balanced_tree)
so that the subsets are approximately equally divided every time we go down the tree. This not only ensures $$ O(log(n)) $$ tree depth
but also modest sized chains of convex hulls of these sets.
I'll still need to look at how convex hull structures inside the tree nodes are to be updated under rotations.

Maybe that's a story for next time.
