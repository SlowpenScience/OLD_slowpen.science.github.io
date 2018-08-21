---
title: "How to embed http websites in your R presentation ?"
description: "March 18, 2018"
slug: "httpres"
image:
keywords: ""
categories: 
    - ""
    - ""
date: 2018-03-18T22:26:13-05:00
draft: false
---

<!-- AddToAny BEGIN -->
<div class="a2a_kit a2a_kit_size_16 a2a_default_style">
Brice Beffara - March 18, 2018 
<a class="a2a_button_twitter"></a>
<a class="a2a_button_facebook"></a>
<a class="a2a_button_email"></a>
<a class="a2a_button_linkedin"></a>
</div>
<script async src="https://static.addtoany.com/menu/page.js"></script>
<!-- AddToAny END -->


Sometimes it can be usefull to incorporate web content in a presentation. I needed it in one of my <a href = "https://support.rstudio.com/hc/en-us/sections/200130218-R-Presentations" target = "_blank">R presentations</a> few months ago and did not know about any straightfoward solution to do so. 

Aggregating - fragmented but usefull - discussions found on forums, I came to a kind of solution using <a href = "https://www.w3schools.com/tags/tag_iframe.asp" target = "_blank">\<iframe></a>. Usually

> "The HTML \<iframe> element represents a nested browsing context, effectively embedding another HTML page into the current page" - <a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" target = "_blank">developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe</a>

It took me time to get a satisfying result because of my lack of knowledge about <a href = "https://en.wikipedia.org/wiki/HTML" target = "_blank">HTML</a> and <a href = "https://en.wikipedia.org/wiki/Cascading_Style_Sheets" target = "_blank">CSS</a>. The HTML part is not very complicated to use and understand. For instance, the following \<iframe> will embed this <a href = "http://rpsychologist.com/d3/NHST/" target = "_blank">rpsychologist.com/d3/NHST/</a> webpage with an option allowing to scroll on the page.

```{r eval=FALSE}
<iframe src="http://rpsychologist.com/d3/NHST/" scrolling= "yes"></iframe>
```


However, if you want to display it properly, you will need some CSS at the beginning of your .rpres file. For instance, this will allow to center the content and display it with a correct size. You will not be able to preview the result directly in RStudio. You will have to choose "View in Browser" in the "Presentation" tab. For more information on CSS style for \<iframe>, you can have a look at <a href = "https://www.thoughtco.com/iframes-and-css-3468669" target = "_blank">www.thoughtco.com/iframes-and-css-3468669/</a>. You can copy-paste the example bellow in your .rpres file to visualise the result.


```{r eval=FALSE}
<style>
  
iframe {
  position: absolute;
  top: 50%; 
  left: 50%;
  -webkit-transform: translateX(-50%) translateY(-50%);
  transform: translateX(-50%) translateY(-50%);
  min-width: 100vw; 
  min-height: 100vh; 
  z-index: -1000; 
  overflow: hidden;
}

</style>

http in R presentation
========================================================
author: An animal
date: A day
autosize: true

========================================================

<iframe src="http://rpsychologist.com/d3/NHST/" scrolling= "yes"></iframe>
```

Better solutions surely exist. For instance, the proposition described here does not work on all browsers. Besides, it only works for http but not https pages. If you konw about a better way to do it, let me know !

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = http://slowpen.science/blog/httpres/;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = httpres; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://slowpen-science.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            