---
layout: post
title: "Obfuscation"
date: 2023-09-17 13:00:00 -0700
categories: jekyll update
---

I've been somewhat invested in the [NeurIPS machine unlearning challenge](https://unlearning-challenge.github.io/).
In a previous post, I ideated a simple regularization strategy for classifier networks to evade entropy based attacks.
Turns out the attack and the regularization was well known. (And documented in the reference I gave myself no less.)

However the problem with training solely on the retain dataset still remains.
I have an alternative that I think is better. It's based on the ideas I mentioned in my previous post.
I've run some experiments and come up with an algorithmic framework that works really well in practice.
I call it obfuscation, for lack of a better word.

I've also written a paper that I submitted to NeurIPS workshops, titled
"A potential flaw in the NeurIPS unlearning challenge". Cheeky, I know.
I would have loved to link it on my blog as well, but the workshops require anonymity.
Even mentioning it on my blog is a little problematic; but since search engines can't find
Shtetl Disorganized I should be okay.
Even if it gets rejected I'll definitely link it on here someday. Pinky promise.

In other news, I made a new friend this week.
And even though I said I'll put DPCH on the back burner, that's all I do in my free time.
The result being that the code is coming along nicely.
I'll try to publish something in a journal as well.
I'll even open source the divide and conquer interval treap because it seems slightly non-trivial
and also quite useful.
