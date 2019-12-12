---
title: How to Bypass Sites With Invalid Certificate in Google Chrome
layout: post
categories: ['howto']
---
When I was setting up a brand new server on AWS, sometimes a valid certificate with Apache is not required because the instance is sitting behind a load balancer and inside a private network. 

I used to able to by pass the error message in Google Chrome by clicking on `Advance` and `proceed`. 

Ever since I upgraded to **Catalina**, the option to `proceed` is gone. 

![]({{ 'assets/img/chrome-bypass-insecure-site.png' | absolute_url }})

**Warning: Not for everyday users**

Much to my surprise, the way to `proceed` is by typing `thisisunsafe` anywhere on the page. Well, what I mean is, when you visited the site, just type the phase `thisisunsafe`. It will let you bypass it. 
