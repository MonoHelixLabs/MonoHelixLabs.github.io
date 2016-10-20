---
layout: post
title:  "Inside a kitchen weight scale"
date:   2016-10-17 19:25:00 +0100
categories: kitchen scale weight
author: paula
permalink: /inside-kitchen-weight-scale.html
---

Ever wondered what is inside a kitchen scale? Does it use any of the sensors that you can buy from your favorite electronics store?

As part of our research on how we could build a Wi-Fi connected scale we looked over what sensors could be used to measure weight. One solution would be to use Force Sensitive Resistors (FSR), and while they are very easy to get started with, they are not precise. They can tell you whether there is some pressure on them or not, but it is very difficult to get precise measures that you can translate in units such as lb or kg (more about this in a future blog post).

When looking at alternatives for measuring weight, we looked over load cells. There are several types, and SparkFun Electronics has a <a href="https://learn.sparkfun.com/tutorials/getting-started-with-load-cells" target="_blank">nice tutorial</a> about the different types of load cells.

Still, it was not clear whether we need four load cells to be able to measure weight or if there is any way one can use only one load cell, especially if our target weight range is under 5 kg. At this point, we stepped into our kitchen to investigate!

![kitchen_scale_00](/images/kitchen_scale_00.jpg)
This is a standard kitchen scale (bought from local store for around 22$) and handles up to 5 kg.

![kitchen_scale_01](/images/kitchen_scale_01.jpg)
And indeed, this scale uses 4 load cells. One can buy such load cells for somewhere around 5$ per piece (more or less, depending on sensor range and store). And we can only assume that the producer of this scale must have gotten a better deal.

But does this mean that all scales use 4 load cells? We ordered a smaller scale from AliExpress to investigate.

![kitchen_scale_02](/images/kitchen_scale_02.jpg)
This is a scale that handles up to 1 kg (bought for around 4$ from AliExpress including shipping).

![kitchen_scale_03](/images/kitchen_scale_03.jpg)
And inside, one load cell bar only! Mystery solved.