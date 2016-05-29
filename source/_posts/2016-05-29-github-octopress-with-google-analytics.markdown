---
layout: post
title: "Github Octopress with Google Analytics"
date: 2016-05-29 20:58:23 +0800
comments: true
categories: 
---
Register Google Analytics
-
Follow this guide [Octopress_3_0_guide][], 
register [Google Analytics Account](https://www.google.com/intl/zh-TW/analytics/) and get the tracking ID.
<!--More-->

Add Trace code into Source
-
Edit the file `source/_includes/google_analytics.html` and add the code 
```html
{% if site.google_analytics_tracking_id %}
  <script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
	    (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
    m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
	      })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', '<YOUR TRACKING ID>', 'auto');
  ga('send', 'pageview');

  </script>
{% endif %}

```
Add option in `_config.yml`
```
google_universal_analytics: YOUR TRACKING ID
google_universal_analytics_cookiedomain: auto
```
Note that `YOUR TRACKING ID` is yor actual tracking ID 

Re-rendor and deploy the pages
-
```bash
$ rake preview
$ rake deploy
```

[Octopress_3_0_guide]: https://www.chrisanthropic.com/blog/2014/adding-google-analytics-to-octopress-3-0/
