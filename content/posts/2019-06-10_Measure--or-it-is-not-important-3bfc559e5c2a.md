---
title: 'Measure, or it is not important'
description: Know your metrics to improve your business
date: '2019-06-10T08:00:36.372Z'
categories: []
keywords: []
slug: /@matanyam/measure-or-it-is-not-important-3bfc559e5c2a
---

This week I would like to highlight the importance of measuring metrics. The usual tracking of metrics relies on collecting them and preferably presenting them in a meaningful way. If you don’t collect your metrics periodically and consistently it will be extremely hard to get useful insights from them.

![](/images/0__AOLTNb8frs8__y1__j.jpg)

#### The golden four

When Operating a service, there are four metrics, called the golden four that should be measured and monitored that represent the health of the service.

The four are:

*   Latency
*   Traffic
*   Errors
*   Saturation

Those four metrics will almost always be the foundation for knowing how your service operates.

![](/images/1__c8wTpmXDOdEL__EKAQl6llg.png)

In the example image above, you can see a fake web service measured by the time it takes a request to be served — i.e. latency, the amount of incoming traffic and the error rate of requests. In addition, the cpu saturation is also measured. Any spike in any of those metrics would mean my attention is needed. Most likely there is an issue with the service itself if latency, errors or cpu saturation spike, and it wight be a good sign if traffic raises, but that would require attention as well, to see the infrastructure can hold with the traffic increase.

Of course those are the very basic measures, and you should measure deeper into your services.

![](/images/1__X81vbnzxpMsFkYlaR7Nmeg.png)

In the above example you can see a deeper look into the I/O rate of a disk array. It updates live and gives a sense of how hard the disk drives are working.

You should assess what should be measured in your service, define how to measure it, and build a mechanism to collect those metrics and present them in a the widest possible way. That is not only true for infrastructure services, Let’s look at a more interesting, and possible less commons measurement.

#### Business metrics and measurements

Since a business exists to make revenue, we need to measure the funnel from a lead to income and from there to profit. I do not know if most businesses measure key elements of the performance of the business but most do look at sells and funnels. Here is an example of business metrics of a service.

![](/images/1__jF7wVv__nJ9SBzgzhugfWvg.png)

In the example above, you can see the measures of the business side of the story. It doesn’t matter to anyone that your infrastructure metrics of the golden four are great and stable of the number of signups to your service are 0. Or if every signup ends up in a support call. Connecting the dots between infrastructure metrics and the business metrics gives you a better, more holistic view of how the service you are selling us actually performing, and will give you insights as to what in your product will require work, polishing and care.

#### The Customer view

Another angle that is important to measure is how your customer perceives the service. It might look to you the service is operating well, but your customer might feel otherwise.

![](/images/1__pAArOmMmohD0wwmhD83Jdw.png)

For example, it might be that your customer location is far from your serving site and that will lead to latency that the customer will experience, although in most cases you won’t notice it.

#### Summary

When you wanted to understand your business, you should collect metrics from three aspects, the customer view, your service infrastructure and the business goals metrics. Connecting the three sources will give you an holistic view of the performance of your services and product and will lead to better understanding of your business and where you should invest to be better.