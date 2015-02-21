---
author: convertify
comments: true
date: 2013-02-11 03:37:07+00:00
excerpt: 'Recently I read <a href="http://theleanstartup.com/"><em>The Lean Startup</em></a>
  by Eric Ries – A popular book that many of you have probably read. At the core of
  his concept is the Build-Measure-Learn loop, which is exactly what Conversion Rate
  Optimization is about. For those who haven’t read it, the quick outline is this:

  '
layout: post
slug: lean-conversion-optimization-strategies-for-fast-implementation-and-results
title: 'Lean Conversion Optimization: Strategies for Fast Implementation and Results'
wordpress_id: 977
categories:
- Conversion Rate Optimization
- Guides
---

Recently I read [_The Lean Startup_](http://theleanstartup.com/) by Eric Ries – A popular book that many of you have probably read. At the core of his concept is the Build-Measure-Learn loop, which is exactly what Conversion Rate Optimization is about. For those who haven’t read it, the quick outline is this:





	
  * Business performance should be measured by how much is learned in a certain span of time.

	
  * To accomplish this, you must build a minimum viable product, test it, measure results, and then learn from it.

	
  * The faster you iterate this process, the faster your business will grow.


The book reminded me exactly why conversion optimization is so effective - We build an experiment to test a hypothesis, measure results by creating a split-test, and then drive a conclusion based on the results.

Something he pointed out that interested me the most, however, is that when 2 companies compete, the company who iterates through this process the quickest is the one who usually wins. In CRO, this also applies. Each test teaches us something about our visitors – and the more we know about our visitors, the better we can sell to them. Every time you learn something about your visitors, you can make a “change” to your site that increases conversions. For example, imagine you had a $50 product but you had low conversions because your visitors were only willing to pay $40.  As long as you don’t learn that information, you'll be losing out on the additional revenue you could've gained by lowering your price. This is what I like to call a “blind spot”, and every business has tons of them.  Uncovering them is how you’ll learn to grow, and split-testing is simply a vehicle that allows us to uncover them. It mitigates the consequences of our assumptions.

This article will detail unique optimization strategies that you will find extremely useful. Some topics will be somewhat technical, requiring the understanding of some programming. Either way, you should read it – understanding why you should apply these strategies is what will ultimately help you improve your conversion rates.


## **Return on Effort**


The effectiveness of an experiment should not be measured solely by the percentage of increase it brings in conversions. Every case study brags about how they hit xxx% increase in conversion, but I believe the most important factor is **return on effort.** You should measure the effectiveness of your test by taking into account the effort and time it took to implement that test. Imagine how much more time and money it would take to test a new video compared to testing a new headline. Headline tests take me about 10 minutes to implement, whereas testing a new video would require a lot more money and resources.  With this in mind, we can begin to lay out a better way to run tests.


## **Choosing What to Test**


If you asked a few experienced optimizers what element they would test first on a specific landing page, I believe you would receive varied responses. One may think the navigation should be tested first, while another would go for a headline test first. Without an effective strategy, most optimizers tend to decide what to test first based on one of two things:



	
  1. What they have seen work before – This is because we want winning tests, and duplicating past wins intuitively seems to have the highest chance of success.

	
  2. What element they believe is most lacking – Optimizers intuitively want to work on whatever has the most room for improvement.


There’s nothing wrong with this – it’s a good place to start. But we shouldn’t run experiments based on this alone. You need to weigh your ideas against the time it will take to implement the test, as well as the resources (and money) required to do so.

To figure out what to test, follow these steps:

	
  1. Make a list of all your hypotheses about how you can increase conversions.

	
  2. Convert these hypotheses into possible experiments.

	
  3. Identify the following attributes of each test:

	
    1. Expected change in conversion rate

	
    2. Time required to implement the test

	
    3.  Money required to implement the test

	
    4. The duration that the test will need to run for to be conclusive. VWO’s [test duration calculator](http://visualwebsiteoptimizer.com/ab-split-test-duration/) will help you with this.




	
  4. Taking these attributes into account, prioritize each test by weighing the expected change in conversion rate against the time, money, and test duration required


This methodology of testing allows you to be more efficient, and is especially necessary for smaller sites that are not getting a lot of conversions to run tests with. This can make the difference between a test that runs 2 months versus a test that runs 2 weeks! Once you figure out what to test, we need to implement it.** **


## **Implementation**


** **I’m not going to get into setting up basic tests – you probably already know how to do that. I’m going to show you some advanced techniques for setting up tests that will allow you to run **multiple site-wide tests at the same time. **I like to call this “layering”. There are 2 huge benefits to running layered tests:



	
  1. By using all of your visitors, you can run tests quicker.

	
  2. By running multiple tests at once, you can run more tests in less time.




### **jQuery**


What makes layering possible is client-side scripting – namely Javascript. With Javascript, we can dynamically adjust a website on-the-fly. jQuery is a Javascript library that allows you to accomplish this with relative ease, much more quickly than if you were to use plain Javascript. With jQuery, you can modify elements dynamically using a selector. I’ll outline a few strategies and show you how to implement each one. Even though you don’t intend to learn the coding, but rather intend to hand the task off to a developer, you should still take the effort to understand how it works.


### **Regular Expressions**


Regular expressions allow you to match strings that meet certain conditions. For example, if you want to run some code on product pages but not category pages, you would use a regular expression.


### **Layering Site-Wide Tests**


In order to learn more efficiently, you have to minimize the time between deciding to implement a test and launching that test. Most of that time in-between goes into development. Site-wide tests often require creating a duplicate of the entire site either in a sub-directory or a sub-domain.  Take a look at the image below of what your test setup might look like in a standard site-wide test using VWO.

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/Screen-Shot-2013-02-10-at-4.47.05-PM-300x1041.png)[/imageframe]



The problem with this is that not only does it require you to create an entire duplicate of your site in a sub-directory then make the changes, but it also allows you only 1 site-wide test at a time.

Of course, you can test just certain sub-directories, such as creating a split-test for domain.com/products/* and another for domain.com/category/*, but you still have to create copies of all the pages residing in that subdirectory. _Think about it_ – _you’re duplicating 100% of the content, even if you are only changing/testing 1% of that content!_ Something about that just doesn’t seem right. And what about when your visitors link back to that URL? If it’s in a sub-directory, that link will send the visitor to a “page not found” after you stop the test. _There’s a better way, and I’m about to show you._

A simple A/B test works by redirecting 50% of the traffic to the variation page. But something else happens in order to ensure that the person sees that page if they leave and come back – a cookie is saved to their computer that identifies which version of the page they should see. Modern software gives you 2 ways to create a split-test: A/B tests, and split-URL tests. An A/B test will show the same URL no matter which variation you are assigned, but a split-URL test will redirect you. The A/B test has the advantage on that front because it prevents people linking to broken pages in the future, but it has a huge disadvantage as well – you can’t test multiple pages.

In software such as Optimizely or VWO, A/B tests are set up using a visual WYSIWYG editor that makes it really easy to create tests, but you can’t make changes to multiple pages at once with a WYSIWYG editor.  For example, you can’t tell a WYSIWYG editor that lets you edit just one page to increase all your prices by 10%. However, these software include a nifty feature that allow you to get the best of both worlds – a Javascript API.

This API allows us to run Javascript code based on the value of the cookie – in essence, the variation they should see. In VWO, it’s a feature of the A/B editor and it allows us to layer site-wide tests on top of each other.

Here’s how you layer site-wide tests:



	
  1. Visit a relevant page on your site.

	
  2. Pull up the developer console, and write/test the code that makes the change you want site-wide.

	
  3. Set up an A/B test, and add just that code to your variation.

	
  4. Change your A/B test’s URL pattern settings so that it runs on the relevant pages, and excludes irrelevant ones.  If your software doesn’t meet your needs of proper URL matching, you can also use regular expressions in your code.

	
  5. Launch test, then repeat steps for next test.


Let’s pretend I want to test 2 things: The effect of changing my background color, and the effects of increasing my prices by 10%. I’ll show you how to set this up in VWO, using Apple’s online store as an example.

First, I visit a page that the test should apply on.  In this case, any page. I’ll just go to the home page. I highly recommend [jQuery injector for Chrome](https://chrome.google.com/webstore/detail/jquery-injector/indebdooekgjhkncmgbkeopjebofdoid). This will allow you to run jQuery from the console on any site.  Here’s the code I’ve come up with:

[cc lang="javascript" escaped="true"]$('body').css('background-color','gray');[/cc]

Here’s the before/after.

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/before.png)[/imageframe]



[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/after.png)[/imageframe]



Make sure you test the code on other pages to make sure it works. Now, I’ll go setup the A/B test. In VWO, you’ll create an A/B test, and just put any URL for now when it asks you for one. I’ll just put apple.com

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/next.png)[/imageframe]



Next, we are taken to the WYSIWYG editor. Click on the little gear next to “variation 1” and click “Insert Javascript/CSS”. Insert your code there, as shown below.

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/final.png)[/imageframe]



That’s it. Save it and move on. Set up your goals and hit next. On the last step where it says “Run test on URL(s):”, put in your test pattern. If you want it on all pages, put domain.com/*, if you want just a subdirectory, put domain.com/subdirectory/*. You can also exclude URLs. For this test, I’m excluding the checkout process as well as the help section. Below is what that might look like

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/last.png)[/imageframe]



What you see in the “Exclude URLs” section is a regular expression. They can be very complex, so you’ll either need to take time to learn it or find someone who knows it well.

Now we launch the test. That literally took me about 5 minutes. Compare _that_ to setting up a sub-domain and cloning the site just to test the background color! Once that's done we can layer our next test on top of it. We’re going to test the effects of raising the price of iPhone cases by 10%. I'll use [this page ](http://store.apple.com/us/product/HA755ZM/A/power-support-hd-anti-glare-film-set-for-iphone-5?fnode=47&fs=m.iphoneCompatibility%3Diphone_5)as the testing page.  Here’s the code I came up with:

[cc lang="javascript" escaped="true"]if (/cases/i.test($('.breadcrumb-nav ol.breadcrumbs li').last().text())) {

currentprice = parseFloat($('#price span.current_price span span').text().replace(/^ss*/, '').replace(/ss*$/, '').replace("$",""));

