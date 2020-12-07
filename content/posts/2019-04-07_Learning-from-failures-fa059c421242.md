---
title: Learning from failures
description: Using root cause analysis to learn from failure
date: '2019-04-07T08:45:31.292Z'
categories: []
keywords: []
slug: /@matanyam/learning-from-failures-fa059c421242
---

I am human, and as a result of being one, I do mistakes. I try really hard to avoid mistakes, but doing mistakes is mostly inevitable, so I compromise on trying to do each mistake only once. It is really hard not to repeat mistakes, but there is a mechanism that helps avoiding repeating mistakes.

One way of reducing the likelihood of mistakes is automating tasks, and another way is creating processes. I might cover them in future posts, but this time I want to cover what to do after the failure had accord.

![](/images/1__CjUSbw69tMokd5SjCp76KQ.jpeg)

Once a failure had happened, there is an opportunity to learn. In order to learn, two things should be in place before the learning can take place.

**Blameless environment**

[Jason Smale](https://medium.com/u/a48d2de6c65e) had written a great [post](https://medium.com/zendesk-engineering/blameless-culture-21662ab9118c) about it in the past, go and read it. In essence, it point to importance of having a culture that can look at failures without finger pointing, and looking at what decisions, systems and actions that were taken led to the issue at hand. The same approach can be applied to decisions and actions taken by a person not involving others. When one says “I failed cause I am stupid” it is not helpful, and does not lead to learning and growth. Looking at your chain of thought at the time of action or decision and identifying what went wrong, or at what checkpoint you could have reversed the wrong path would allow for improving for the next time a similar situation will rise.

**Honesty**

Once the setting allows for blameless environment people and more likely to be honest about what actions or decisions where taken by them. This is a crucial key point in the learning path. When people feel safe and are sure no one will judge them, the truth seems like the natural outcome. We should encourage and celebrate when our environment praises honesty.

#### The process

*   Identify and describe clearly the fault/problem.
*   Establish a timeline (history of events) from normal situation until the fault/problem.
*   Distinguish between the root cause and causal factors
*   Establish a [causal graph](https://en.wikipedia.org/wiki/Causal_graph "Causal graph") between the root cause and the fault/problem
*   Identify preventive and corrective actions
*   Implement the preventive and corrective actions

This process is widely used in domains such as IT operations, telecommunications, industrial process control, accident analysis, medicine, healthcare industry and so on. It can of course be used in other domains as well, as one sees fit.

Let’s look at a real-world case.

**Real world case**

On January 29, 2018 wikipedia was down for 8 minutes. [Here is the root cause analysis document](https://wikitech.wikimedia.org/wiki/Incident_documentation/20180129-MediaWiki).

In the case the fault is clearly described, and in non-technical words it means wikipedia was unavailable for 8 minutes. Then, a clear timeline is presented, with decisions and actions clearly outlined. In this case there were no real causal factors to confuse the investigation. The causal graph between the root cause and the fault is vivid, and the link between the actions and the site failure are direct. At last, there is a conclusion, and further actionable to implement, tracked in a ticketing system, to follow-up on execution. In this case, non of them are implemented at the time of this writing.

**Applying to decision making**

The case described above is a classic engineering root cause analysis. I use the same process for identifying root causes for wrong decisions I take, and for other mistakes done. This process helps a lot in learning from the fault and helps prevent the fault from reoccurring in the future.