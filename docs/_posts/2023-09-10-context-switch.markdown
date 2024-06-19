---
layout: post
title: "Context switch"
date: 2023-09-10 15:00:00 -0700
categories: jekyll update
---

I have some final thoughts on DPCH.
Since no one is asking me to work on it, and I don't see any further utility,
I'll be putting it on the back burner for a while.

But I do have some parting thoughts on how to go about implementing it.
My previous [post](/jekyll/update/2023/08/29/solving-a-problem-no-one-asked.html)
described the crux of the problem, and a reference that shows us how to find bridges
in $$ O(log(h)) $$ instead of $$ O(log(h)^2) $$ using a simultaneous binary search.
($$ h $$ being the size of the hull presently.)

To implement the divide and conquer dynamically, we need a tree that's
- approximately height balanced
- the leaves store data regarding individual points
- has internal nodes of degree strictly 1 or 2 

The leaf/internal node restriction is to simplify some cases of mergeing two hulls
while going up (or reversing the merge while going down) the tree.


I looked at several alternatives for such a structure, including B+-trees and Splay trees.
In the end, I again settled for treaps, with the added restriction on the priority of all
the internal "merge" nodes to be smaller than the any of the leaf "point" nodes.
This way I don't have to worry about rotations, and just have to worry about
how to split, merge, insert and delete from such treaps.

~~That's definitely a story for some other time.~~

Update September 14th : I've implemented a prototype of such an interval-treap.
