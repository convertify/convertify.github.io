---
author: wpengine
date: '2012-04-27 01:13:24'
layout: post
slug: tracking-optimizing-review-sites-with-google-website-optimizer-or-any-page-with-multiple-outoing-links
status: publish
title: Tracking & Optimizing Review Sites with Google Website Optimizer (or Any Page
  with Multiple Outoing Links)
featured_image: http://convertify.staging.wpengine.com/wp-content/uploads/2012/04/star-rating.jpeg
wordpress_id: '233'
tags: ['scripts']
categories:
- Scripts
---

Google Website Optimizer is a great tool for split-testing in order to increase conversions, but it requires a single thank you page. What if you are just trying to improve the outgoing CTR's going from your review site (or any page with multiple links for the matter) to outgoing links, such as affiliate links? In this case, a "conversion" would be an outgoing click. Since GWO doesn't have a way to track this, here's a workaround I've been using for clients that should allow you to achieve this for your own sites.  
  
The way this works is that we set up a single PHP page where ALL your links will direct visitors to. This page will include some (simple) PHP code that will redirect users to the correct place according to which link they clicked on the previous page. Also, this page will include your GWO thank you page code, so that a conversion is tracked if any of the links are clicked!  
  
Now.. let's get down to business...  
  
In this guide, we will assume we have a page with 3 links as so:  
  
**Link 1: **http://site1.com/somepage.html  
  
**Link 2: **http://site2.com/somepage.html  
  
**Link 3: **http://site3.com/somepage.html  
  
We will need to create a php file on the server. Let's call this redirect.php.  
  
We will assume the page you are trying to optimize is at http://yoursite.com/page-to-be-optimized.html.  
  
[dropcap]1[/dropcap] First, we start by changing all the links to link to this redirect page. So on the link that links to Link 1, we will change the link to be " http://yoursite.com/redirect.php?link=1". Notice how we added the '?link=1' at the end? Thanks to php, the redirect page will be able to use this information and send the visitor to the correct place. Do this for the other links as well.  
  
[dropcap]2[/dropcap] Now, we create the redirect page. Create a file called redirect.php using any text or HTML editor and copy in the following code:  
  
[cc lang="html" escaped="true"]  
  
<?php include('conversion.html'); switch ($_GET['link']) {  
  
case 1: echo "<script>location.href='http://site1.com/somepage.html'</script>"; break;  
  
case 2: echo "<script>location.href='http://site2.com/somepage.html'</script>"; break;  
  
case 3: echo "<script>location.href='http://site3.com/somepage.html'</script>"; break;  
  
}  
  
?>  
  
[/cc]  
  
[dropcap]3[/dropcap] Create a page named conversion.html and copy your tracking code in there. This is the page you will use as the 'thank you' page in GWO.  
  
   
  
All Done! All you have to do to add more links is add a new case statement. Even without any coding knowledge it should be pretty obvious how to do this by looking at the code.
