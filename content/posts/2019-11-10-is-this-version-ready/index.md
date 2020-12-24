---
date: "2019-11-10"
title: "Is this version ready?"
description: To answer the question if the version is ready, you need to tell mm how much you ar willing to pay
slug: /2019-11-10/is-this-version-ready
authors: ["Matanya Moses"]
tags: ["Software Development", "Software Testing"]
categories: ["Software Development"]
---

Have you ever been asked this question? I guess some of you have. I wonder what is the common answer people typically answer this question regarding a build, a release or a version. I have a standard, boilerplate response:

> Depends how much you want to pay

You see, one can test a piece of code basically forever, but then it won't ship,
and still might contain bugs. Testing is super important, but similar to many
things in economics the rule of [diminishing
returns](https://en.wikipedia.org/wiki/Diminishing_returns) applies here as well.

At some point it is no longer worth finding that little UI bug that annoys one
user, you have invested many dollars to find that bug, but it won't matter
enough to be worth the money spent, that you could've spent on something else.

{{< figure src="bug.jpg" caption="A real bug found in [Harvard Mark II](https://en.wikipedia.org/wiki/Harvard_Mark_II), giving the name bug to a software defect. Courtesy of the Naval Surface Warfare Center, Dahlgren, VA., 1988. [Public domain]" >}}

There are a few tested and proven ways to increase trust in a code base. such as:
- Shipping small chunks of code
- Having extensive test suite
- Test coverage

But all those methods only increase the likelihood of finding a bug, they do not guarantee a bug-free code base.

## WHY?

You probably ask yourself why software engineering is not like other engineering. Basically, you probably think, the ingredients are smart people writing some code with the aid of some coffee, how different is that from assembling a car in a factory?
The truth is writing code is not like assembling a car. On your production line of cars, all parts should be identical, and you take a sample and assume it represents the entire batch of that part. In code, you can't do that. Testing one code line does not represent the others, and certainly does not represent any inter-logic flaws between other code lines. And Dave Mangot wrote it much better than I would.
However, as you spend more time which equals more money on testing your code, you will likely find more issues. The secret is to find the balance as to where your investment is worth the additional findings, the delay to release and hit the market and the cost of actually running the test suite.
I am not calling for cutting on QA, nor am I calling for investing in your testing until you feel any additional bug found will not be worth the money spent. I am suggesting to build your own spectrum, which shows where your sweet spot of investment VS quality improvements lie.

## Industry specifics

Of course the spectrum differs greatly from industry to industry and from
compliance and risk view points of the consciousnesses of bugs. A bug in a
[critical system can actually kill people](https://en.wikipedia.org/wiki/Therac-25), or [cause losses of millions of dollars](https://en.wikipedia.org/wiki/Cluster_(spacecraft)#Launch_failure).

But most software releases are not in such sensitive and risky intolerant
industries. Most websites do not incur life risks or loosing severe amounts of
money if they contain bugs. This includes security related bugs, which are after
all, also [bugs](http://lkml.iu.edu/hypermail/linux/kernel/1711.2/01701.html).

{{< youtube PK_yguLapgA >}}

## Invest in the right place
The first thing to do if you want to invest your money in the right place is to identify what are the causes for most of your bugs. Some examples to illustrate:
Are they integration issues
- Are they complicated configurations conflicting
- Are they logical issues
- Some crazy one-off not well covered
- Release process issues
- Performance issues

And so on and so forth. Once you have identified the main source of pain, you can actually go and fix that pain point, and you will likely find it is not going to be that costly.
Having your lessons learnt from new code shipments is the basis for getting better at sipping better code, so don't avoid that learning opportunity.

---
