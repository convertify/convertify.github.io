---
author: wpengine
date: '2012-03-08 10:27:18'
layout: post
slug: how-to-run-ab-split-tests-on-volusion-ecommerce-using-google-website-optimizer-2
status: publish
title: How to Run A/B Split Tests on Volusion eCommerce using Google Website Optimizer
featured_image: https://s3.amazonaws.com/convertify-s3/blog/images/2012/03/volusionshiny.jpg
wordpress_id: '1106'
categories:
- E-Commerce
- Scripts
---

I recently had a client who wanted me to optimize a few landing pages on their volusion eCommerce store. Unfortunately, Volusion doesn't allow you to just insert snippets of code into the header of a specific product page, and when searching through their support all I found was a page that asks for a ridiculous $200 to have them set up A/B split-tests for you. Anyways, this is how I approached it:  
  
**EDIT: **I figured out that you can in fact add to the head of the page by using the custom meta tags section, so I've removed the javascript code that I was using to get around it.  
  
[dropcap]1[/dropcap]Go to your product page in Volusion. Go down to the 'Advanced Settings' section and choose the 'Search Engine Optimization' tab on the left. Look for the section that says 'CUSTOM META TAGS OVERRIDE'. This is where you paste your tracking code from Google Website Optimizer.  
  
[dropcap]2[/dropcap]Do the same thing for your variation pages. The meta tags section is meant for inserting meta tags for your site. These meta tags go in the head section which is exactly where your script needs to go, so it works out.  
  
[dropcap]3[/dropcap] **If you want a conversion counted for ANY sale: **In Volusion, go to the 'Design' tab then hit the 'Site Content' link in the drop-down menu. Look for article 130 (or use cmd + f or ctrl + f on windows then type '130') and edit the article by hitting the article ID. paste your conversion code in the 'Article Body' section.  
  
**If you only want specific products to count as a conversion: **Go to the product editor, and click the 'Advanced Settings' drop-down. Find the 'Product Display' section, and find the box labeled 'Order Finished Note'. Put your conversion code here. Do the same for other products you want to count as a conversion. This basically just tells Volusion to run code only if that specific product is bought.  
  
[dropcap]4[/dropcap] It gets a little tricky next because GWO wants you to validate the pages. the product pages should validate fine now, but the conversion code wont. This is because there has to be an actual order that gets completed for the script to run. What you need to do is go to the Article 130 edit page again and look for 'View live article page' on the top-left of that page. It will show you that page, then save that page by hitting File>Save in your browser. Next, go back to GWO's validate pages section and upload that file manually. If anyone knows of some kind of variable you can pass in the URL through Volusion to get it to run the script, please let me know in the comments. That would be a better solution for this which I believe Volusion should have implemented.  
  
Once you've done these steps, you're all done! Please let me know how this works out for you guys and if you run into any issues.
