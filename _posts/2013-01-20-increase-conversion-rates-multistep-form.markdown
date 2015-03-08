---
author: wpengine
date: '2013-01-20 04:18:21'
layout: post
slug: increase-conversion-rates-multistep-form
status: publish
title: Increase Conversion Rates With Our Multistep Form [Free Plugin]
wordpress_id: '814'
featured_image: http://convertify.staging.wpengine.com/wp-content/uploads/2013/01/framework_seo.gif
categories:
- Conversion Rate Optimization
- Guides
- Scripts
---

We've developed a simple plugin that transforms your form into a sliding multi-step form. It's extremely easy to implement and has had significant effect on conversion rates of experiments we've used it on.  Here's a demo of a form with a plugin installed: 

## Demo

   
  
Today, I'd like to take some time to walk you through how to use our plugin and how to convert your existing forms into multi-step forms Make sure to A/B test before implementing it permanently, as we have seen tests where a multi-step form actually decreased the conversion rate.  
  
**1. Download the plugin here: [http://landersoptimized.com/i/multistep.zip](http://landersoptimized.com/i/multistep.zip)**[ ](http://landersoptimized.com/i/multistep.zip)  
  
**2. Unzip, then upload the folder to your server.  **For simplicity's sake I'll assume you uploaded the folder to the root of your domain  for the rest of the tutorial.  
  
**3. Make sure you have jQuery. **If you already have jQuery, skip this step. If you aren't sure, there's a simple way to find out. just check the source of your page and do a find (ctrl+f or cmd+f) and type 'jquery'. You should find a match in a line that looks like the following code. If you find it, move to the next step. If you dont have it, put the following code in-between the <head> tags of your page:  
  
{% highlight html %}  
  
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7/jquery.min.js"></script>  
  
{% endhighlight %}  
  
**4. Add the following tags to the <head> section of your page, AFTER the jQuery code:**  
  
{% highlight html %}  
  
<link rel="stylesheet" href="/multistep/multistep.css"> <script type="text/javascript" src="/multistep/multistep.js"></script>  
  
<script type="text/javascript"> $(function() { $('#multistep-form').multistep();  
  
});  
  
</script>  
  
{% endhighlight %}  
  
_note: use "multistep/multistep.css" and "multistep/multistep.js" if you didn't place files in the root of the domain._  
  
**5. Give your form a ID tag of 'multistep-form' like so:**  
  
{% highlight html %}  
  
<form id="multistep=form">  
  
</form>  
  
{% endhighlight %}  
  
**6. Separate your steps by wrapping them as follows. Also, give the last step an ID of 'last-step':**  
  
{% highlight html %}  
  
<form id="multistep-form">  
  
<div class="step">  
  
<!-- Stuff for step 1 here... -->  
  
</div>  
  
<div class="step">  
  
<~-- Stuff for step 2 -- >  
  
</div>  
  
<div class="step" id="last-step">  
  
<~-- Stuff for step 3 (last step) -- >  
  
</div>  
  
</form>  
  
{% endhighlight %}  
  
   
  
**7. Give each step a button**  
  
{% highlight html %}  
  
<form id="multistep-form">  
  
<div>  
  
<!-- Stuff for step 1 here... --> <button type="submit" class="submit">Continue</button> </div>  
  
..............  
  
{% endhighlight %}  
  
   
  
**8. You're finished! **If you are having trouble or want more info, visit the [project page](https://github.com/coopermaruyama/multistep.js) or leave a comment below and I'll help out.
