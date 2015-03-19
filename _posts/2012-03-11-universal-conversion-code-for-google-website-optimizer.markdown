---
author: wpengine
date: '2012-03-11 17:26:56'
layout: post
slug: universal-conversion-code-for-google-website-optimizer
status: publish
title: Universal Conversion Code for Google Website Optimizer
featured_image: https://s3.amazonaws.com/convertify-s3/blog/images/2012/03/353373_ZMnl3spGy4fpK_v0LDnCTILKw-3.jpg
wordpress_id: '171'
categories:
- Conversion Rate Optimization
- Scripts
---

I was reading a post over at [ROIRevolution](http://roirevolution.com) and found an awesome code that allows you to use one snippet of code to track all of your experiments, so I thought I'd share it here. This basically looks at your cookie and pulls out the proper conversion ID then inserts it into the code dynamically using javascript. Here's the code:  
  
{% highlight js %}
  
<script type="text/javascript"> function readCookie(name) { // function to read cookie var nameRegex = RegExp("(?:; |^)" + name + "=([^;]+)"); nameValue = nameRegex.exec(document.cookie); if(nameValue) { return nameValue[1]; } else { return null; } } </script>  
  
<script type="text/javascript"> (function () { try { _gaq.push(['gwo._setAccount', 'UA-XXXXXXX-Y']); var utmx = readCookie("__utmx"); var pieces = utmx.split(/(?:^|:)[^.]*(?:.|$)/); for (i = 0; i < pieces.length; i += 1) { if (pieces[i]) { _gaq.push(['gwo._trackPageview', '/' + pieces[i].substring(10) + '/goal']); } } } catch (err) { } })();  
  
(function() { var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true; ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js'; var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s); })(); </script>  
  
{% endhighlight %}
  
This code should replace all your current GWO-related code on your conversion page.
