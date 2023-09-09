---
layout: post
title: "Serendipity"
date: 2023-09-05 15:00:00 -0700
categories: jekyll update
---

It just so happens that I've been asked to solve a problem inspired by 
[technical analysis](https://en.wikipedia.org/wiki/Technical_analysis) :
given a stream of 2D points ordered by a time coordinate in the "time"-"price" plane, find the two rightmost edges of the
convex hull of a window of points. We may assume that all points have a distinct time coordinate, so the problem is well defined.


There's an interesting application of the dynamic convex hull structure that I've been thinking about for the past two weeks.
It's possible there's a simple approach for the "time-monotone windowed-convex hull" problem.
Or maybe someone's reading my blog, who knows?

Either way, DPCH is seeming more and more worth it.

In other news, I'm interviewing with the [Voleon](https://voleon.com/index.html) group. Fingers crossed!
