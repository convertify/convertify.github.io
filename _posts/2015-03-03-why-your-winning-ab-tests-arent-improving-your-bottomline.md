---
layout: post
author: Cooper Maruyama
title: "Why Your Winning A/B Tests Aren't Improving Your Bottom-line"
description: ""
featured_image: https://s3.amazonaws.com/convertify/blog/media/images/2015/03/angry-man-computer.jpg
fluid_image: true
title_image: true
use_math: true
category: "tips"
tags: ["tips", "testing platforms"]
---
{% include JB/setup %}

<p class="lead">Have you ever ran an A/B test that reported a significant lift in conversion, but when you implemented it, you saw no change in your sales? Well, this is a common occurrence, and I get asked about it often. Let me explain why this happens, and how to run tests in a manner that prevents this from happening.</p>


## Understanding how testing platforms report a "Winner"

Let's say that you ran an A/B test which had the following results when it declared a winner:

|  Variation  | Visitors | Conversions | Conversion Rate |     Lift    | Significance |
| ----------- | -------- | ----------- | --------------- | ----------- | ------------ |
|   Control   |    20000 |        2000 |             10% |          -- |           -- |
| Variation 1 |    20000 |        2120 |           10.6% |      +6.00% |        97.6% |

You're probably thinking that what these results are saying is that if you were to implement the winning variation, there's a 97.6% probability that you will see a 6% lift in conversions. If that's how you interpret these results, then you are **dead wrong.**

What this result _actually_ means is that there's a 97.6% probability that variation 1 will convert better than the control, but **it does not have any confidence in the lift itself.** So, how come testing tools don't adjust their algorithms so that the significance represents the confidence in the _improvement,_ rather than just the confidence in which one will win regardless of how much it will win by? Well, there are two very good reasons for this:

  1. It would take significantly more data to be able to reach 95% significance in the improvement. In fact, it would probably take more than _**ten times as much data, which means you'd need to run your tests more than ten times longer.**_  
  2. Once you know which one is the better variation, _**who cares how much it's going to win by?**_ It makes more sense to just implement it right away, and move on to another test. In other words, it's more practical to be able to run 10 experiments with confidence in which one will convert better (regardless of the lift), than to run a single test where you have absolute confidence in the lift.

If this is news to you, at least now you're aware of this, which is a step forward. Although we shouldn't assume that we're going to get as big a lift as is reported in the results, it also means that we might get a **bigger** lift than what is reported! Most of the time though, I've found that the former result tends to be the case. 


## How to create tests that actually improve your sales

The most common reason why winning tests don't turn into more sales is due to testing variables that result in a small standard deviation, therefore allowing the variance in your natural conversion rate to have a relatively large influence in the results. This is kind of a complex phenomenon to explain but I'll do my best to drill it into your mind. 

To understand this better, we first need to understand the concept of a **standard deviation.** The standard deviation is a measure that is used to quantify the amount of ariation in a set of data. Here's a good way to think about this: Let's assume we have a website that gets a 10% conversion rate. Now, imagine that the individual conversion rate for each day over a 10-day span looks something like this:

| Day | Conversion Rate |
| --- | --------------- |
|  1  |              8% |
|  2  |              5% |
|  3  |             13% |
|  4  |             12% |
|  5  |              5% |
|  6  |              7% |
|  7  |              9% |
|  8  |             15% |
|  9  |             20% |
| 10  |              6% |

For the sake of this example, assume that we got the same amount of visitors every day. As you can see, although the conversion rate is 10%, that doesn't mean that we are getting that conversion rate every day. Now there's no need to know how to calculate the standard variation, but we'll calculate it so that you understand the concept of it. In order to get the standard variation, we subtract the conversion rate for each day from the average conversion rate. However, this number can be negative, so we square each to get a positive value then get the average of _that_, which gives us the average variance. Then we un-square it (square root) so we don't have inflated values:

| Day | Conversion Rate |  Variance (x - mean)^2  |
| --- | --------------- | ----------------------- |
|  1  |              8% |    (8 - 10)^2 = **4**   |
|  2  |              5% |    (5 - 10)^2 = **25**  |
|  3  |             13% |    (13 - 10)^2 =  **9** |
|  4  |             12% |    (12 - 10)^2 =  **4** |
|  5  |              5% |    (5 - 10)^2 = **25**  |
|  6  |              7% |    (7 - 10)^2 =  **9**  |
|  7  |              9% |    (9 - 10)^2 =  **1**  |
|  8  |             15% |    (15 - 10)^2 = **25** |
|  9  |             20% |   (20 - 10)^2 = **100** |
| 10  |              6% |    (6 - 10)^2 = **16**  |

then we get the average of the differences and get its square root:

$$ \sqrt{\frac{4+25+9+4+25+9+1+25+100+16}{10}} = 4.669 $$

As you can see, our standard deviation is about 4.7 which is 47% of our conversion rate. Not only is this very large, but also much larger than the lift you will probably get in your A/B tests. It's unlikely that tools such as Optimizely would consider results like this "conclusive" unless you had lots of data in the test, but you get the gist of it now. Keep in mind that this is in either direction, so a high standard deviation means the test will not improve your sales. However, here's what you should take from this:

> **The larger your standard deviation, the more dramatic the difference between your control and variations need to be in order to create tests where the reported lift more closely matches the lift you'll see when you implement the variation.**

And with that said, the one thing you need to do is **test changes to variables that actually matter to your visitors.** If you aren't seeing lifts in sales from your winning tests, it's most likely because you are focusing too much on 'visual' aspects of your site, like colors, layout, and aesthetics, rather than the things they actually consciously consider, such as product features, reviews, and competitors. 

The first time I saw KISSMetric's inforgraphic on [how colors affect purchases](https://blog.kissmetrics.com/color-psychology/), I thought it was interesting but at the same time, I almost shed a tear because I knew just how many people scrambled after reading it and started running split-tests where they different colors on the elements on their website, inspired by that inforgraphic. When is the last time you changed your mind about buying something because of the color of something on the site? Probably never. When you test something like this, the resulting lift is most likely entirely due to variance, and you probably would've gotten the same result if you did an A/A test. 

If you want to learn more about creating tests that actually increase your sales, check out our free CRO course [No Guesswork](https://convertify.io/no-guesswork).