---
title: Supporting a customer the right way
description: Turning a lemon into lemonade in customer support
date: '2019-03-17T07:56:47.293Z'
categories: ["Customer support"]
tags: ["AWS", "Spotinst", "Customer Support", "Spot"]
authors: ["Matanya Moses"]
slug: /2019-03-17/supporting-a-customer-the-right-way
---

AWS has [four types of ec2 computing resources](https://aws.amazon.com/ec2/pricing/). On demand, reserved, dedicated and spot. On demand, as it name indicates is a pay as you go program. The instance has a price, and you pay it as long as your instance is running. Reserved, is a plan where you commit to using a resource for one or three years, and pay up front if you wish, to get discounts of 30%–60% of the on demand list price. Dedicated are physical instances that are 100% yours, as the name indicates. The spot type is based on AWS extra capacity, and works on requesting spot capacity. You can read more about how it works [here](https://aws.amazon.com/blogs/compute/new-amazon-ec2-spot-pricing/), this can lead to up to 80% saving in cost.

{{< figure src="servers.jpg" caption="Wikimedia foundation servers by Victorgrigas [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0)" >}}

We use three ec2 types, for various workloads, we do not use dedicated. Some workloads are predictable, and can’t be interrupted, and for that we would use reserved instances. Some workloads are unpredictable, short lived and can’t be interrupted, so we use on demand for that. We use spot for any other workload. We use a company called [spotinst](https://spotinst.com/) to handle our spot fleet. The idea behind spotinst is to handle all the bidding, and instance replacement due to interruptions as transparently as possible. The instances are placed in an elastic group, and are handled in autoscaling policies.

In the case there is no spot available, we revert back to on demand, to make sure we always have compute resources to handle our workloads. One day in one of our components, we suddenly lost all compute resources for a short period of time. It was unclear to us at first what happened, but we quickly realized all our spot instances where gone away at once, and replaced by on demand. The way we implemented our replacement strategy is gradually replacing the instances to make sure we have a transparent transition. In addition to that, we have a variety of instance types, to make sure that if one spot market for an instance type has scarce resources, we can move to another instance type market to meet our needs.

All of this did not help. The instances were gone at once. We quickly figured spotinst has a parameter called ‘risk’ which indicates how far you are willing to go with spot in your elastic group setting. In all our elastic groups until that point we had 100% spot, with no issue at all. In that specific case, we reduced the rate to 60%, to make sure we will always have on demand instances to cover our needs for that workload.

We opened a case to spotinst, to uncover the mystery. They looked into it, and found a few interesting findings. For historical reasons, that workload still resides in EC2-classic, while the rest of our services reside in VPC. Nowadays AWS gives little love to EC2-classic. This led to a tiny spot market in that specific case, and as it seems, it was just gone all at once at some point. Until we spawned the new on demand instances, we had a short period with no instances. On a call with spotinst, they recommended to reduce the risk to 60%, which we already did on our own. In addition, they said they identified a place for improvement in their code, to handle such cases better. They also asked if we can move to VPC, to which we answered, yes, but not now. Another wise step by spotinst was to include a product manager on the call, to see if we have any product requirements or wishes.

I was fairly unrest before the call with them, and was on the verge of asking my direct reports to pull out spotinst from our infrastructure until we cleared out some uncertainty. Spotinst team has done a great job in calming the situation down and clarifying where we stand.

**Takeaways for doing support right**

*   Listen to what your customer is complaining about
*   Clearly explain the situation
*   Suggest a workaround
*   Check with the customer if a permanent solution is feasible
*   Admit your shortcomings
*   Include a product manager or other similar function that can collect feature requests from the failure

Thank you spotinst team for your professional support and help during an incident.

---
