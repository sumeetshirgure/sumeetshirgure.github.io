---
layout: post
title: "With peers like these..."
date: 2026-07-11
categories: jekyll update
---

Academia relies on peer review for evaluation of published work.
After having been part of the peer review process for a few months on both sides of it,
I'm compelled to comment on an issue with this process.
A major problem that seems to pervade this domain is the existence of bad reviewers.
And it's not just me saying this, the "unhelpful reviewer #2" trope has evolved to
the point of becoming a
[meme](https://amlbrown.com/2015/11/10/how-not-to-be-reviewer-2/).
Granted there exist a lot of poorly written papers and a lot of AI slop.
Still, it shouldn't excuse such behavior.

Case in point, consider this paper : [[BPs](https://www.nature.com/articles/s41467-018-07090-4)]
that I built upon in my recent manuscript. The publicly available peer review
[[file](https://static-content.springer.com/esm/art%3A10.1038%2Fs41467-018-07090-4/MediaObjects/41467_2018_7090_MOESM2_ESM.pdf)]
is an absolute treasure trove of a read. Prepare some popcorn for when you dive into it.

In summary : one of the reviewers (#1 and not #2 this time)
strongly objects to the paper, with some flawed reasoning, and says that they
(and others in the field) had known about the results prior.
Another remarkable coincidence I noticed is that such reviewers always make it a point
to show off their credentials and accolades in the word-limited review text box.
Reviews should be constructive, and if there are flaws those should be pointed out gracefully.
It shouldn't become a competition between the reviewer and the authors, in case it wasn't obvious.

Now I don't claim to be an expert in matters relating to academia,
few months is not nearly enough. But this does seem concerning.
If the fate of your paper is in the hands of such reviewers, that are drawn by the hands of lady luck,
maybe getting a rejection isn't the indictment that it comes off as.
I just hope my reviewers don't suck, and on the flip side, I will try to be as helpful
of a reviewer as possible in the future, like I've (hopefully) been in the past.

Furthermore, I came up with a (not so great) idea to fix such issues.
Throwing money at the problem might help -- reviewers are volunteers a lot of the times
and changing the incentive structure needs to be researched in case it already hasn't been.

My simple solution is applying AdaBoost :
boosting is a technique in machine learning which can be used to aggregate multiple
weak classifiers (reviewers) into a strong one by assigning weights to each classifier.
The way it works is by continuously updating the weights (multiplicatively if you're using
multiplicative weights/Hedge algorithms) of the reviewers based on their past "results".
The "results" take into account whether their review led to an acceptance/rejection
of a previous article. If their prediction agreed with the actual outcome,
increase their weight for future reviews. And if they behave like #2 (pardon the pun),
disregard their future opinions or simply don't invite them in the future.

I pitched this to Claude/Gemini and they rightly pointed out some problems with this setup :
if the game changes to predicting "_what will the other reviewers think?_" instead of actually
reviewing the article, that might lead to some unfavorable "Nash equilibria",
-- concepts I don't fully understand since I'm not an algorithmic game theorist.
Basically, the reviewers are incentivized to regress to the mean opinion instead of doing their
job. I don't know how much the reviewers will care for their arbitrary rating,
people on reddit seem to care about the made up points system.
But this does compound badly in case reviewers start getting paid at some point.
Then, maybe the feedback signal shouldn't be the averaged reviewer opinion,
but external factors like the number of citations, awards, or retractions.
All such signals are delayed by months if not years, so their practical applicability is uncertain.

Anyway that was all I had to share with you.
If you would like to connect and share your thoughts -- you can't since I haven't programmed a comments section.
Cheers!
