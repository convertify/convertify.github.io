---
author: convertify
comments: true
date: 2014-02-21 15:39:03+00:00
excerpt: 'Tracking Infusionsoft sales in Google Analytics is a bit trickier than it
  needs to be. Because of the fact that the Infusionsoft cart is hosted on a different
  domain, cookie values are not persisted through the checkout process. Also, they
  do not provide variables that provide order details on the thank you page. Therefore,
  there are really 2 things that need to be accomplished to solve this problem:'
layout: post
slug: how-to-track-infusionsoft-sales-with-google-analytics-e-commerce-tracking
title: How to Track Infusionsoft Sales With Google Analytics E-Commerce Tracking
wordpress_id: 1084
categories:
- Analytics
- E-Commerce
- Guides
- Scripts
---

_Note: If you'd like us to perform this integration for you, we offer a flat rate to do this for you. Please email [info@convertify.io](mailto:info@convertify.io) to hire us._

Tracking Infusionsoft sales in Google Analytics is a bit trickier than it needs to be. Because of the fact that the Infusionsoft cart is hosted on a different domain, cookie values are not persisted through the checkout process. Also, they do not provide variables that provide order details on the thank you page. Therefore, there are really 2 things that need to be accomplished to solve this problem:



	
  1. Setup cross-domain tracking to pass GA data from your domain to Infusionsoft's domain.

	
  2. Use the order ID on the thank you page as well as the Infusionsoft API to fetch the necessary order information.


Overall it's a technical process that requires some code, but we've done all the work for you. The following instructions will walk you through step-by-step to get this precious data tracked in Google Analytics!

**Note: This post assumes you have Wordpress. We will edit it soon so that it can be added to any PHP site**

If you have any trouble or have any questions, _please _let us know in the comments below!


## Setting Up Cross-Domain Tracking


Just in case, I'm going to assume that you don't have Google Analytics installed on your Infusionsoft order forms.

The first thing we need to do is get our website to pass Google Analytics information to our order forms and our checkout pages. Follow the steps below:


### If you have the traditional Google Analytics:


You'll need to edit your current tracking code. Assuming your code looks like this:

[cc lang="js"]



[/cc]

You'll need to make it look like this:

[cc lang="js"]




[/cc]

Make sure not to overwrite your original Account ID ([cci]UA-XXXXX-X[/cci]) or your domain name (The part after [cci]_setDomainName'.[/cci]) with the information from the example code. Also, replace the "m48" part in  [cci]var infusionsoft_app_id = "m48";[/cci] with your actual Infusionsoft App ID.


### If you have Universal Analytics


You'll need to append some code to your current tracking code. Assuming your code looks like this:

[cc lang="js"]




[/cc]

You'll want to make it look like this:

[cc lang="js"]



[/cc]


### Test If it's working


Let's see if it works! Once this change has been made, go to a page on your website that contains an "Add to Cart" button for infusionsoft. Once you click it, look at the URL on the next page. If you have traditional analytics, your URL should look like this now:

https://m179.infusionsoft.com/app/orderForms/Product?**__utma=145477216.1430762516.1392159380.1392937143.1392989453.7&__utmb=145477216.4.10.1392989453&__utmc=145477216&__utmx=-&__utmz=145477216.1392159380.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none)&__utmv=-&__utmk=244849413**

If you have universal analytics, your URL should look like this: https://m179.infusionsoft.com/app/manageCart/showManageOrder?**_ga=1.38339491.1087305745.1390089092**&clearCart=true&subscriptionPlanQuantity=1&subscriptionPlanId=9&cartSkinId=8632&productId=692&productQuantity=1
I've bolded the information that should be appended assuming it's working. Once this is done, you're ready for the next step! If you're having trouble, please let us know in the comments below!


### Adding Tracking to Infusionsoft


Now we need to get Infusionsoft to use this information in the URL. You'll need to add the tracking code to the following 2 areas in Infusionsoft:



	
  1. **Shopping cart footer: **Located at** **Ecommerce >> Ecommerce Setup >> Shopping Cart Themes >> Edit Theme >> HTML Areas >> Custom Footer

	
  2. **Order Form Footer: **Located at Ecommerce >> Ecommerce Setup >> Order Form Themes >> Edit Theme >> HTML Areas >> Custom Footer


Copy the following code into each area, making sure to replace the account ID and domains below with your appropriate information:


#### Traditional Analytics Code:


[cc lang="js"]



[/cc]


#### Universal Analytics Code:


[cc lang="js"]



[/cc]

Once that's done, cross-domain tracking is set up! Now it's time to get your site hooked up to the Infusionsoft API.


## Pulling E-Commerce Data From Infusionsoft


Now we need to get Infusionsoft to pass data back to our site, and into google analytics. Before we start, we'll need to grab our API key from Infusionsoft. Here's a quick GIF showing how to generate one if you haven't already:

[![Get Api Key from Infusionsoft](http://convertify.wpengine.com/wp-content/uploads/2014/02/Untitled.gif)](http://convertify.wpengine.com/wp-content/uploads/2014/02/Untitled.gif)


### Wordpress Instructions


We've provided here a plugin that will make the rest of the process a piece of cake. Start by downloading the appropriate plugin:

_Note: credit for the  files used goes to [Mindshare Studios](https://github.com/mindsharestudios/infusionsoft-google-analytics) as these are just slightly modified versions of their code._
  
  

**If you have traditional analytics: [Download](http://landersoptimized.com/static/infusionsoft-google-analytics/wp-traditional.zip)**
  

**If you have universal analytics: [Download](http://landersoptimized.com/static/infusionsoft-google-analytics/wp-universal.zip)**
  
  

Once downloaded, login to wordpress, go to Plugins > Add Plugins, and upload the ZIP as a new plugin.

Once the plugin is installed, go to Settings -> Infusionsoft Google Analytics and enter your Infusionsoft App ID as well as your API Key there and save.

We're almost there!

Next, in Wordpress, go to Appearance >> Editor. On the right menu, click for the "Footer" link. Now scroll to the very bottom of the editor, and right before the closing [cci][/cci] tag, paste the following code:

[cc lang="php"]



[/cc]

If you haven't done so already, set up a thank you page on your Wordpress site. Then, use this page as the thank you page for ALL your order forms as well as your shopping cart, and make sure to check the "Pass contact's information to Thank You page" setting (see below).

[![Screenshot 2014-02-24 12.45.10](http://convertify.wpengine.com/wp-content/uploads/2014/02/Screenshot-2014-02-24-12.45.10.png)](http://convertify.wpengine.com/wp-content/uploads/2014/02/Screenshot-2014-02-24-12.45.10.png)



The code we put in the footer of your Wordpress runs globally, so you can set up multiple thank you pages and if you want, and it will still work as long as the page is on Wordpress.

That's it - you're done!

Hope that wasn't too hard! Now, just wait and watch the data roll into google analytics! If all goes well, you will start seeing data in google analytics under Conversions >> Ecommerce >> Overview, and it should look something like this:

[![Screenshot 2014-02-21 07.26.18](http://convertify.wpengine.com/wp-content/uploads/2014/02/Screenshot-2014-02-21-07.26.181.png)](http://convertify.wpengine.com/wp-content/uploads/2014/02/Screenshot-2014-02-21-07.26.181.png)



If you have any trouble, please comment below and we'll try to help. Enjoy!