newprice = Math.round((currentprice + (currentprice * .1))*100)/100;

$('#price span.current_price span span').text("$"+newprice);

}[/cc]

For sake of time I didn’t test it on every page (and it’s not going to actually submit this price when you hit add to cart), but it’s a good example because it’s somewhat complex and it works on the [page I tested it on](http://store.apple.com/us/product/HA755ZM/A/power-support-hd-anti-glare-film-set-for-iphone-5?fnode=47&fs=m.iphoneCompatibility%3Diphone_5). This took about 15 minutes, and it will be the same for any decent developer.

Real quick, I’ll tell you how this code works:



	
  1. Look at the breadcrumbs and make sure the last word is “Cases”

	
  2. If so, save the price of the product into a variable.

	
  3. Add 10% to the price, and overwrite the old price.


Once we launch this test, we have layered 2 site-wide tests, and in less than an hour. _That’s efficient_**. **To make an _entire copy_ of the apple site just to add this test would have taken **tons** of time, money, and resources.

I hope this is getting you excited – I know I was when I first discovered this! But you probably noticed a small issue with this – when the test completes and you stop the test, you still have to implement this to your site. However, changing the price of something on a site is much easier than duplicating the entire site. Also, if you duplicate the entire site and the test fails, you've gone through all that work for nothing.

There’s almost nothing that you can’t manipulate with jQuery – it’s awesome. If you want to go even deeper, you can also read the cookie manually using a server-side language, and have even more options for testing. However, that’s another post in itself that I’ll cover another time.


## **Measuring Efficiently**


To iterate even faster, you can take advantage of techniques to lower the confidence level needed by your testing software. Here’s a few ways to analyze tests so you can finish a bit earlier, as well as get a better idea of how your tests are doing.


### **Goal Correlation**


You should always measure as many goals as possible. At minimum, always measure revenue-per-visitor, conversion rate, engagement, and visits to intermediate funnel steps. If you’re not too confident in the results of a test, look at the correlation between the metrics. If they are all green, you can give it a bit more confidence. The test below is only at 70% statistical significance in revenue, but I wouldn’t mind finishing this one at about 75% or so because of the correlation.

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/goal.png)[/imageframe]



Tracking multiple goals also gives you more insight as to how your variation is affecting visitors. For example, if you have a lead capture form and notice engagement is down but conversions are up, it usually means you’re doing a better job qualifying your visitors.


### **Chart Path**


If you look at the line graph for any split-test you’ll notice that it goes up-and-down a lot in the beginning and then starts traveling straighter. As more data is collected, our conversion rate range decreases, which is the basis of the calculation for statistical significance. If you notice the lines on your graph have been parallel for a while, you can have more confidence in the results.

[imageframe lightbox="no" style="bottomshadow" bordercolor="" bordersize="0px" stylecolor="#000000" align="center" animation_type="0" animation_direction="down" animation_speed="0.1"]![](http://convertify.io/wp-content/uploads/2013/02/chart.png)[/imageframe]




## **Conclusion**


Conversion optimization is simply a method for learning about your visitors. The quicker you learn about them, the quicker you’ll grow. Taking advantage of this methodology for testing will have significant effects on what you can accomplish with your own tests, or what your testing team can do for your business. If you have any technical questions or any feedback, please leave a comment. Now go run some tests!



[_Hire Us_](http://landersoptimized.com/contact/)
