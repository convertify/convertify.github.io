---
author: wpengine
date: '2012-04-03 22:30:10'
layout: post
slug: track-clicks-as-conversions-in-google-website-optimizer
status: publish
title: Track Clicks as Conversions in Google Website Optimizer
wordpress_id: '182'
categories:
- Scripts
---

Sometimes, you may be interested in optimizing clicks-through-rates using Google Website Optimizer. Since GWO requires a thank-you page link with code in it in order to count as a conversion, we came up with a workaround to make a click count as a conversion. Not only will I be showing you how to track clicks as a conversion, but I'll also show how you can track **multiple** clicks as the **same **conversion. My recent client wanted me to improve his click-through-rates on his review site, which meant I needed to count specific outgoing clicks from his website as a conversion. The way the solution works is that you make all the buttons link to the same page, which contains the conversion code in it. The page then redirects them to the proper page based on which button/link they clicked. It's unnoticeable, and easy to do:  
  
[dropcap]1[/dropcap] First we need to create an HTML page with the conversion code in it. Open up any text-editor, and copy/paste your conversion code from GWO into the file. save it anywhere on your web server. We'll call it conversion.html for this example. M**ake sure the filename ends in .html before saving!**  
  
[dropcap]2[/dropcap]Open up the text-editor again and create another file. We'll call it gwo.php for this example. Copy the following code into it then save it on your web server in the same folder as conversion.html! If you just want to track 1 destination, look at the first block of code. If you want to track multiple links going to multiple destinations and want to count them all as the same conversion, see the second section of code.  
  
**Single destination: **_(Replace 'http://www.domain.com/page.html' with the link it should redirect to.)_  
  
[cc lang="html" escaped="true"]  
  
<?php include('conversion.html'); echo "<script>location.href='http://www.domain.com/page.html'</script>";  
  
?>  
  
[/cc]  
  
**Multiple Destinations: **_Two outgoing links are used in this example. If you have 4 links, there would be 4 "case" statements. You can copy/paste extra ones as needed. Replace the links which follow "href=" with your links. _  
  
[cc lang="html" escaped="true"]  
  
<?php include('conversion.html'); switch ($_GET['id']) {  
  
case 1: echo "<script>location.href='http://www.domain.com/page.html'</script>"; break;  
  
case 2: echo "<script>location.href='http://www.domain.com/page.html'</script>"; break;  
  
}  
  
?>  
  
[/cc]  
  
Once finished, save the file and move to the next step.  
  
[dropcap]3[/dropcap] Now, we have to change the link of your buttons to link to this new page. But first, we need to figure out what link to use. Let's pretend that our gwo.php file is saved at http://website.com/gwo.php. If we wanted to link to the site in 'case 1', we would visit http://website.com/gwo.php?id=1 . If we wanted the button to link to 'case 2', we simply change id=1 in the link to id=2. So http://website.com/gwo.php?id=2 would take us to a different site than if we put id=1. In the process, it will also spit out the conversion code so that GWO can track it.  
  
[dropcap]4[/dropcap] Last, we need to validate the page. When setting up the experiment in the GWO setup wizard, in this example, we put http://website.com/conversion.html in the thank-you page field. Google Website Optimizer should validate the page successfully if your page is uploaded correctly.  
  
That's it, You're Done! If you want to add more links to be counted as conversions, all you need to do is add another 'case' to the php page we made. Hope this helps!
