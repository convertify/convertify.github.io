---
author: convertify
date: '2013-02-13 08:46:38'
layout: post
slug: tracking-multiple-cnames-masked-domains-in-google-analytics
status: publish
title: Tracking Multiple CNAMEs & Masked Domains in Google Analytics
wordpress_id: '998'
featured_image: http://convertify.staging.wpengine.com/wp-content/uploads/2013/02/Untitled-2.jpg
categories:
- Scripts
---

Here's a neat trick.

Let's say you have www.domainA.com and www.domainB.com - whereas www.domainB.com uses a CNAME or an alias pointing to www.domainA.com. Using this trick you can track both domains in a single google analytics account (or profile) using the same code on both sites. There is no limit as to how many domains  you can do this for, as long as they share the same files.

Change your GA code to look like this:

[cc lang="javascript" escaped="true"]

var _gaq = _gaq || []; _gaq.push(['_setAccount', 'UA-12345-1']); _gaq.push(['_setDomainName', window.location.hostname]); _gaq.push(['_setAllowLinker', true]); _gaq.push(['_trackPageview']);

(function() { var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true; ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js'; var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s); })();

[/cc]

And then set up your standard cross-domain profile filter:

![](/media/images/{{ page.date | date: "%F" }}-{{ page.slug }}/Screen-Shot-2013-02-13-at-8.36.04-AM-300x2611.png)

Enjoy!
